# Experimental Laboratory for Robotics, Assignment 2
Assignment 2 of Experimental Laboratory course, Robotics Engineering faculty UNIGE


## INDEX 🔖

* [Introduction](#introduction)
  * [Simulator](#simulator)
* [Install and Running](#install-and-running)




* [Video](#video)
* [Autors](#autors)

<div id='introduction'/>

## INTRODUCTION
Given a complex environment with multiple obstacles in Gazebo, four markers with different IDs are placed inside it (look [https://github.com/CarmineD8/aruco_ros](https://github.com/CarmineD8/aruco_ros). In order to capture the images that for the scanning of the marker for ID's detection, the following waypoints are given:
 
* WP 1: x = -7.0, y = 1.5 (Marker 15)
* WP 2: x = -3.0, y = -8.0 (Marker 12)
* WP 3: x = 6.0, y = 2.0 (Marker 11)
* WP 4: x = 7.0, y = -5.0 (Marker 13)
  
The goal is to develop a ROS2 package that lets a mobile robot endowed with a camera and a laser scanner move the robot to the waypoint corresponding to the lowest ID.
The requirement is to use PlanSys2 to plan the actions of the robot

<div id='simulator'/>

### Simulator
For this assignment, it was used Gazebo and Rviz within ROS. Gazebo served as the 3D simulation environment to test and refine the robot's movements, while Rviz was used for detailed 3D visualization, with also the information of the robot's sensor.

<div id='install-and-running'/>

## INSTALL AND RUNNING 📖
First of all, you need to go into your ros2 workspace (folder src for packages is suggested)
```bash
cd /root/ros2_ws/src
```
Then, clone the repository to your machine (or download)
```bash
git clone https://github.com/NicolasBravi01/ExpLab_Unige.git
```
Now, you can can back to the ros2_ws path and build
```bash
cd ..
colcon build
```
Now it is possible to run
```bash
ros2 launch robot_urdf gazebo2.launch
```
In order to run the controller with the PDDL problem, open another terminal and run it
```bash
ros2 run plansys2_patrol_navigation_example patrolling_controller_node
```


## Logic
**Patrolling_controller_node**
This node was created to initialyze the PlanSys2 framework in order to correctly navigate in the enviroment and patrol the desired waypoints. Here's a list of everything the node does:
- Basic knowledge initialization (instances, predicates and connections).
- Goal definition: depending on the state the node is in, the controller is able to set a specific goal.

**State Machine**:
  - **STARTING**: At the beginning of the task, the problem with the goal is defined. At this state, we do not know yet which is the marker with the lowest ID, so the goal is to scan all the four markers. As specified above, a marker can be scanned only if the mobile robot is at the relative point.
  - **PATROL_FINISHED**: At this state, the controller defines the new robot's goal based on received marker IDs. The new goal is to reach the waypoint that corresponds to the marker with the lowest ID.
  - **GO_BACK**: Handles returning to the waypoint of the marker with the lowest ID and cleans up predicates after completion.



<div id='video'/>

## Video 👨‍💻



<div id='autors'/>

## AUTORI 👨‍💻

* [Nicolas Bravi](https://github.com/NicolasBravi01)
* [Ilaria Colomba](https://github.com/ilacolo)
* [Enrico Piacenza](https://github.com/EnricoPiacenza)

