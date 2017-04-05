**Render**
================================
   *3D transformations, Rasterization, Illumination, Shading, Texture Mapping*
   -------------------------------------------------------------
by *Qichen Wang*

created on Feb 8th 2017, last edited on Apr 3rd 2017

Screenshots
-----------
**Texture Mapping with Phong shading**
![screenshot 1](https://github.com/QichenW/MyRenderDocumentations/blob/master/progress/screen_shot_1.png "screenshot 1")
![screenshot 2](https://github.com/QichenW/MyRenderDocumentations/blob/master/progress/screen_shot_2.png "screenshot 2")
![screenshot 3](https://github.com/QichenW/MyRenderDocumentations/blob/master/progress/screen_shot_3.png "screenshot 3")

*Texture input*

<img src="https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab4/stripes_green.png" width="120"/><img src="https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab4/harlequin_check_purple.png" width="120"/><img src="https://github.com/QichenW/MyRenderDocumentations/blob/master/Lab4/leopard_print_yellow.png" width="120"/> 


**Phong shading**
![screenshot 1](https://github.com/QichenW/MyRenderDocumentations/blob/master/progress/screenshot__1.png "screenshot 1")
**Gouraud shading**
![screenshot 2](https://github.com/QichenW/MyRenderDocumentations/blob/master/progress/screenshot_2.png "screenshot 2")
**Constant shading**
![screenshot 3](https://github.com/QichenW/MyRenderDocumentations/blob/master/progress/screenshot_3.png "screenshot 3")
**Random coloring**
![screenshot 4](https://github.com/QichenW/MyRenderDocumentations/blob/master/progress/screenshot_4.png "screenshot 4")
**Wireframe**
![screenshot 5](https://github.com/QichenW/MyRenderDocumentations/blob/master/progress/screenshot_5.png "screenshot 5")
Demo video
---------
This render is capable of creating animations on-the-fly. Click the image below to play the demo video.

[![Play at youtube.com](https://img.youtube.com/vi/SxIMqGQxuWE/0.jpg "Play at youtube.com")](https://youtu.be/SxIMqGQxuWE)

Input
-----
   1. Object geometric data in a **right-handed** model coordinate system (from a .d file)
   2. View Specifications (from a .txt file):
      1. number of objects
      2. each object's Euler angles (pitch, yaw, roll of object) in degrees
      3. each object's color (RGB intensities, both diffusive and specular)
      4. In **right-handed** world coordinate system:
         1. each object's position
         2. the camera's position
         3. the camera's reference point (where it's looking at)
         4. the camera's up vector
         5. the half x- and half y-span of the viewing frustum's near size, the distances between the camera's position and the viewing frustum's near size and between it and the far size
         6. the vector from scene to light source (assuming the light source is infinitely far)
   3. Arbitrary PNG files

Data flow
---------
![flow chart](https://github.com/QichenW/MyRenderDocumentations/blob/master/progress/data_flow_4.png "Data flow chart of the software")

Source code structure
----------------------

  * **/src/main.cpp** is the application's entry point
  * **/src/setup/**
    * **PolygonObject.cpp** provides instances that store all objects' geometric data in local space **statically** and in the current (world, camera, screen or device/viewport) space **seperately**
    * **ModelXformation.cpp** provices instances that store information about each object's rigid transformation from local space to world coordinate system, and create the corresponding model transformation matrices
    * **VandPxformations.cpp** provides an instance that stores viewing specs about camera and viewing frustum, and creates the view and perspective transformation matrices
    * **Illumination.cpp** provides instances to describe light sources and functions which, given the normal vector, calculate ambient, diffusive, specular terms of RGB intensities
    * **FileLoader.cpp** loads data in .d file then **statically** stores it in **PolygonObject**; loads specifications in .txt file into an instance of **VandPxformations** and several instances of **ModelXformation**
  * **/src/ui/**  
    * **UserInputManager.cpp** creates a right-click menu and items in it then define their behaviors
    * **StringUtils.cpp** generates and prints strings about viewing specs in the bottom-left corner of the viewport using openGL's api, for demostration only
  * **/src/matrix/**  
    * **VectorCalculation.cpp** contains primitive Maths for vector and matrix calculation 
    * **XformationHelper.cpp** contains Maths used in creating transformation matrices
  * **/src/draw/**  
    * **DrawPolygons.cpp** provides functions that given the data after perspective transformation, do device (viewport) transformation then scan conversion with Z-buffer algorithm to figure out the correct RGB value of each pixel, and finally draw the polygons of all objects in the viewport with hidden surfaces removed
  * **/src/data/**
    * **Pixel.cpp** provides instances that store the RGB value of a pixel
    * **EdgeEntry.cpp** provides instances to be stored in the edge tables (ymin, xmin, ymax, slope, depth_min, depth_slope)
    * **EdgeTable.cpp** provides instances that function as the edge table (ET) and active edge table (AET) for scan conversion with z-buffer algorithm
  * **/input/** contains model geometric data (.d), viewing specs (.txt) and texture (.png) files
  * **/nfd/** is a 3rd party open source software that brings up file explorer/finder windows
  * **/lodepng/** is a 3rd party open source software that loads image files as RGB arrays
  * **/CMakeLists.txt** is the configurations to compile the project
