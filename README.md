[![Udacity - Robotics NanoDegree Program](https://s3-us-west-1.amazonaws.com/udacity-robotics/Extra+Images/RoboND_flag.png)](https://www.udacity.com/robotics)

# Where Am I?
## Project Description
### Munir Jojo-Verge

Welcome to the "Where Am I" localization project! In this project, you will learn to utilize ROS AMCL package to accurately localize a mobile robot inside a map in the Gazebo simulation environments.

Over the course of this lesson, you will learn several aspects of robotic software engineering with a focus on ROS:

Create a ROS package that launches a custom robot model in a custom Gazebo world

Utilize the ROS AMCL package and the Tele-Operation / Navigation Stack to localize the robot

Explore, add, and tune specific parameters corresponding to each package to achieve the best possible localization results

## Install

#### 1) Clone with Submodules 

```
$ cd ws
$ git clone --recurse-submodules https://github.com/munirjojoverge/RoboND_AMCL_ROS
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
#### 6) Launch "AMCL" ros package (Terminal 2)

```
$ roslaunch my_robot amcl.launch
```

#### 7) If you had a problem loading with the MAP
Go to 
```
$ cd src/my_robot/maps
```
double click on __map.pgm__. If you can't open it (error), then I left a map.xcf ready for you to open it with "gimp" (sudo apt-get install gimp). Select File -> extract. Save it as map.pgm and select "raw". This should have solved the problem. Try again by relaunching the amcl package (step 6) 

#### 8) If everything went fine, you should be able to see the robot on RViz souranded by particles+arrows. This is the Monte Carlo Localizaion algorithm (best known as ___"Particle Filter"___) giving you the best estimmate for the position and orientation of the robot. You can also move the robot either by clicking on __"2D Nav Goal"__ button on RViz (top bar, below the menu bar) or by running the Teleop Twist on a separate terminal (Terminal 3):
```
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

## Folter Structure
```
RoboND_AMCL_ROS/
├── ball_chaser
│   ├── launch
│   ├── src
│   └── srv
├── images
├── my_robot
│   ├── config
│   │   └── __MACOSX
│   ├── launch
│   ├── maps
│   ├── meshes
│   ├── model
│   │   ├── Building
│   │   └── HumanoidRobot
│   ├── rviz
│   ├── urdf
│   └── worlds
├── pgm_map_creator
│   ├── launch
│   ├── maps
│   ├── msgs
│   ├── src
│   └── world
└── teleop_twist_keyboard
```
## Results
Take a look at the images provided on __"images"__ folder
