**Model-View-Projection Render**
================================
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
   
   
Output:
------
  * 3d data drawn in **left-handed** screen coordinated system with back-facing polygons removed
