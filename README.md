# Grab AI For SEA Computer-Vision
This is a challenge from Grab to identify the make / model and color of vehicles.

# Libraries
_Required_

- pip install mat4py
- pip install opencv-python
- pip install tensorflow
- pip install keras==2.2.2
- pip install webcolors

_May Require_
- pip install numpy

# Prerequisite
- Download the model file ("model_frcnn.hdf5") from https://drive.google.com/open?id=1sODlnbkThlpQa-msGefKljOW97OK7CcT and copy to "4-Making_Predictions" folder.
- Download training data from imagenet.stanford.edu/internal/car196/cars_train.tgz. Extract and copy to "2-Read_ImgLabels_Resizer_From_CSV" > "cars_train" folder.

# Data Preprocessing
- "1A-cars_train_annos.mat.ipynb" reads all the bounding boxes and classes of the vechicles and export it to CSV format
- "1B-cars_meta.mat" maps the car_classes (in integer format) to the name of the the vechicle (in string format).

# Data Cleaning
- "2A-Data-Cleaning-Image_Labels-Resizer" reads all the bounding boxes and classes of the vehicles. The image is then standardised to the same resolution and the bounding boxes are resized and recalculated. The new images are saved in "cars_train_new" folder and the calculated bounding boxes (x1, y1, x2, y2), image name and image class are saved inside the "cars_train_new_labels-512.csv" folder.

# Data Preview
- "2B-Data_Preview" shows you the class / type of image and the respective image. A sample of the output is inside the Jupyter notebook.
![Image of Preview](https://github.com/jeromechua/Grab-AI-For-SEA---Computer-Vision/blob/master/2-Read_ImgLabels_Resizer_From_CSV/data_preview.png)

# Data Modelling.
- The code is adapted from https://github.com/kbardool/keras-frcnn.
- Copy the "cars_train_new_labels-512.csv" from "2-Read_ImgLabels_Resizer_From_CSV" folder and rename it as "annotate.txt". Also, copy the newly resized images ("cars_train_new") as "train_images".
- Use the command line to go into this directory. 
- Run "python train_frcnn.py -o simple -p annotate.txt" to begin the training process. If you have a GPU, ensure thay you installed the TensorFlow with GPU support as this will significantly speedup the training process.

# Data Prediction
- The colour code is adapted from https://stackoverflow.com/questions/9694165/convert-rgb-color-to-english-color-name-like-green-with-python.
- Change directory of the image by changing the "00019.jpg" part in "img_location = os.path.join(current_working_directory, "00019.jpg")".
- The predicted data will have a bounding box over the vehicle and the colour will be calculated by finding 100 random regions over the part that has the bounding box. The colour that has the highest count, will be estimated the color of the car.
- The output looks something like that:
![Image of Output](https://github.com/jeromechua/Grab-AI-For-SEA---Computer-Vision/blob/master/Expected%20Output.PNG)

The make / model of the vehicle is shown and the colour (sienna) is also calculated.

The rationale for using this alogirthm is that it is able to detect cars preciesely and the make / model of each car, hence it is useful for real-life deployment.
