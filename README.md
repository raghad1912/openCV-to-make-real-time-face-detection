# use openCV to make real time face detection




## introduction:
### openCV is a open source library for computer vision , image and video processing   and a lot of things .
### openCV support a number of programming language like python , C++ , java ,etc
### i will use openCV with python 

#### first of all you must install python , if you don't ,so go to this link [install python on windows(pycharm IDE)](https://www.guru99.com/how-to-install-python.html)

#### go to terminal option  that in pycharm ( at the bottom ) and write this command : 
 
 ```
 pip install opencv-python
 ```



#### 1. Imports:

```
1 | import cv2 
2 | import os
```


#### 2. Initialize the classifier:

```
3 | cascPath=os.path.dirname(cv2.__file__)+"/data/haarcascade_frontalface_default.xml"
4 | faceCascade = cv2.CascadeClassifier(cascPath)
```
#### 3. Apply faceCascade on webcam frames:

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

#### 4. Release the capture frames:

```
30 | video_capture.release()
31 | cv2.destroyAllWindows()
```


#### then run a program 



#### and when you want stop a webcam capture press 'q' 
