# calibration-exercise
## Camera image rectification
To calibrate the camera, we use the camera_calibration package. I made the launch file calibrate_camera.launch.
The launch file plays the bag file and runs the camera_calibration package simultaneously. When the routine is done, click "Calibrate" then "Save". This will save .yaml file that contains new calibration parameters.

![Screenshot](https://github.com/aellaboudy/calibration-exercise/blob/master/Screen%20Shot%202018-02-11%20at%201.13.12%20PM.png)

Now we use the change_camera_info.py to write a new bag file with the new camera_info parameter overwritten.

Now we have a new bag file with the correct camera_info topic. We create another launch file to play this new bag file and also the image_proc and image_view packages to view the new rectified image vs the old unrectified image.

![Screenshot](https://github.com/aellaboudy/calibration-exercise/blob/master/Screen%20Shot%202018-02-11%20at%201.35.06%20PM.png)


## Lidar to Camera Calibration
To align the lidar point cloud to the camera image, we must first find some corresponding features between the two datasets. Usually during calibration there are some physical features that are created to easily find corresponding points between lidar and camera images. In this case, however, we will have to manually find some points between the image and the lidar point cloud that correspond to each other. In this case, we can pick a frame where the checkerboard is clearly visible and label it's corners in both the lidar image and the camera image. These points are fed via a JSON file to a camera-to-lidar calibration module (ros-camera-lidar-calibration) that outputs the tranformation and rotation between the points. This transofrmation and rotation parameters are fed to a static transformer publisher in image_to_lidar.launch where it aligns the lidar to the camera frame. Screen shot of the two aligned below:

![Screenshot](https://github.com/aellaboudy/calibration-exercise/blob/master/Screen%20Shot%202018-02-12%20at%2012.34.14%20AM.png)
