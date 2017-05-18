# hector_quadrotor

This is a slightly-modified version of TU Darmstadt's hector_quadrotor repository, with kinetic-devel set as the main branch. The original repository is available at: https://github.com/tu-darmstadt-ros-pkg/hector_quadrotor


Table of Contents
=================

* Installation
* Requirements, Setup, Use
* License
* Contact


Installation
============

Instructions for installing this repository (hector_quadrotor) are available at the following wiki site (but reproduced below):
* https://github.com/AS4SR/general_info/wiki/(Some)-Robots-in-ROS-plus-Gazebo!#hector_quadrotor

There are three ways to install hector_quadrotor, pick one of these:
* Install manually using git:
```
    source /opt/ros/kinetic/setup.bash
    sudo apt install ros-kinetic-joystick-drivers ros-kinetic-teleop-twist-keyboard
    mkdir ~/catkin_ws/src
    cd ~/catkin_ws/src
    git clone https://github.com/AS4SR/hector_quadrotor.git # forked from kinetic-devel branch of https://github.com/tu-darmstadt-ros-pkg/hector_quadrotor.git
    git clone -b catkin https://github.com/tu-darmstadt-ros-pkg/hector_slam.git
    git clone -b catkin https://github.com/tu-darmstadt-ros-pkg/hector_localization.git
    git clone -b kinetic-devel https://github.com/tu-darmstadt-ros-pkg/hector_gazebo.git
    git clone -b kinetic-devel https://github.com/tu-darmstadt-ros-pkg/hector_models.git
    cd ~/catkin_ws
    catkin_make
    source devel/setup.bash
```
-OR-
* Install using wstool:
```
    source /opt/ros/kinetic/setup.bash
    sudo apt install ros-kinetic-joystick-drivers ros-kinetic-teleop-twist-keyboard
    sudo apt install python-wstool ros-kinetic-geographic-msgs
    mkdir ~/catkin_ws/src
    cd ~/catkin_ws
    wstool init src https://raw.githubusercontent.com/AS4SR/hector_quadrotor/kinetic-devel/tutorials.rosinstall
    catkin_make
    source devel/setup.bash
```
-OR-
* Install using rosinstall:
```
    source /opt/ros/kinetic/setup.bash
    sudo apt install ros-kinetic-joystick-drivers ros-kinetic-teleop-twist-keyboard
    mkdir ~/catkin_ws/src
    rosinstall ~/catkin_ws/src /opt/ros/kinetic https://raw.githubusercontent.com/AS4SR/hector_quadrotor/kinetic-devel/tutorials.rosinstall
    cd ~/catkin_ws
    catkin_make
    source devel/setup.bash
```


Requirements, Setup, Use
========================

This requires a ROS kinetic install on an Ubuntu 16.04 LTS instance. (This has been tested-working under VirtualBox and as a native Ubuntu install. A native Ubuntu installation is preferred, as it runs much faster and more efficiently, and gazebo is much more stable.)

For more detailed Ubuntu O/S installation instructions, see:
* https://github.com/AS4SR/general_info/wiki/Instructions-for-installing-ROS-and-Gazebo!-:)
* https://github.com/cmcghan/vagrant-rss/blob/ubuntu-16.04-xenial/README.md

Note that this and other ROS code does **not** work on Bash on Ubuntu on Windows for Windows 10, as of 2017-05-18, due to issues with the Linux Subsystem and also the ros_comm library's (mis)handling of TCP/IP errors/warning messages.

Setup consists of installing `ros-kinetic-desktop-full` on the Ubuntu instance prior to installation/compilation of the hector_quadrotor repository.

Note that if you have not added lines in your .bashrc file to automatically source the ROS system-wide installed packages and your catkin workspace, that you will have to run the following lines before anything else in any terminal you open.
* Assuming that ~/catkin_ws is your workspace directory:
```
    source /opt/ros/kinetic/setup.bash
    source ~/catkin_ws/devel/setup.bash
```

Run the original "indoors" tutorial sim via:
* terminal #1:
```
    roslaunch hector_quadrotor_demo indoor_slam_gazebo.launch
```
* terminal #2: ([link]()http://answers.ros.org/question/217686/controlling-hector-quadrotor-with-keyboard/)
```
    rosservice call /enable_motors true # so the "motors" will respond to `geometry_msgs/Twist` commands to `/cmd_vel`
    rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

Run the modified "indoors" tutorial sim via:
* terminal #1:
```
    roslaunch hector_quadrotor_demo indoor_slam_gazebo_only.launch
```
* terminal #2:
```
    rosservice call /enable_motors true # so the "motors" will respond to `geometry_msgs/Twist` commands to `/cmd_vel`
    rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

(Note that an alternative to `teleop_twist_keyboard` is [lharikrishnan1993/hector_keyboard_teleop](https://github.com/lharikrishnan1993/hector_keyboard_teleop), as mentioned at the ROS wiki site ([link](http://wiki.ros.org/hector_quadrotor_teleop)).)


Copyright
=========

The original code base is Copyright (c) Institute of Flight Systems and Automatic Control, Technische Universität Darmstadt. See LICENSE.txt for more details. The original github project repository is available at: https://github.com/tu-darmstadt-ros-pkg/hector_quadrotor

Additions and modifications to the code are Copyright (c) University of Cincinnati. See LICENSE-2.txt for more details.


License
=======

LICENSE.txt is the license for the Technische Universität Darmstadt source code.

LICENSE-2.txt is the license for the modifications and additions made to this code base by the AS4SR Lab at the University of Cincinnati.

LICENSE.txt and LICENSE-2.txt are both BSD 3-clause licenses, and should be fully-compatible with each other.

This is free software released under the terms of the BSD 3-Clause License. There is no warranty; not even for merchantability or fitness for a particular purpose. Consult LICENSE.txt and LICENSE-2.txt for copying conditions.

When code is modified or re-distributed, the LICENSE.txt and LICENSE-2.txt files should accompany the code or any subset of it, however small. As an alternative, the LICENSE text can be copied within files, if so desired.


Contact
=======

If you have any questions regarding the contents of this repository, please email Catharine McGhan at <cat.mcghan@uc.edu>.

-EOF-
