## REAL-TIME CRIMINAL IDENTIFICATION SYSTEM BASED ON FACE RECOGNITION
Small description about the project like one below
As the world has seen exponential advancement over the last decade, there is an abnormal 
increase in the crime rate and also the number of criminals are increasing at an alarming 
rate, this leads toward a great concern about the security issues. various causes of theft, 
stealing crimes, burglary, kidnapping, human trafficking etc. are left unsolved because the 
availability of police personnel is limited, many times there is no identification of the 
person who was involved in criminal activities. To avoid this situation an automated facial 
recognition system for criminal identification is proposed using Haar feature- based 
cascade classifier. This paper presents a real-time face recognition using an automated 
surveillance camera. This system will be able to detect and recognize
face automatically in real-time.

## About
<!--Detailed Description about the project-->
The face is crucial for human identity. It is the feature which best distinguishes a person. Face detection and 
recognition is the technology which is used to identify a person from a video or image.
we propose a face detection and recognition system for criminal identification using python along with OpenCV 
package.
Most of the common facial recognition techniques include target matching method, geometric feature recognition 
method, and principal component analysis method and so on.
Most of the criminals are mingled with us in our society and they are much hard to identify.
Traditionally, repeated criminals are identified by their biometrics such as thumbprint. But criminals are smart enough 
to not to leave their biometrics in crime scene.
Face recognition system built by using Principal Component Analysis (PCA) method. The two main disadvantages of 
using the PCA method are that computational complexity is high and it can only process the faces that have similar 
facial expressions.
## Features
<!--List the features of the project as shown below-->
- Construct a database connection with criminal records
- Secure network 
- High scalability.
- Less time complexity.

## Requirements
<!--List the requirements of the project as shown below-->
1.Operating system :Windows OS
2.Programmimg language :PYTHON
3.Platform :Pycharm

Hardware Requirements 
Processor : Intel core processor 
RAM :8GB
Hard disk : 430 GB
Compact Disk :650 Mb
Keyboard :Standard keyboard
Monitor :15.6 colour monitor

## System Architecture

<!--Embed the system architecture diagram as shown below-->

The architecture of a real-time criminal identification system based on face recognition 
involves several interconnected components working together to achieve accurate and efficient 
identification of individuals. At its core, the system consists of a front-end module responsible 
for capturing live video streams from surveillance cameras or other sources. These video 
streams are then fed into a face detection module, which uses computer vision algorithms to 
locate and extract facial regions from the frames in real-time. Once faces are detected, they are 
passed to a face recognition module, which compares the extracted facial features against a 
database of known criminals or suspects. This module utilizes machine learning models, such 
as convolutional neural networks (CNNs), to compute similarity scores and determine potential 
matches. The system's backend architecture includes a database management component for 
storing and managing facial data, as well as an integration layer for communication with 
external systems, such as law enforcement databases or access control systems. Additionally, 
the system may incorporate features for real-time alerts, notifications, and logging to facilitate 
timely responses and monitoring of identified individuals. Overall, the architecture of a real-
time criminal identification system based on face recognition is designed to be scalable, robust, 
and responsive, enabling effective detection and prevention of criminal activities in various 
environments.

## Code :
~~~
import the necessary packages
from Imutils import paths
import face recognition
import argparse
import pickle
import cv2
import os
# construct the argument parser and parse the arguments
ap = argparse.ArgumentParser()
ap.add_argument("-i", "--dataset", required=True,
help="path to input directory of faces + images")
ap.add_argument("-e", "--encodings", required=True,
help="path to serialized db of facial encodings")
ap.add_argument("-d", "--detection-method", type=str, default="cnn",
help="face detection model to use: either `hog` or `cnn`")
args = vars(ap.parse_args())
# grab the paths to the input images in our dataset
print("[INFO] quantifying faces...")
imagePaths = list(paths.list_images(args["dataset"]))
# initialize the list of known encodings and known names
knownEncodings = []
knownNames = []
# loop over the image paths
for (i, imagePath) in enumerate(imagePaths):
# extract the person name from the image path
print("[INFO] processing image {}/{}".format(i + 1,
len(imagePaths)))
name = imagePath.split(os.path.sep)[-2]
# load the input image and convert it from BGR (OpenCV ordering)
# to dlib ordering (RGB)
image = cv2.imread(imagePath)
rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
# detect the (x, y)-coordinates of the bounding boxes
# corresponding to each face in the input image
boxes = face_recognition.face_locations(rgb,
model=args["detection_method"])
# compute the facial embedding for the face
encodings = face_recognition.face_encodings(rgb, boxes)
# loop over the encodings
for encoding in encodings:
# add each encoding + name to our set of known names and
# encodings
knownEncodings.append(encoding)
knownNames.append(name)
# dump the facial encodings + names to disk
print("[INFO] serializing encodings...")
data = {"encodings": knownEncodings, "names": knownNames}
f = open(args["encodings"], "wb")
f.write(pickle.dumps(data))
f.close()
~~~
## Results and Impact
<!--Give the results and impact as shown below-->
By using this real time criminal identification using face recognition can get security while attaching criminal database with home camera and this will send a signal to nearby police station.

Thisay give a secure surrounding where theft happensore.

## Articles published / References
1] Nurul Azma Abdullah, Md. Jamri Saidi and Nurul Hidayah Ab Rahman "Face recognition for criminal identification: An 
implementation of principal component analysis for face recognition"The 2nd International Conference on Applied Science and 
Technology 2017 (ICAST')
[2] Apoorva.P, Ramesh.B and Varshitha.M.R "Automated criminal identification by face recognition using open computer vision 
classifiers" Third International Conference on Computing Methodologies and Communication (ICCMC 2019)

3] Rasanayagam, K.Kumarasiri, S.D.D, Tharuka, W. A. D. Samaranayake, N. Samarasinghe and P.
 Siriwardana "CIS: An Automated Criminal Identification System". 2018 IEEE International Conference on Information and 
Automation for Sustainability (ICIAfS)R. Nicole, "Title of paper with only first word capitalized," J. Name Stand. Abbrev., in press.

[4] Mantoro, T., Ayu, M. A., & Suhendi. (2018)." Multi-Faces Recognition Process Using Haar Cascades and Eigenface Methods" 2018 
6th International Conference on Multimedia Computing and Systems (ICMCS)




