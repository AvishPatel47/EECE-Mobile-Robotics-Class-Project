# EECE-Mobile-Robotics-Class-Project
## Setup:
In your remote PC, do the following:
1.  Clone the repository into the ```catkin_ws/src```. This includes the necessary packages such as ```turlebot3_explore```,```turtlebot3_navigation```, ```turtlebot3_slam```,```explore_lite```, and ```apriltag_ros```.
2. Go to ```catkin_ws``` and ```catkin_make```.
3. Source the workspace using ```source devel/setup.bash```

In your Turtlebot3, do the following:
1. ```SSH``` into your raspberrypi of your turtlebot from your remote PC by entering ```sudo ssh ubuntu@ip_address```. Enter the password when required.
2. Install cv_camera package using ```sudo apt install ros-noetic-cv-camera```.
4. Calibrate the camera by following the instructions.
5. Source the ```catkin_ws``` using ```source devel/setup.bash```


## Execution:
Setup the bashrc file on the Remote PC using the instructions as per: https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/#pc-setup

Configure the wifi settings and setup the bashrc file for turtlebot as per instructions from: https://emanual.robotis.com/docs/en/platform/turtlebot3/sbc_setup/#configure-the-wifi-network-setting-1

Run ```roscore``` on your PC.

For **Turtlebot3**, execute following:
>*For each step it is required to be implemented in the new terminal window and followed by`SSH` command to get into the robot's system*
1. To bringup the Turtlebot, run ```roslaunch turtlebot3_bringup turtlebot3_robot.launch```
2. To launch the Camera, run ```roslaunch turtlebot3_bringup turtlebot3_rpicamera.launch```
In **RemotePC**, execute following:
> For autonomous exploration and ocupancy grid mapping:
1. To implement *move_base*, run ```roslaunch turtlebot3_navigation move_base.launch```
2. To implement *gmapping*, run ```roslaunch turtlebot3_slam turtlebot3_slam.launch```
3. To implement frontier exploration using *explore_lite*, run ```roslaunch explore_lite explore.launch```
> For April tag detections
4. To implement transformations between map and robots components, run ```roslaunch turtlebot3_explore tf_camera.launch```
5. To implement tag detections using *apriltag_ros*, run ```roslaunch apriltag_ros c_detect.launch```

To view the results:
run ```rqt_image_view``` to see the camera window for tags detections
***OR***
In the ```rviz``` window that is already running, add ```image``` and ```tf``` topics

To save the results:
record all the topics using, run```rosbag record -a``` ***AND***
save the map by running ```rosrun map_server map_saver -f ~/map```
