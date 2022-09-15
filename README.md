# Calibration and Augmented Reality

## Project Description
For this project we implemented a program that can calibrate a camera and then use the calibration data in order to generate virtual objects in a scene. The final program has the ability to detect a target point and then place a virtual object in the scene relative to the target. As a result, the virtual object will be capable of orienting itself according to the location and movements of the camera (or target). In this specific implementation we are using a 9x6 checkerboard checkerboard.png  as a target and means of camera calibration. 

## Instructions for running executables:
1. Place all .cpp and .h files along with a CMakeLists.txt file into a directory (i.e. called "project4")
2. Open "project4" in Visual Studio Code
3. Build "project4" using the "CMake Tools" extension
4. Run the program by entering "./project4" 

### Keypress Definitions
```
q = quit
s = save image as .png
c = calibrate camera
spacebar = compute current position of camera
f = stop computing current position of camera
x = draw chessboard corners
d = draw 3D axes
o = draw 3D virtual object
r = detect robust features (harris corners)
a = detect arcuo markers
```

### Video Capture Set-Up
1. 

## Program Features

### Detecting and Extracting Chessboard Corners

<img src="/readme-images/chessboard-corners.png" width=50%>

### Camera Calibration

<img src="/readme-images/calibration.png" width=50%>

### Calculating Current Position of the Camera

<img src="/readme-images/camera-position.png" width=50%>

### Projecting 3D Axes

### Creating a Virtual Object

### Detecting Robust Features


###### Khoury Wiki
https://wiki.khoury.northeastern.edu/x/R9l5Bg
