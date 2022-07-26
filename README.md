# Object-Detection-using-Yolov5

Yolov5 Custom Dataset Training


A. Dataset Creation

- collect images for custom dataset training.(size and resolution of the image dosent matter)
- install python using https://www.python.org/downloads/
- open command prompt and install lxml by typing "pip install lxml"
- open command prompt and install PyQt5 by typing "pip install PyQt5" or "pip3 install PyQt5"
- open labelImg folder in command prompt and type "python labelImg.py" for open labelImg.(labelImg is used for annotating the images)
- in labelImg open collected image directory and start annotating the images using create rectbox tool and mention class name after that save all annotation in pascalvoc format.
- after completing annotation copy all xml file to convert folder in \xml_to_yolo_convert\convert location.
- then edit convert.py file.edit the class name in these lines with our class names(like "accessory,"top","rubber" etc the class name given in the time of annotation) and remove unwanted classes
- save convert.py file
- then open command prompt in that convert folder and type "python convert.py" this will create yolo text file(.txt) for the xml file

B. Seperating Dataset for train and validation

- for training we need 80% of images we collected and for validation the remaining 20% image needed ( train=80% and validation=20% ).
- copy 80% of images from dataset to train folder in location dataset\images\train
- copy corresponding yolo file of the image used for train to location dataset\labels\train
- copy remaining images from dataset to validation folder in location dataset\images\val
- copy corresponding yolo file of the image used for validation to location dataset\labels\val

C. Yaml file editing

- open the folder data in yolov5\data and open custom_dataset.yaml in notpad.
- change the value of nc to the no of classes present in our dataset
- replace the classnames with our class names
- save the file

D. Yolov5 training and detecting

- open command prompt in folder yolov5 then type "pip install -r requirements.txt" for installing requirement for yolov5
- for training open command prompt in folder yolov5 then type "python train.py --img 640 --batch 16 --epochs 100 --data custom_dataset.yaml --weights yolov5s.pt --cache"
- after training it will create weight in folder yolov5/runs/train/exp/weights/best.pt
- for detecting images copy some images for testing in folder yolov5\data\images
- open command prompt in folder yolov5 then type "python detect.py --source data/images/ --weights runs/train/exp/weights/best.pt"
- after completing detection it gives results in folder yolov5/runs/detect

E. Keywords used in Yolov5

- batch — batch size (-1 for auto batch size). Use the largest batch size that your hardware allows for.
- epochs — number of epochs.
- data — path to the data-configurations file.
- cfg — path to the model-configurations file.
- weights — path to initial weights.
- cache — cache images for faster training.
- img — image size in pixels (default — 640).
- source — input path (0 for webcam)
- conf — confidence threshold
- iou — IoU threshold for NMS (Non Max Supression)
- augment — augmented inference (TTA)

F. Create Virtual Environment for python ( optional )

- download and install python
- create a folder in our local disk
- open newely created folder in command prompt
- type "python -m venv virtual_environment_name" in the place of virtual_environment_name we can give our own virtual environment name by replacing it
- type "virtual_environment_name\Scripts\activate" for activating the virtual environment
- type "deactivate" for deactivating virtual environment
- if pip not showing in virtual folder type "python -m ensurepip" then upgrade pip

G. Yolo Commands

- python train.py --img 415 --batch 16 --epochs 30 --data dataset.yaml --weights yolov5s.pt --cache
- python train.py --img 640 --batch 8 --epochs 100 --data mat.yaml --weights yolov5s.pt --cache
- python detect.py --source data/images/ --weights runs/train/exp/weights/best.pt
- python detect.py --source data/images/ --weights runs/train/exp/weights/best.pt --conf 0.50
- python export.py --data mat.yaml --weights runs/train/exp/weights/best.pt --include tflite --img 640
- python detect.py --weights runs/train/exp/weights/best-fp16.tflite --img 640 --source data/images/

H. References
- python : https://www.python.org/downloads/
- labelImg : https://github.com/tzutalin/labelImg
- xml to yolo converter : https://github.com/bjornstenger/xml2yolo
- yolov5 : https://github.com/ultralytics/yolov5
- labelimg annotation tutorial : https://youtu.be/Tlvy-eM8YO4
- yolov5 training tutorial : https://youtu.be/80Q3HIBy7Qg
