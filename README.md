# Automatic Number Plate Recognition :india:

## Table of Content
  * [Demo](#demo)
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Technical Aspect](#technical-aspect)
  * [Installation](#installation)
  * [Run](#run)
  * [Directory Tree](#directory-tree)
  * [To Do](#to-do)
  * [Bug / Feature Request](#bug---feature-request)
  * [Technologies Used](#technologies-used)
  * [Team](#team)
  * [License](#license)
  * [Resources](#resources)
  
 


## Overview
This is a four phased Object Detection project mainly focussing on detecting Vehicle's license plates and thereby reading the license number and saving them in a text file for use by the concerned authority.This Deep Learning Project uses YOLOv4(You Only Look Once) as its Neural Network Architecture which is made above a framework called Darknet.It is then made deployment ready with Tensorflow Lite making it compatible for using it in various edge devices such as android, iOS, raspberry Pi etc. 


## Motivation

- Automatic License Plate Recognition (ALPR) has been a frequent topic of research due to many practical applications, such as automatic toll collection, traffic law
enforcement, private spaces access control and road traffic monitoring.

- ALPR systems typically have three stages: License Plate (LP) detection, character segmentation and character recognition. The earlier stages require higher accuracy or almost
perfection, since failing to detect the LP would probably lead to a failure in the next stages either. Many approaches search first for the vehicle and then its LP in order to reduce processing time and eliminate false positives.

- Although ALPR has been frequently addressed in the literature, many studies and solutions are still not robust enough on real-world scenarios. These solutions commonly depend on certain constraints, such as specific cameras or viewing angles, simple backgrounds, good lighting conditions, search in a fixed region, and certain types of vehicles (they would not detect LPs from vehicles such as motorcycles, trucks or buses).

- Many computer vision tasks have recently achieved a great increase in performance mainly due to the availability of large-scale annotated datasets (i.e., ImageNet) and the hardware (GPUs) capable of handling a large amount of data. In this scenario, Deep Learning (DL) techniques arise. However, despite the remarkable progress of DL approaches in
ALPR, there is still a great demand for ALPR datasets with vehicles and LPs annotations. The amount of training data is determinant for the performance of DL techniques.

- In this work, we propose a new robust real-time ALPR system based on the YOLO object detection Convolutional Neural Networks (CNNs). Since we are processing video frames, we also employ temporal redundancy such that we process each frame independently and then combine the results to create a more robust prediction for each vehicle.



## Technical Aspect

In order to have an efficient object detection (here, the vehicle number plates), I have used the most recently developed algorithm of YOLO series i.e. YOLOv4 backed up over a framework of Darknet.

Yolov4: Yolo abbreviates to You Only Look Once depicting its ability to detect objects and entities by using CNN (Convolutional Neural Network).Neural Network in YOLO uses weights trained by the user through annotated training data by using bounding boxes. Hence YOLO takes an image as input puts it through a Neural Network and gives the output in the image through bounding boxes.The input image is divided into SXS grid of cells.Each cell contributes to the object detection. Each cell predicts Bounding Boxes as well as Class probabilities. The prediction consists of 5 components (x,y,w,h,confidence).(x,y) represents the centre of the bounding box and (w,h) are the width and the height of the boxes.Confidence represents the Estimated Prediction Accuracy of the object.YOLO is extremely fast and accurate as compared to other algorithms and hence was our primary choice for this project.



### Dataset Source:

As, this project needed a lot of images to perform transfer learning with the weights of pre-trained model of YOLOv4 architecture which is trained on large scale dataset called COCO dataset(having more than 80 classes for object detection), so I used the Google Open Image Dataset for my custom retraining with that model.For extracting images for both training and testing, I used an toolkit called OIDToolKit4 which extracts the images from the Open Images Dataset by Google and create annotations for each files as YOLO architecture takes the image annotations present in a text file as an input. A complete directory for that toolkit is present above in this repository.Kindly follow the readme.md file of it to get into the specifications.




### Important Python Scripts:

1. ANPR_YOLOV4_Darknet_.ipynb: This takes care of the transfer learning of my custom image dataset which I extracted using the OIDToolKIt4.For better performance and use free GPU benefits by Google, Open this notebook on Google Colab.and perform the neccessary steps mentioned on it. 

2. convert_annotations.py: This python script is present under the subdirectory of OIDToolKit and it helps to extract out the images annotations on a .txt file.

3. generate_train.py and generate_test.py: The configuration files needed before we can begin to train our custom detector are the train.txt and test.txt files which hold the relative paths to all our training images and valdidation images.These scripts easily generate these two files withe proper paths to all images.

4. extract_frames.py: This python script extract frames out of the output video with bounding boxes into frames in order to perform Optical Character Recognition.

5. pytesseract_ocr.py: This python script takes care of performing Optical Character Recognition with the help of Google Tesseract API on the output images. 


## Technologies Used

![](https://forthebadge.com/images/badges/made-with-python.svg)

[<img target="_blank" src="https://keras.io/img/logo.png" width=200>](https://keras.io/) 

[<img target="_blank" src="https://scikit-learn.org/stable/_static/scikit-learn-logo-small.png" width=170>](https://scikit-learn.org/stable/_static/scikit-learn-logo-small.png)

[<img target="_blank" src="https://www.gstatic.com/devrel-devsite/prod/vbf66214f2f7feed2e5d8db155bab9ace53c57c494418a1473b23972413e0f3ac/tensorflow/images/lockup.svg" width=280>](https://www.gstatic.com/devrel-devsite/prod/vbf66214f2f7feed2e5d8db155bab9ace53c57c494418a1473b23972413e0f3ac/tensorflow/images/lockup.svg)

[<img target="_blank" src="http://image-net.org/index_files/logo.jpg" width=200>](http://image-net.org/index_files/logo.jpg) 

[<img target="_blank" src="https://jupyter.org/assets/nav_logo.svg" width=200>](https://jupyter.org/assets/nav_logo.svg) 

[<img target="_blank" src="https://pjreddie.com/media/image/yologo_2.png" width=200>](https://pjreddie.com/media/image/yologo_2.png)

[<img target="_blank" src="https://pjreddie.com/static/img/darknet.png" width=200>](https://pjreddie.com/static/img/darknet.png)

[<img target="_blank" src="https://opencv.org/wp-content/uploads/2020/07/cropped-OpenCV_logo_white_600x.png" width=200>](https://opencv.org/wp-content/uploads/2020/07/cropped-OpenCV_logo_white_600x.png)


