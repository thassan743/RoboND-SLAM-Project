# RoboND-SLAM-Project

### This document assumes ROS and Gazebo are installed.
### `catkin_ws` is the name of the active ROS Workspace, if your workspace name is different, change the commands accordingly

If you do not have an active ROS workspace, you can create one by:
```sh
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/
$ catkin_make
```

Now that you have a workspace, clone or download this repo into the **src** directory of your workspace:
```sh
$ cd ~/catkin_ws/src
$ git clone https://github.com/thassan743/RoboND-SLAM-Project.git
```

Install dependencies:
```sh
$ sudo apt-get install ros-kinetic-rtabmap ros-kinetic-rtabmap-ros && sudo apt-get remove ros-kinetic-rtabmap ros-kinetic-rtabmap-ros
```

Install RTAB-Map:
```sh
$ cd ~ && git clone https://github.com/introlab/rtabmap.git rtabmap && cd rtabmap/build && cmake .. && make && sudo make install
```

Ensure `~/.gazebo` directory exists then download Gazebo model collisions for the project:
```sh
$ curl -L https://s3-us-west-1.amazonaws.com/udacity-robotics/Term+2+Resources/P3+Resources/models.tar.gz | tar zx -C ~/.gazebo/
```

Build the project:
```sh
$ cd ~/catkin_ws
$ catkin_make
```

Source the terminal
```sh
$ source ~/catkin_ws/devel/setup.bash
```

First launch gazebo with the desired world. Either the supplied `kitchen_dining` world:
```sh
$ roslaunch slam_project world.launch
```

or the custom world:
```sh
$ roslaunch slam_project my_world.launch
```

In a new terminal, launch the `teleop` node:
```sh
$ roslaunch slam_project teleop.launch
```
This will allow you to drive the robot around the world using the keyboard.

Before moving the robot, in a new terminal launch the `rtabmap_ros` node:
```sh
$ roslaunch slam_project mapping.launch
```

Finally, in a new terminal launch the `rviz` node:
```sh
$ roslaunch slam_project rviz.launch
```
