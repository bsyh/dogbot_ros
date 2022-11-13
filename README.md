
# Quick look


![physical simulation](/doc/ezgif-5-0ebe57dec0.gif)
A quick project of building a **dog bot** and physical simulation environment in **ROS**.
## Dogbot mechanics

    roslaunch dogbot dogbot_rvis.launch
![rivs displays robot TF](/doc/WechatIMG37.jpeg)
*rivs displays robot TF*
The robot description file contains
 - **material**
 - **geometry**
 - **collision box**
 - **inertial and msss**
 - **joints/transfer**
 - **actuators/fake Hardware Interface**
 - **camera**
 ## physical simulation

    roslaunch dogbot dogbot_gazebo.launch word:=willowgarage_world.launcg
  
  launch gazebo for  simulation 
![alt text](/doc/WechatIMG38.png)
  
## Camera raw image simulation
     rosrun rqt_image_view rqt_image_view
![alt text](/doc/WechatIMG39.png)


## Joints_state controller
     rosrun rqt_gui rqt_gui
![alt text](/doc/WechatIMG40.png)

## Architect
```mermaid
graph LR
Z[Gazebo_gui simulator]
X[Plugin/external controller] --  topic:joint_state --> B
A[rgt_gui] -- topic:joint_state -->B((Robot_controller)) -->F{Dogbot}
A[rgt_image_view] -- topic:camera_raw --> F
```
## Usage


> To install **ROS**, please check [ROS wiki](https://wiki.ros.org/ROS/Installation).



 1. clone the poject
 2. initialize catkin workspace
 3.  `catkin_make` to cmake in the project directory
 4. >if catkin_make can't locate you gazebo_ros config, try add prefix "PKG_CONGIG_PATH=$(rospack find gazebo_ros)/cmake cmake .." at the dogbot directory.
 5. run above commands
