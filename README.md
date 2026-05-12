## 1 rslidar_sdk

**rslidar_sdk** is the Software Development Kit of the RoboSense Lidar based on Ubuntu. It contains:

+ The lidar driver core [rs_driver](https://github.com/RoboSense-LiDAR/rs_driver),
+ The ROS support,
+ The ROS2 support,

### Point Type Supported

- XYZI - x, y, z, intensity
- XYZIRT - x, y, z, intensity, ring, timestamp

## 2 Dependencies

### 2.1 ROS

To run rslidar_sdk in the ROS environment, please install below libraries.

+ Ubuntu 16.04 - ROS Kinetic desktop
+ Ubuntu 18.04 - ROS Melodic desktop
+ Ubuntu 20.04 - ROS Noetic desktop

For installation, please refer to http://wiki.ros.org.

**It's highly recommanded to install ros-distro-desktop-full**. If you do so, the corresponding libraries, such as PCL, will be installed at the same time.

This brings a lot of convenience, since you don't have to handle version conflict.

### 2.2 ROS2

To use rslidar_sdk in the ROS2 environment, please install below libraries.

+ Ubuntu 16.04 - Not supported
+ Ubuntu 18.04 - ROS2 Eloquent desktop
+ Ubuntu 20.04 - ROS2 Galactic desktop
+ Ubuntu 22.04 - ROS2 Humble desktop
+ Ubuntu 24.04 - ROS2 Jazzy desktop

For installation, please refer to https://index.ros.org/doc/ros2/Installation/Eloquent/Linux-Install-Debians/

**Please do not install ROS and ROS2 on the same computer, to avoid possible conflict and manually install some libraries, such as Yaml.**

### 2.3 Yaml (Essential)

version: >= v0.5.2

*If ros-distro-desktop-full is installed, this step can be skipped*

Installation:

```sh
sudo apt-get update
sudo apt-get install -y libyaml-cpp-dev
```

### 2.4 libpcap (Essential)

version: >= v1.7.4

Installation:

```sh
sudo apt-get install -y  libpcap-dev
```

## 3 Compile & Run

### 3.1 Compile with ROS catkin tools

(1) Create a new workspace folder, and create a *src* folder in it. Then put the rslidar_sdk project into the *src* folder.

(2) Go back to the root of workspace, run the following commands to compile and run. (if using zsh, replace the 2nd command with *source devel/setup.zsh*).

```sh
catkin_make
source devel/setup.bash
roslaunch rslidar_sdk start.launch
```

### 3.2 Compile with ROS2 colcon

(1) Create a new workspace folder, and create a *src* folder in it. Then put the rslidar_sdk project in the *src* folder.

(2) Download the driver kernel as zip from this [link](https://github.com/RoboSense-LiDAR/rs_driver). Unzip and paste the content in *rslidar_sdk/src/rs_driver* folder.

(3) Download the packet definition project in ROS2 through [link](https://github.com/RoboSense-LiDAR/rslidar_msg), then put the project rslidar_msg in the *src* folder you just created.

(4) Go back to the root of workspace, run the following commands to compile and run. (if using zsh, replace the 2nd command with *source install/setup.zsh*).

(5) The LiDAR's default IP address is 192.168.1.200. It is important to configure the Ethernet connection on the same subnet (for example: 192.168.1.102).

```sh
colcon build
source install/setup.bash
ros2 launch rslidar_sdk start.py
```
