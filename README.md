
# Quick look


![physical simulation](/doc/ezgif-5-0ebe57dec0.gif)
![physical simulation2](/doc/ezgif-5-da58cfe1e0.gif)

A quick project of building a **dog bot** and **physical simulation environment** in **ROS**.
## Dogbot mechanics

![node joints test](/doc/ezgif-2-4d830865b7.gif)

The robot description file contains
 - **material**
 - **geometry**
 - **collision box**
 - **inertia and mass**
 - **joints/transfer**
 - **actuators/fake Hardware Interface**
 - **camera**
 ```
roslaunch dogbot dogbot_rvis.launch
 ```
![rivs displays robot TF](/doc/WechatIMG37.jpeg)
*rivs displays robot TF*<br/>

 ## physical simulation

    roslaunch dogbot dogbot_gazebo.launch word:=willowgarage_world.launch
  
launch gazebo for simulation 
![alt text](/doc/WechatIMG38.png)
  
## Camera raw image simulation
     rosrun rqt_image_view rqt_image_view
simulate camera data installed under dog head
![alt text](/doc/WechatIMG39.png)


## Joints_state controller
to open a node for joint control
```
roslaunch dogbot dogbot_controller.launch
```

to publish commands for the joint_state topic
```
rosrun rqt_gui rqt_gui
```
create a node to control joints of the dog 
![alt text](/doc/WechatIMG40.png)

## Architect
```mermaid
graph LR
R[rvis] --"auto-generate transfer(TF) using URDF"--> V{Dogbot}

Z[Gazebo_gui simulator]

X[Plugin/external controller] --  topic:joint_state --> B
H[rqt_gui] -- topic:joint_state -->B((Robot_controller)) --URDF-->F{Dogbot}
A[rqt_image_view] -- topic:camera/image_raw --> F
```
## Usage


> To install **ROS**, please check [ROS wiki](https://wiki.ros.org/ROS/Installation).



 1. clone the poject
 2. initialize catkin workspace
 3.  `catkin_make` to cmake in the project directory
 4. >if catkin_make can't locate you gazebo_ros config, try add prefix "PKG_CONFIG_PATH=$(rospack find gazebo_ros)/cmake cmake .." at the dogbot directory.
 5. run above commands
# dogbot_ros
