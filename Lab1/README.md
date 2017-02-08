**Model-View-Projection Render**
================================
by *Qichen Wang*, G24147928

Screenshots
-----------
![screenshot 1](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab1/screenshot_1.png "screenshot 1")
![screenshot 2](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab1/screenshot_2.png "screenshot 2")
![screenshot 3](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab1/screenshot_3.png "screenshot 3")
![screenshot 4](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab1/screenshot_4.png "screenshot 4")

Input
-----
   1. Object geometric data in a **right-handed** model coordinate system (from a .d file)
   2. View Specifications (from a .txt file):
      1. Object's Euler angles (pitch, yaw, roll of object) in degrees
      2. In **right-handed** world coordinate system:
         1. object's position
         2. camera's position
         3. camera's reference point (where it's looking at)
         4. camera's up vector
         5. the distance, positive real number, between camera's position and the image plane 

Data flow
---------
![flow chart](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab1/data_flow.png "Data flow chart of the software")

Source code structure
----------------------
  * **/CMakeLists.txt** is the configurations to compile the project
  * **/data/** contains model geometric data (.d) files and viewing specs (.txt) files
  * **/nfd/** is a 3rd party open source software that brings up file explorer/finder windows
  * **/src/main.cpp** is the application's entry point
  * **/src/setup/**
    * **PolygonObject.cpp** provides an instance that stores an object's geometric data in local space and current (camera or screen) space
    * **Xformations.cpp** provides an instance that stores an object's viewing specs and creates the three transformation matrices
    * **FileLoader.cpp** loads data in .d file into an instance of **PolygonObject**; loads data in .txt file into an instance of **Xformations**
  * **/src/ui/**  
    * **StringUtils.cpp** generates and prints strings about viewing specs in the bottom-left corner of the viewport
    * **UserInputManager.cpp** creates a right-click menu and items in it then define their behaviors
  * **/src/matrix/**  
    * **VectorCalculation.cpp** contains primitive Maths for vector and matrix calculation 
    * **RotationHelper.cpp** contains Maths used in creating transformation matrices
  * **/src/draw/**  
    * **DrawPolygons.cpp** draws polygons of an object in 3d screen space
    

Demo video
---------
The source code can be compiled into a software to create frames and animations. 
Click the image below to play the demo video.

[![Play at youtube.com](https://img.youtube.com/vi/fFu08kVndPQ/0.jpg "Play at youtube.com")](https://youtu.be/fFu08kVndPQ)
