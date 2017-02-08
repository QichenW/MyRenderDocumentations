**Model-View-Projection Render**
================================
Qichen Wang, G24147928

Screenshots:
-----------
![screenshot 1](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab1/screenshot_1.png "screenshot 1")
![screenshot 2](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab1/screenshot_2.png "screenshot 2")
![screenshot 3](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab1/screenshot_3.png "screenshot 3")
![screenshot 4](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab1/screenshot_4.png "screenshot 4")

Input:
-----
   1. Object geometric data in **right-handed** model coordinate system (in a .d file under **/data**)
   2. View Specifications (in a .txt file under **/data**):
      1. Object's Euler angles (pitch, yaw, roll of object) in degrees
      2. In **right-handed** world coordinate system:
         1. object's position
         2. camera's position
         3. camera's reference point (where it's looking at)
         4. camera's up vector
         5. the distance, positive real number, between camera's position and the image plane 

Data Flow:
---------
![flow chart](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab1/data_flow.png "Data flow chart of the software")

Demo clip:
---------
[![Play at youtube.com](https://img.youtube.com/vi/fFu08kVndPQ/0.jpg "Play at youtube.com")](https://youtu.be/fFu08kVndPQ)
