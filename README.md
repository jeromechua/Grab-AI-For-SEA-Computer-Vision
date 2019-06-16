# Grab-AI-For-SEA---Computer-Vision
This is a challenge from Grab to identify the make / model and color of vehicles.

# Libraries
_Required_

- pip install mat4py
- pip install opencv-python
- pip install tensorflow
- pip install keras==2.2.2

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

# Data Modelling.
- The code is adapted from https://github.com/kbardool/keras-frcnn.
- Copy the "cars_train_new_labels-512.csv" from "2-Read_ImgLabels_Resizer_From_CSV" folder and rename it as "annotate.txt". Also, copy the newly resized images ("cars_train_new") as "train_images".
- Use the command line to go into this directory. 
- Run "python train_frcnn.py -o simple -p annotate.txt" to begin the training process. If you have a GPU, ensure thay you installed the TensorFlow with GPU support as this will significantly speedup the training process.

