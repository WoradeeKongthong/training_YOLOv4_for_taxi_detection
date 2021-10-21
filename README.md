# train_YOLOv4_for_taxi_detection

## How I created the dataset
**Taxi dataset**  
Where to get the dataset : https://storage.googleapis.com/openimages/web/index.html  

Tools to get the dataset : follow the README.md in https://github.com/theAIGuysCode/OIDv4_ToolKit.git  
Or you can follow my steps in your terminal:

(option 1 : you have never used OIDv4 toolkit before)
- create virtual environment `$python -m venv oid_download`
- activate the virtual environment `$source venv oid_download/bin/activate`
- clone or download the repository `$git clone https://github.com/theAIGuysCode/OIDv4_ToolKit.git`
- cd into the repository folder `$cd OIDv4_ToolKit`  
- install required packages `$pip install -r requirements.txt`  
- download train set `$python main.py downloader --classes Taxi --type_csv train`  
- download validation set `$python main.py downloader --classes Taxi --type_csv validation`
- download test set `$python main.py downloader --classes Taxi --type_csv test`
- put the class name(s) of dataset you are going to train into classes.txt (notes : the class name(s) must be the same as the one shown in downloaded label file), in out case, we just put `Taxi` in the first and only line.
- convert the label files of OID dataset to YOLO dataset `$python convert_annotations.py`
- check the correctness in converted txt file, if the class name(s) is changed to integer number.
- (optional) remove the Label folders in train,validation and test folders
- now, your `OIDv4_ToolKit/OID/Dataset/` folder is ready to use

(option 2 : you have used OIDv4 toolkit before)
- clone or load the repository from https://github.com/theAIGuysCode/OIDv4_ToolKit.git
- copy `convert_annotations.py` file and paste it into your `ODIDv4_ToolKit` folder
- activate your virtual environment
- download your dataset (if you haven't downloaded it yet)
- put the class name(s) of dataset you are going to train into classes.txt (notes : the class name(s) must be the same as the one shown in downloaded label file), in out case, we just put `Taxi` in the first and only line.
- convert the label files of OID dataset to YOLO dataset `$python convert_annotations.py`
- check the correctness in converted txt file, if the class name(s) is changed to integer number.
- (optional) remove the Label folders in train,validation and test folders
- now, your `OIDv4_ToolKit/OID/Dataset/` folder is ready to use

## How to train the YOLOv4
**training_YOLOv4_for_taxi_detection.ipynb**  
In this notebook, I train the YOLOv4 model on one class dataset which is Taxi datset.  

- Create a model and load pre-trained weights.  
- Prepare dataset and other related files (config file, obj.data, obj.names, train.txt and test.txt) for training YOLOv4 model.   
- Download the pre-trained weights for the convolution layers, mount drive for backup training weights and train the model.
- Evaluate the model (mAP).
- Test that my model is functional by testing it on a random image in test dataset.  
