# calibration-exercise
## Camera image rectification
To calibrate the camera, we use the camera_calibration package. I made the launch file calibrate_camera.launch.
The launch file plays the bag file and runs the camera_calibration package simultaneously. When the routine is done, click "Calibrate" then "Save". This will save .yaml file that contains new calibration parameters.

![Screenshot](https://github.com/aellaboudy/calibration-exercise/blob/master/Screen%20Shot%202018-02-11%20at%201.13.12%20PM.png)

Now we use the change_camera_info.py to write a new bag file with the new camera_info parameter overwritten.

Now we have a new bag file with the correct camera_info topic. We create another launch file to play this new bag file and also the image_proc and image_view packages to view the new rectified image.
