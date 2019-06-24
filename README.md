# Teleoperate Pioneer P3dx pn VREP using ROS and and Android App

<!-- <img src="picture/env.jpg"> -->

* Build 2D grid map with laserscan data avia `rviz`
* Control the mobile robot in the `vrep` simulation environment with keyboard
* Image Recognition and localization
* Visual Servoing (follow the yellow ball)
* roslaunch ros nodes

<img src="picture/rqt_graph.jpg">

## SETUP
#### ROS install and catkin
1. Install catkin: http://wiki.ros.org/catkin
2. Install ROS: http://wiki.ros.org/ROS/Installation
3. Configure and create catkin workspace
```
$ echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
$ mkdir -p ~/teleop_pioneer_slam/src
$ cd ~/teleop_pioneer_slam/
$ catkin_make
$ echo "source ~/teleop_pioneer_slam/devel/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```
#### Install V-REP
1. Dowload V-REP: http://www.coppeliarobotics.com/downloads.html
```
$ cp V-REP_PRO_EDU_V3_4_0_Linux.tar.gz ~
$ tar -zvxf ~/V-REP_PRO_EDU_V3_6_0_Linux.tar.gz
$ mkdir ~/V-REP
$ mv ~/V-REP_PRO_EDU_V3_6_0_Linux ~/V-REP
```
#### Load RosInterface and Some Packages
* Copy everything in this repo to `~/teleop_pioneer_slam/`
```
$ cd ~/teleop_pioneer_slam/
$ catkin build
$ source ~/.bashrc
```
* Copy /RosInterface/libv_repExtRosInterface.so
```
$ cd teleop_pioneer_slam/RosInterface
$ cp libv_repExtRosInterface.so  ~/V-REP
```

## RUN
1. open one terminal and run `$ roscore`
2. open another terminal and run `$ . ~/V-REP/vrep.sh`
>  Please pay attention to these message and if you see
```
Plugin ’RosInterface’: loading...
Plugin ’RosInterface’: load succeeded.
```
3. open `slam_peoneer_p3dx_2.ttt` in vrep's scene and press the start bottom
4. control the robot using the Android APP
```
$ rosrun key_teleop key_teleop.py
```
5. launch the ros nodes for face detection/recognition and automatic ball tracking
```
$ roslaunch hector.launch
```


<!-- <img src="picture/run.jpg"> -->
