# Map My World
The goal of this project is to build 2D & 3D Map of the env using ROS pkg `rtabmap_ros pkg`  which is a ROS wrapper (API) for interacting with rtabmap to generate a `2D` occupancy grid and `3D` octomap from a provided simulated environment with best solution for (`SLAM`) to develop mobile robots .

**2D Map and 3D Map**

![2d map and 3d map](/images/RTAB.png)


**Occupancy_Grid_Mapping**

![Occupancy_Grid_3d](/images/Occupancy_Grid_Mapping.png)



#### This project is intended to be completed in the Udacity Workspace or on Jetson TX2 and might encounter performance issue on personal laptop or the VM.

Because RTAB-Map 's speed and memory management  for information analysis and the quality of the documentation. Being able to leverage RTAB-Map with our own robots will lead to a solid foundation for mapping and localization well.

# Project Setup
To begin, several ROS packages need to be installed as dependencies:

```
$ sudo apt-get update && sudo apt-get upgrade -y
$ sudo apt-get install ros-kinetic-rtabmap-ros
$ sudo apt-get install ros-kinetic-teleop-twist-keyboard
```

With the dependencies installed, download/clone the repository, navigate up to the root level directory, and execute:

```
$ catkin_make
$ source devel/setup.bash
$ roslaunch my_robot world.launch
```

To operate the robot via the keyboard, open a second terminal, navigate to the root level directory, and execute:

```
$ source devel/setup.bash
$ roslaunch my_robot teleop_twist.launch
```

You can then command the robot to move using the keys indicated by the teleop node.

Finally, to run SLAM, open a third terminal, navigate to the root level directory, and execute:

```
$ source devel/setup.bash
$ roslaunch my_robot Mapping.launch
```

As you move the robot around, RTAB-Map will build a map of the room. When you terminate the mapping window, the map will be saved as a database file in the launch folder. To view the map, execute: `$ rtabmap-databaseViewer rtabmap_gloable.db`

* Choose View -> Constraints View and Graph View
* To see 3D Map, Choose Edit -> View 3D Map.


You could also open the database I already generated in this project. The number of loop closures can be found in overview.png.


##### In order to get a loop closure in this project

* you have to drive your robot with low velocity while moving  in a straight line and a little bit when you spinnig (rotating).

* you increase the number of your features in your Env.

* beside tuning the rtabmap-pkg
