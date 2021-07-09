# use openCV to make real time face detection




## introduction :

#### openCV is a open source library for computer vision , image and video processing   and a lot of things .
#### openCV support a number of programming language like python , C++ , java ,etc
#### i will use openCV with python 


## steps : 

##### first of all you must install python , if you don't ,so go to this link [install python on windows(pycharm IDE)](https://www.guru99.com/how-to-install-python.html)

##### go to terminal option  that in pycharm ( at the bottom ) and write this command : 
 
 ```
 pip install opencv-python
 ```
##### then :

#### 1. Imports :

```
1 | import cv2 
2 | import os
```


#### 2. Initialize the classifier :

```
3 | cascPath=os.path.dirname(cv2.__file__)+"/data/haarcascade_frontalface_default.xml"
4 | faceCascade = cv2.CascadeClassifier(cascPath)
```



#### 3. Apply faceCascade on webcam frames :

```
5  | video_capture = cv2.VideoCapture(0)
6  | 
7  | while True:
8  |    # Capture frame-by-frame
9  |     ret, frames = video_capture.read()
10 | 
11 |     gray = cv2.cvtColor(frames, cv2.COLOR_BGR2GRAY)
12 |
13 |     faces = faceCascade.detectMultiScale(
14 |         gray,
15 |         scaleFactor=1.1,
16 |         minNeighbors=5,
17 |         minSize=(30, 30),
18 |         flags=cv2.CASCADE_SCALE_IMAGE
19 |     )
20 |
21 |     # Draw a rectangle around the faces
22 |     for (x, y, w, h) in faces:
23 |         cv2.rectangle(frames, (x, y), (x+w, y+h), (0, 255, 0), 2)
24 |
25 |     # Display the resulting frame
26 |     cv2.imshow('Video', frames)
27 |
28 |     if cv2.waitKey(1) & 0xFF == ord('q'):
29 |         break
```

##### ```video_capture``` is object have a device index or the name of the video file. Device index is just the number to specify which camera. when you put a parameter 0 that means a first camera  , and when put 1 that means second camera and so on 

#####  ``` detectMultiScale()``` is function that used to detect the faces and  will return a rectangle with coordinates(x,y,w,h) around the detected face.

#### 4. Release the capture frames :

```
30 | video_capture.release()
31 | cv2.destroyAllWindows()
```

##### ```destroyAllWindows()``` is a method used to force all the open windows to close at once .


#### then run a program 

![Screenshot (69)](https://user-images.githubusercontent.com/56357074/125143557-bfa07100-e123-11eb-8095-de4ec72ec767.png)


#### and when you want stop a webcam capture press 'q' , you can choose any key that you want to stop a capture by change a parameter of ```ord()``` that is in line 28 
