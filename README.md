[![Udacity - Robotics NanoDegree Program](https://s3-us-west-1.amazonaws.com/udacity-robotics/Extra+Images/RoboND_flag.png)](https://www.udacity.com/robotics)

# Map My World: GraphSLAM using Real Time Apperance Base Map (RTAB_MAP) algorithm in ROS
## Project Description
### Munir Jojo-Verge

#### Overview
In this project we will create a 2D occupancy grid and 3D octomap from a simulated environment using our own robot with the RTAB-Map package.

RTAB-Map (Real-Time Appearance-Based Mapping) is a popular solution for SLAM to develop robots that can map environments in 3D. RTAB-Map has good speed and memory management, and it provides custom developed tools for information analysis. Most importantly, the quality of the documentation on ROS Wiki (http://wiki.ros.org/rtabmap_ros) is very high. Being able to leverage RTAB-Map with your own robots will lead to a solid foundation for mapping and localization well beyond this Nanodegree program.

For this project we will be using the rtabmap_ros package, which is a ROS wrapper (API) for interacting with RTAB-Map. Keep this in mind when looking at the relative documentation.

#### Project Instructions
The project flow will be as follows:

We will develop our own package to interface with the rtabmap_ros package.

We will build upon our localization project (https://github.com/munirjojoverge/RoboND_AMCL_ROS) to make the necessary changes to interface the robot with RTAB-Map. An example of this is the addition of an RGB-D camera.

We will ensure that all files are in the appropriate places, all links are properly connected, naming is properly setup and topics are correctly mapped. Furthermore you will need to generate the appropriate launch files to launch the robot and map its surrounding environment.

When our robot is launched we will teleop around the room to generate a proper map of the environment.

## Install

#### 1) Clone with Submodules (IMPOTANT)

```
$ cd ws
$ git clone --recurse-submodules https://github.com/munirjojoverge/RoboND_RTAB_MAP_ROS
```
#### 2) Rename the repo folder, if necessary, to "src"

#### 3) Source ros & build the packages

```
$ cd ws
$ source /opt/ros/kinetic/setup.bash
$ source catkin_make
$ source /opt/ros/kinetic/setup.bash
```
#### 4) If you had a problem, resolve all the dependencies
```
$ rosdep install --from-paths src --ignore-src -r -y
```
go to step 3 and try again.

## Run
#### 5) Launch "my_robot" package (Terminal 1)

```
$ roslaunch my_robot world.launch
```
#### 6) Launch "RTAB_MAP" ros package (Terminal 2)

```
$ roslaunch my_robot mapping.launch
```

#### 7) Drive the robot around the environment to map it: Launch the teleop node (Terminal 3)

```
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

Navigate your robot in the simulation to create map for the environment! When you are all set, terminal the node and you could find your map db file in the place you specified in the launch file. If you did not modify the argument, it will be located in the /root/.ros/ folder.

#### Best Practices
You could start by lower velocity. Our goal is to create a great map with the least amount of passes as possible. Getting 3 loop closures will be sufficient for mapping the entire environment. You can maximize your loop closures by going over similar paths two or three times. This allows for the maximization of feature detection, facilitating faster loop closures! When you are done mapping, be sure to copy or move your database before moving on to map a new environment. Remember, relaunching the mapping node deletes any database in place on launch start up!

## Folter Structure
```
RoboND_RTAB_MAP_ROS/
├── ball_chaser
│   ├── CMakeLists.txt
│   ├── launch
│   ├── package.xml
│   ├── src
│   └── srv
├── CMakeLists.txt -> /opt/ros/kinetic/share/catkin/cmake/toplevel.cmake
├── images
│   ├── rtabmap_viewer_kitchen_dinning.png
│   ├── rtabmap_viewer_museum.png
│   └── rtabmap_viewer_my_original_world.png
├── LICENSE
├── my_robot
│   ├── CMakeLists.txt
│   ├── config
│   ├── launch
│   ├── maps
│   ├── meshes
│   ├── model
│   ├── package.xml
│   ├── rviz
│   ├── urdf
│   └── worlds
├── pgm_map_creator
│   ├── CMakeLists.txt
│   ├── launch
│   ├── LICENSE
│   ├── maps
│   ├── msgs
│   ├── package.xml
│   ├── README.md
│   ├── src
│   └── world
├── README.md
├── RvizConfig.rviz
└── teleop_twist_keyboard
    ├── CHANGELOG.rst
    ├── CMakeLists.txt
    ├── package.xml
    ├── README.md
    └── teleop_twist_keyboard.py
```
## Results
Take a look at the images provided on __"images"__ folder.
I mapped 3 places and here are the pros and cons of each one:

1) My personal world (munir_simple0.world): The symetry of the environment and the lack of strong features made the "loop closures" impossible to achieve. Strangely enough the mapping is creat even without closures. Due to the lack of loop closures, I had to move on and try a different environment.
2) Kitchen & Dinning (munir_simple2.world). Turned out that all the objects have not collision and not laser reflectivity and NO map was produced even though, and since I drove it for quite a while, I encountered 68 loop closures.
3) Museum (munir_simple.world). This envrinment was reach and perfect for mapping, but just a little too large for this experiement. The results were great in the center area were we can zoom in and see perfect mapping of the walls an other objects. The problem is that outside this ceter area, the mapping is poor since it requires a lot of driving/exploring around.
# rtab_map dbs located here: 
https://drive.google.com/open?id=1XoiL_5oBGUUp3f_MO7B0ogWiCeQhGWem
