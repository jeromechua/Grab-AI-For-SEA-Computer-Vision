# Grab-AI-For-SEA---Computer-Vision
This is a challenge from Grab to identify the make / model and color of vehicles.

# Libraries
- Required 
pip install mat4py
pip install opencv-python
pip install tensorflow
pip install keras==2.2.2

- May Require
pip install numpy

# Prerequisite
- Download the model file ("model_frcnn.hdf5") from https://drive.google.com/open?id=1sODlnbkThlpQa-msGefKljOW97OK7CcT and copy to "4-Making_Predictions" folder.
- Download training data from 

# Data Cleaning
- "1A-cars_train_annos.mat.ipynb" reads all the bounding boxes and classes of the vechicles and export it to CSV format
- "1B-cars_meta.mat" maps the car_classes (in integer format) to the name of the the vechicle (in string format).

# Data Preprocessing
- "2A-Data-Cleaning-Image_Labels-Resizer" reads all the bounding boxes and classes of the vehicles. The image is then standardised to the same resolution and the bounding boxes are resized and recalculated.
