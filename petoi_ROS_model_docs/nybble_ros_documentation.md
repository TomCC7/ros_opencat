# [Petoi](https://www.petoi.com/ "Petoi")

### Nybble ROS Documentation
This documentation is designed to configure Nybble in the ROS Simulation Environment.

### Pre-requisites 🤔
Your system must have:
- [Ubuntu (Version 20.04 recommended)](https://releases.ubuntu.com/focal/)
- [ROS Noetic Ninjemys](http://wiki.ros.org/noetic/Installation/Ubuntu)

### Tutorial 😃
- #### [ROS Installation Steps](https://www.youtube.com/watch?v=ZA7u2XPmnlo)

   Open the terminal and follow the below commands to install [ROS Noetic Ninjemys](http://wiki.ros.org/noetic/Installation/Ubuntu)


```bash
    sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
 ```
 ```bash
    sudo apt install curl # if you haven't already installed curl
 ```
```bash
 curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
```bash
sudo apt update
```
```bash
sudo apt install ros-noetic-desktop-full ros-noetic-effort-controllers
```
- #### Create Catkin Workspace for the ROS Packages


Follow the below mentioned commands to create a Catkin Workspace for creating and modifying the ROS packages.

```bash
mkdir -p ~/catkin_ws/src
```
```bash
cd ~/catkin_ws/
```
```bash
catkin_make
```
Open the ```~/.bashrc file``` via below command

```bash
gedit ~/.bashrc
```
.bashrc file will appear

<img src="bittle_ros_images/bashrc.png" height ="100%" width="100%" alt text="bashrc file">

Paste the below commands in ```.bashrc file``` (screenshot has been attached for reference)

```bash
source /opt/ros/noetic/setup.bash
source ~/catkin_ws/devel/setup.bash
```

Clone the folder [nybble_description package](https://github.com/PetoiCamp/ros_opencat/tree/ros1/petoi_ros_docs/nybble_ros) and paste it inside the ```src``` folder of the catkin workspace.

- #### Launch Gazebo simulation

Start the ROS master via
```bash
roscore
```

<img src="bittle_ros_images/roscore.png">

Open a new terminal window or simply press ```Ctrl+Alt+T```and follow below mentioned commands to spawn your Nybble in an empty Gazebo Simulation Environment.

```bash
roscd nybble_description
```
``` bash
ls
```
```bash
cd launch
```
```bash
ls
```
```bash
roslaunch nybble_description gazebo.launch
```

<img src="nybble_ros_images/final.png">
<img src="nybble_ros_images/nybble_simulation.png">

- #### Steps to launch your Nybble in the Gazebo world Simulation Environment

<br>

$${\color{red}CAUTION: \space \color{orange}Before \space launching \space your \space Nybble \space in \space the \space Gazebo \space World \space Simulation \space Environment \space you \space are \space first \space required \space to \space kill \space the \space existing }$$

$${\color{orange}processes. \space Just \space by \space simply \space pressing \space Ctrl+C \space it \space will \space going \space to \space kill \space the \space existing \space node}$$

<br>

   Once the existing nodes are killed follow the below commands to launch your nybble.

  ```bash
  roslaunch nybble_gazebo nybble_world.launch
  ```

<img src="nybble_ros_images/nybble_world.png">

For launching controller for the joints of the Nybble.

```bash
  roslaunch nybble_description controller.launch
  ```
Press the play button ▶️ in the Gazebo to load all the joint controllers.

<img src="nybble_ros_images/controller_1.png">
<img src="nybble_ros_images/controller_2.png">

For controlling the joint position of the neck you are required to install [joystick ros driver](http://wiki.ros.org/joy/Tutorials/ConfiguringALinuxJoystick) <br>
[Video reference for installation of joystick driver](https://www.youtube.com/watch?v=4cSRdS83PX4&t=204s)

Open a new terminal window and launch your joystick package
```bash
  roslaunch nybble_joystick nybble_joystick.launch
  ```

<img src="nybble_ros_images/joystick_2.png">

Open another terminal and run your joystick node
```bash
  rosrun nybble_joystick nybble_joystick.py
  ```
Press `Enter`

<img src="nybble_ros_images/joystick_1.png">
<img src="nybble_ros_images/joystick.jpeg">

Move this joystick button as mentioned in the above image to control the neck movement.

To visualize your Nybble in Rviz(Robot Visualization)

```bash
   roslaunch nybble_description display.launch
  ```

<img src="nybble_ros_images/rviz.png">

You can move the joints by sliding the corresponding joints bar using `joint_state_publisher_gui` node.

### Yayy!! You are done😃


