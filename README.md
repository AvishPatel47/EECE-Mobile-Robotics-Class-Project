# EECE-Mobile-Robotics-Class-Project

## Execution:
Setup the bashrc file on Remote PC using instructions as per:https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/#pc-setup

Configure the wifi settings and setup the bashrc file for turtlebot as per instructions from:
https://emanual.robotis.com/docs/en/platform/turtlebot3/sbc_setup/#configure-the-wifi-network-setting-1

Run ```roscore``` in your PC. 

For **Turtlebot3**, excute following: 
>*For each step it required to be implemented in new terminal window and followed by`SSH` command to get into the robot's system*
1. To bringup the Turtlebot, run ```roslaunch turtlebot3_bringup turtlebot3_robot.launch```
2. To launch the Camera, run ```roslaunch turtlebot3_bringup turtlebot3_rpicamera.launch```

In **RemotePC**, excute following:
> For autonomous exploration and ocupancy grid mapping:
1. To implement *move_base*, run ```roslaunch turtlebot3_navigation move_base.launch```
2. To implement *gmapping*, run ```roslaunch turtlebot3_slam turtlebot3_slam.launch```
3. To implement frontier exploration using *explore_lite*, run ```roslaunch explore_lite explore.launch```
> For April tag detections
4. To implement transformations between map and robots components, run ```roslaunch turtlebot3_explore tf_camera.launch```
5. To implement tag detections using *apriltag_ros*, run ```roslaunch apriltag_ros c_detect.launch```


To view the results:
run ```rqt_image_view``` to see camera window for tags detections
***OR***
In the ```rviz``` window that is already running, add ```image``` and ```tf``` topics

To save the results:
record all the topics using, run```rosbag record -a``` ***AND***
save the map by running ```rosrun map_server map_saver -f ~/map```
