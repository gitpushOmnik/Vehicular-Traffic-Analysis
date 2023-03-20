# Vehicular-Traffic-Analysis

Speed detection and analysis of traffic data is a challenging task that plays a vital role in the safety of civilians considering the dangers imposed with everyday transportation. The presence of an automated and intelligent traffic surveillance system in today’s civilized society is of critical importance for monitoring traffic activity and detecting overspeeding vehicles. We present an accurate and effective computer vision-based system for monitoring vehicular traffic by detecting and classifying vehicles and extracting crucial statistics such as average road speed, overspeeding detections, vehicle types, frequency of vehicles, etc. Our proposed system implements a machine learning-based approach that makes use of computer vision techniques and classifiers on real-world traffic video surveillance for effective vehicular detection and classification as well as for obtaining traffic statistics.

**The paper based on this project has been published in the Journal of Emerging Technologies and Innovative Research**

## Introduction

The concept of Machine Learning is to create a system that automatically learns and evolves without being explicitly programmed. Humans have applied this method to various fields of technology, research, and engineering to achieve systems that can determine future weather, convert a person’s voice to text, predict a quantity’s value from other values that it seems to depend upon, recognize objects, texts, and faces in an image, etc. These tasks are easy for humans to perform, and now we can program machines to do the same. One system mentioned above is "Image Recognition": The task of recognizing and identifying entities that are present in an image. These entities may include physical objects, text, numbers, faces, patterns, etc. This model has various applications from facial recognition for security to text recognition for simple convenience.

One such scenario where Image Recognition is applicable is traffic and vehicles. Given a big set of images of vehicles, a system can be trained to detect vehicles in more images. Similarly, the system can learn to detect objects that are typically seen with vehicles like roads and traffic lights. Such a system would be useful because it will enable a vast array of analyses and computations to be done on the images. This can be further expanded by using a large set of images taken in quick succession that show the movement of the vehicle, in other words: a video. Frames extrapolated from a video will show clear and well-defined displacement of the vehicle as we move along the frames. If the system detects the vehicle in each frame, it will be able to quantify the vehicle’s displacement. This, coupled with the background that stays in place, provides us with enough information to deduce the speed of the moving vehicle.

Now we have a system that can detect the speeds of vehicles in a video. The traffic police can use this to detect overspeeding vehicles. The system can instantly provide the number plates of these vehicles. If installed at a particular road, it can provide data such as the speed and type of every vehicle that passes through that road. If a sufficient amount of data is gathered, it can be analyzed to determine the average speed of vehicles on the road, most popular vehicle types, times when the road has the most traffic, etc. This analysis can be insightful and useful.

## Tools and Technologies Used

• OS: Windows 10/11, Mac, Ubuntu/ Fedora and different Linux distributions

• Programming Language: Python

• Frontend scripting: HTML, CSS, Bootstrap, JavaScript

• Backend scripting: Flask

• IDE: Jupyter Notebook, Visual Studio Code

• Database: MySQL

• Algorithms: YOLOv5, YOLOv3, DeepSort

## Dataset Description

We make use of a custom dataset for vehicle detection and classification derived from publicly available Microsoft Common Objects In Context (MS COCO) dataset.

The dataset consists of 5 different classes which are bicycle, car, motorcycle, bus, and truck. We performed various image pre- processing and transformation steps such as image augmentation, image rotation, image flip etc. We have also applied data normalization and scaling on our dataset to help improve the final accuracy of the model. We have converted the detected bounding box format that conforms to that of the object detection algorithm’s standard format. Our dataset consists of 19,758 images out of which the training images are 15,807, and the testing as well as validation are 3,951 images.

## Overview

### Dashboard:
The dashboard is the main user interaction module. Upon opening the web- portal, the user will be greeted by the application dashboard. It contains options to access all of the part intented for a user like logging in or registering, exiting the application, uploading a video, and reviewing a video. It presents the user with an easy to use and familiar UI containing standard buttons and actions that the user may already be used to which make it smoother for the user to access the full functionality of the website.

### 1. Upload video for vehicle classification
The role of this module is to take a video from the user that is received from the web portal, and feed it to the the trained classification model. The classification model was constructed using the ensembled architec- ture of YOLOv5 and YOLOv3 object detection algorithms trained on the filtered Microsoft COCO (Common Objects in Context) dataset contain- ing 5 classes: car, truck, motorcycle, bus, and bicycle. Thus, it will detect and then classify the vehicle into one of the above mentioned classes. The module will also process the video by applying the DeepSort algorithm which will detect the movement and trajectory of every vehicle, even if it gets obscured by another vehicle or object. The resultant output is a video with overlaid bounding box on every detected vehicle in every frame with the respective frame and vehicle id mentioned on top of the bounding box.

### 2. Upload video for counting vehicle
After the classification and detection of vehicles in a given video, this module will count the total number of vehicles that pass through the region of interest defined by the user. This is aided further by the use of Deepsort as it assigns a distinct id to every vehicle, which means the number of unique vehicles is equal to the number of unique tracking ids. The purpose of this model is to assess the traffic on the monitored road, as the greater the count, the higher the traffic. It will also provide an estimate to how the traffic changes throughout a day.

### 3. Upload video for speed estimation
Once the vehicles are detected and classified in the given video, this model can begin to calculate their speed. YOLOv3 model is employed for estimation of average speed of the detected vehicles. Estimated speed will be mentioned on the top of bounding boxes of the detected vehicles with their respective ids. A resultant csv file is generated to store details of over-speeding vehicles. The csv file stores information such as vehicle id, speed of the vehicle and if the vehicle was over-speeding or not.

### Login Module
The login module is responsible for user authentication. Every existing user must authenticate their credentials. It will ask for a username and password to confirm the user’s identity. This will enable them to access all the func- tionalities of the website.

### Sign Up Module
This module is responsible for registering users in the database of the website. Every new user must provide their credentials like their email address, user- name and password which will be used to create their profile in the database. The provided password will be used later during login to authenticate the user. Signing up is necessary to use the website.

## Workflow

![alt text](https://github.com/gitpushOmnik/Vehicular-Traffic-Analysis/blob/main/Images/Workflow.png)

## Testing Performed

### Unit Testing:
Each unit or individual component of the software application is tested as part of unit testing. A functional test begins at this level. This method involves verifying the function of individual components. The goal of unit testing is to isolate each part of the program and show that individual parts are correct in terms of requirements and functionality.

### Integration Testing
Units or independent modules of the system are tested in groups during integration testing. The integration testing level’s goal is to expose flaws during the interaction of interrelated components or units. Integration testing can be significantly sped up using this method. The integration process will be more difficult if the test cases are not properly recorded and their results aren’t properly recorded.

### Regression Testing
Software regression testing ensures an application is still functional after an application has undergone any changes, updates, or improvements. It ensures that existing features, when tested, remain stable and functional.
In addition to bug fixes, software enhancements, configuration changes, and even electronic component substitutions may require regression testing. Test automation is often employed in regression test suites that grow as more defects are found.

### Validation Testing
Tests are conducted to determine if the tested and developed software meets the needs of the client/user. A detailed analysis of the business requirement logic or scenarios is required. A validation tester should verify that the right product is being developed in accordance with the specified requirements.

### Alpha Testing
Alpha testing determines whether a new product performs as expected during the initial phases of development. As many bugs or usability issues as possible are uncovered during alpha testing before the final release of the product to a wide audience.

### Beta Testing
In beta testing, users are given the opportunity to test a product in a production environment so they can identify any bugs or issues before a general release. Beta tests are conducted with a sample of the intended audience early in the development process, followed by alpha testing conducted by the internal staff.

### Load Testing
In a load testing environment, bottlenecks in the system can be identified and avoided before they occur in production. The system’s reliability and performance are assured when it has been subjected to load testing.

## Output Website and Results

![alt text](https://github.com/gitpushOmnik/Vehicular-Traffic-Analysis/blob/main/Images/Image1.png)
![alt text](https://github.com/gitpushOmnik/Vehicular-Traffic-Analysis/blob/main/Images/Image2.png)
![alt text](https://github.com/gitpushOmnik/Vehicular-Traffic-Analysis/blob/main/Images/Image3.png)
![alt text](https://github.com/gitpushOmnik/Vehicular-Traffic-Analysis/blob/main/Images/Image4.png)
![alt text](https://github.com/gitpushOmnik/Vehicular-Traffic-Analysis/blob/main/Images/Image5.png)
![alt text](https://github.com/gitpushOmnik/Vehicular-Traffic-Analysis/blob/main/Images/Image6.png)
![alt text](https://github.com/gitpushOmnik/Vehicular-Traffic-Analysis/blob/main/Images/Image7.png)
![alt text](https://github.com/gitpushOmnik/Vehicular-Traffic-Analysis/blob/main/Images/Image8.png)

## Classification

Our project successfully detects, classifies and tracks different vehicles as well as estimates its speed based on the surveillance video provided. We have trained custom state-of-the-art deep learning models which are YOLOv5 and YOLOv3. The parameter for determining accuracy for object detection models is mean average precision (mAP) which comes out to be 66.90% for YOLOv5 model and 69.20% for YOLOv3 model after training it using Microsoft’s COCO (Common Objects in Context) dataset upon 5 different classes of vehicles which are car, motorcycle, bus, truck and bicycle. We have achieved an increased accuracy of 10.1% in our custom YOLOv5 model with respect to the pre-trained YOLOv5 model. Furthermore, we have performed model ensembling between our custom YOLOv3 and YOLOv5 models. For multiple object tracking, we have integrated our ensembled model with DeepSORT architecture that produces high precision and accuracy. The speed of the vehicles is estimated using the YOLOv3 model.


