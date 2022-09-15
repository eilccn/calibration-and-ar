# Calibration and Augmented Reality

## Project Description
This program implements camera calibration then uses the calibration data in order to generate virtual objects within a scene. It has the ability to detect a target point and then place a virtual object in the scene relative to the target. As a result, the virtual object will be capable of orienting itself according to the location and movements of the camera (or target). A 9x6 checkerboard (below) is used as a target and means of camera calibration. 

<img src="/readme-images/checkerboard.png" width=50%>

## Instructions for running executables:
1. Place all .cpp and .h files along with a CMakeLists.txt file into a directory (i.e. called "project")
2. Open "project" in Visual Studio Code
3. Build "project" using the "CMake Tools" extension
4. cd into the build directory then run the program by entering "./project" 
5. Please see the requirements.txt file for necessary plug-ins

### Keypress Definitions
```
q = quit
s = save image as .png, save corner locations, and save 3D world points
c = calibrate camera
spacebar = compute current position of camera
f = stop computing current position of camera
x = draw chessboard corners
d = draw 3D axes
o = draw 3D virtual object
r = detect robust features (harris corners)
a = detect arcuo markers
```

## Program Features

### Detecting and Extracting Chessboard Corners
<img src="/readme-images/chessboard-corners.png" width=50%>
Description: Calibration image with chessboard corners highlighted. The functions <a href="https://docs.opencv.org/3.4/d9/d0c/group__calib3d.html#ga93efa9b0aa890de240ca32b11253dd4a" target="_blank">findChessboardCorners</a>, <a href="https://docs.opencv.org/4.x/dd/d1a/group__imgproc__feature.html#ga354e0d7c86d0d9da75de9b9701a9a87e" target="_blank">cornerSubPix</a>, and <a href="https://docs.opencv.org/3.4/d9/d0c/group__calib3d.html#ga6a10b0bb120c4907e5eabbcd22319022" target="_blank">drawChessboardCorners</a> were used in order to detect, extract, and draw the chessboard corners. The user then captures a set of images and saves the corner locations and 3D world points from each image via the 's' keypress functionality. 

### Camera Calibration and Selecting Calibration Images
<a href="https://calib.io/blogs/knowledge-base/calibration-best-practices" target="_blank">Tips for Calibration</a>

<img src="/readme-images/calibration.png" width=50%>
Description: Upon obtaining the chessboard corners and 3D world points of at least 5 images, we can run camera calibration via <a href="https://docs.opencv.org/3.4/d9/d0c/group__calib3d.html#ga3207604e4b1a1758aa66acb6ed5aa65d" target="_blank">cv::calibrateCamera</a>. After calibration, the camera saves the intrinsic parameters, the camera matrix, and distance coefficient data, to a file to be read for later AR functionalities. It also prints out the camera matrix and distortion coefficients to the terminal, along with the final re-projection error. An optimal reprojection error is as close to 0 as possible.

### Calculating Current Position of the Camera
<img src="/readme-images/camera-position.png" width=50%>
Description: The rotation (R) and translation (T) values are obtained from the <a href="https://docs.opencv.org/3.4/d9/d0c/group__calib3d.html#ga549c2075fac14829ff4a58bc931c033d" target="_blank">solvePNP</a> function. The camera calibration parameters that were previously saved into a file, then starts a video loop. For each frame, it tries to detect a chessboard. If found, it grabs the locations of the corners and points. It then populates the points, corners, camera matrix, distance coefficients, rotation values (an output value initialized as a cv::Mat), and translation values (an output value initialized as a cv::Mat) into the function solvePnP to obtain the board's pose (rotation and translation).

### Projecting 3D Axes
<img src="/readme-images/3d-axis.png" width=50%>
Description: 3D axes on the board drawn from a point on the board using drawFrameAxes. In the real-time feed I have to angle the board certain ways in order for the axes to align correctly. I think this has to do with the fact that I may have taken a lot of similar images from only a handful of angles. If I were to take better calibration images and take a lot more calibration images, the axes would show up more accurately.

### Creating a Virtual Object


### Detecting Robust Features
| Greyscale | Without Greyscale |
|---|---|
| <img src="/readme-images/harris-corners-1.png" width=50%> | <img src="/readme-images/harris-corners-2.png" width=50%> |


###### Khoury Wiki
https://wiki.khoury.northeastern.edu/x/R9l5Bg
