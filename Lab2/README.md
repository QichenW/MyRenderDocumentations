**Render**
================================
   *Model-View-Projection, scan conversion, Z-Buffer Algorithm*
   -------------------------------------------------------------
Created by *Qichen Wang* on Feb 19, 2017

Screenshots
-----------
![screenshot 1](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab2/screenshot_1.png "screenshot 1")
![screenshot 2](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab2/screenshot_2.png "screenshot 2")
![screenshot 3](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab2/screenshot_3.png "screenshot 3")

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
![flow chart](https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab2/data_flow_2.png "Data flow chart of the software")

Source code structure
----------------------
  * **/CMakeLists.txt** is the configurations to compile the project
  * **/input/** contains model geometric data (.d) files and viewing specs (.txt) files
  * **/nfd/** is a 3rd party open source software that brings up file explorer/finder windows
  * **/src/main.cpp** is the application's entry point
  * **/src/setup/**
    * **PolygonObject.cpp** provides an instance that stores an object's geometric data in local space and current (camera or screen) space
    * **ModelXformation.cpp** 
    * **VandPxformations.cpp** provides an instance that stores an object's viewing specs and creates the three transformation matrices
    * **FileLoader.cpp** loads data in .d file into an instance of **PolygonObject**; loads data in .txt file into an instance of **Xformations**
  * **/src/ui/**  
    * **UserInputManager.cpp** creates a right-click menu and items in it then define their behaviors
    * **StringUtils.cpp** generates and prints strings about viewing specs in the bottom-left corner of the viewport
* **/src/matrix/**  
    * **VectorCalculation.cpp** contains primitive Maths for vector and matrix calculation 
    * **XformationHelper.cpp** contains Maths used in creating transformation matrices
  * **/src/draw/**  
    * **DrawPolygons.cpp** given the data after perspective transformation, do device transformation then scan conversion with Z-buffer algorithm to calculate the RGB value of each pixel, finally draw the polygons of all objects in the viewport with hidden surface removed
  * **/src/data/**
    * **Pixel.cpp** provides instances that store RGB values of a pixel
    * **EdgeEntry.cpp** provides instances to be stored in the edge tables (xmin, ymax, slope)
    * **EdgeTable.cpp** provides instances function as the edge table (ET) and active edge table (AET) for scan conversion with z-buffer algorithm, where ymin, depth_min, depth_slope are also recorded (and needs to be migrated to EdgeEntry.cpp in the next phase of this project)
    
