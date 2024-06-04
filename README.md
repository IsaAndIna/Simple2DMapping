# Simple2DMapping
A simple application for 2d mapping from images. It contains tasks such as "Focal Length Estimation" &amp; "Camera Pose Estimation", and is supposed to be applied to "Pedestrian Localization" tasks.


## Objective
The objective of this application is to provide a platform for 3d reconstrction from images taken with fixed cameras (relatively static). It is done following the next steps.

## Contents
### 1. __Focal length estimation__
Considering that the focal length is not always available in a needed unit, firstly we estimate it.
More precisely, in this part, we estimate the camera pose(Degree of Freedom: DoF=6) and the focal length(DoF=1), by applying 4 colinearity constraints, each of them providing 2 constraints.
    - __Inputs__: 4 pairs of XYZ absolute orthogonal coordinates (arbitrary scale) and the corresponding uv image coordinates. For example, the 4 corners of a square can be a good choise of points. The size of the square can be given arbitrary. 
    - __Medium__: Camera pose (X,Y,Z,$\omega$, $\phi$, $\kappa$) in the XYZ absolute orthogonal coordinate system of the given points.
    - __Main output__: focal length $c$ of the camera, in pixel unit.
    - __Assumptions__: 1. There is no center gap in the camera. In other words, the lens axis pass through the center of the image, thus $\Delta x=\Delta y=0$. 2. There are no lens distortions, either.
    - __Things to be careful of__: The given points must not be on a single plane parallel to the image plane, or the focal length $c$ will not be determined.

#### Example of Focal length estimation
The picture below contains a A4-size paper(210mm x 297mm).
![A4-size paper](figure/focal_length_demo.jpg)
By providing the uv image coordinates of the 4 corners, we can calculate the focal length of the camera(e.g. 1036.39 pixels, where the size of the image is 1280 x 720).

### 2. __Camera Pose estimation__\
Now that the focal length is obtained, we can effectuate a camera pose estimation of any picture taken with this camera. In this part, we obtain the 

![dining table](figure/camera_pose_estimation_demo.jpg)
