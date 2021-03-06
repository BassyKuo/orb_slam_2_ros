[![OS Version](https://img.shields.io/badge/OS-ubuntu%2016.04-blue.svg)](https://shields.io/) [![ROS Distro](https://img.shields.io/badge/ROS-kinetic-blue.svg)](https://shields.io/) [![Eigen3](https://img.shields.io/badge/Eigen3-3.3.7-blue.svg)](http://eigen.tuxfamily.org) [![Mono RViz](https://img.shields.io/badge/Mono%20RViz-OK-green.svg)](https://shields.io/) [![Stereo RViz](https://img.shields.io/badge/Stereo%20RViz-untested-lightgrey.svg)](https://shields.io/) [![RGBD RViz](https://img.shields.io/badge/RGBD%20RViz-untested-lightgrey.svg)](https://shields.io/)

# ORB-SLAM2
**ORB-SLAM2 Authors:** [Raul Mur-Artal](http://webdiis.unizar.es/~raulmur/), [Juan D. Tardos](http://webdiis.unizar.es/~jdtardos/), [J. M. M. Montiel](http://webdiis.unizar.es/~josemari/) and [Dorian Galvez-Lopez](http://doriangalvez.com/) ([DBoW2](https://github.com/dorian3d/DBoW2)).
The original implementation can be found [here](https://github.com/raulmur/ORB_SLAM2.git).

# ORB-SLAM2 ROS node
This is the ROS implementation of the ORB-SLAM2 real-time SLAM library for **Monocular**, **Stereo** and **RGB-D** cameras that computes the camera trajectory and a sparse 3D reconstruction (in the stereo and RGB-D case with true scale). It is able to detect loops and relocalize the camera in real time. This implementation removes the Pangolin dependency, and the original viewer. All data I/O is handled via ROS topics. For vizualization you can use RViz. This repository is maintained by [Lennart Haller](http://lennarthaller.de) on behalf of [appliedAI](http://appliedai.de).

##### In this fork, you can run the following code to see the vizualization:
    roslaunch orb_slam2_ros orb_slam2_airsim_mono.launch
##### or use your camera source and setting:
    roslaunch orb_slam2_ros orb_slam2_airsim_mono.launch CAMERA_SOURCE:=<camera_source_rostopic> SETTING_FILE:=<setting_file_path> 
##### You can change the [camera topic](./ros/launch/orb_slam2_airsim_mono.launch#L2L3) and [rviz image source](./Data/rviz.rviz#L150) to your own case.

## Features
#### [this fork add]
- [x] support PointCloud Visualization with RViz. (Default config: `Data/rviz.rviz`)
- [x] support [AirSim ROS node](https://github.com/Mayankm96/airsim_ros_client) connection. (Need to install [AirSim](https://microsoft.github.io/AirSim/docs/build_linux/) first and download at least one [environment](https://github.com/Microsoft/AirSim/releases) as your simulation environment.)

##### ▸ related file locations:
```
├── Data
│   └── rviz.rviz                           <--- RViz settings
├── orb_slam2
│   └── config
│       └── Airsim_Mono.yaml                <--- ORB_SLAM2 settings for AirSim scene (resolution: 640x480)
└── ros
    └── launch
        └── orb_slam2_airsim_mono.launch    <--- launch file for ORB_SLAM2 with AirSim connection & RViz visualization 
```

###### (Please change the [camera topic](./ros/launch/orb_slam2_airsim_mono.launch#L2L3) and [rviz image source](./Data/rviz.rviz#L150) if you use different camera source.)

![demo](./Data/vis_demo.png)


#### [origin]
- Full ROS compatibility
- Supports a lot of cameras out of the box, such as the Intel RealSense family. See the run section for a list
- Data I/O via ROS topics
- Parameters can be set with the rqt_reconfigure gui during runtime
- Very quick startup through considerably sped up vocab file loading


### Related Publications:
[Monocular] Raúl Mur-Artal, J. M. M. Montiel and Juan D. Tardós. **ORB-SLAM: A Versatile and Accurate Monocular SLAM System**. *IEEE Transactions on Robotics,* vol. 31, no. 5, pp. 1147-1163, 2015. (**2015 IEEE Transactions on Robotics Best Paper Award**). **[PDF](http://webdiis.unizar.es/~raulmur/MurMontielTardosTRO15.pdf)**.

[Stereo and RGB-D] Raúl Mur-Artal and Juan D. Tardós. **ORB-SLAM2: an Open-Source SLAM System for Monocular, Stereo and RGB-D Cameras**. *IEEE Transactions on Robotics,* vol. 33, no. 5, pp. 1255-1262, 2017. **[PDF](https://128.84.21.199/pdf/1610.06475.pdf)**.

[DBoW2 Place Recognizer] Dorian Gálvez-López and Juan D. Tardós. **Bags of Binary Words for Fast Place Recognition in Image Sequences**. *IEEE Transactions on Robotics,* vol. 28, no. 5, pp.  1188-1197, 2012. **[PDF](http://doriangalvez.com/php/dl.php?dlp=GalvezTRO12.pdf)**

# 1. License
ORB-SLAM2 is released under a [GPLv3 license](https://github.com/aaide/ORB_SLAM2_ROS/blob/master/License-gpl.txt). For a list of all code/library dependencies (and associated licenses), please see [Dependencies.md](https://github.com/aaide/ORB_SLAM2_ROS/blob/master/Dependencies.md).

For a closed-source version of ORB-SLAM2 for commercial purposes, please contact the authors: orbslam (at) unizar (dot) es.

If you use ORB-SLAM2 (Monocular) in an academic work, please cite:

    @article{murTRO2015,
      title={{ORB-SLAM}: a Versatile and Accurate Monocular {SLAM} System},
      author={Mur-Artal, Ra\'ul, Montiel, J. M. M. and Tard\'os, Juan D.},
      journal={IEEE Transactions on Robotics},
      volume={31},
      number={5},
      pages={1147--1163},
      doi = {10.1109/TRO.2015.2463671},
      year={2015}
     }

if you use ORB-SLAM2 (Stereo or RGB-D) in an academic work, please cite:

    @article{murORB2,
      title={{ORB-SLAM2}: an Open-Source {SLAM} System for Monocular, Stereo and {RGB-D} Cameras},
      author={Mur-Artal, Ra\'ul and Tard\'os, Juan D.},
      journal={IEEE Transactions on Robotics},
      volume={33},
      number={5},
      pages={1255--1262},
      doi = {10.1109/TRO.2017.2705103},
      year={2017}
     }

# 2. Building orb_slam2_ros
We have tested the library in **Ubuntu 16.04** with **ROS Kinetic** and **Ubuntu 18.04** with **ROS Melodic**. A powerful computer (e.g. i7) will ensure real-time performance and provide more stable and accurate results.
A C++11 compiler is needed.

## Getting the code
Clone the repository into your catkin workspace:
```
cd ${catkin_workspace}/src
git clone https://github.com/BassyKuo/orb_slam_2_ros.git
```

## ROS
This ROS node requires catkin_make_isolated or catkin build to build. This package depends on a number of other ROS packages which ship with the default installation of ROS.
If they are not installed use [rosdep](http://wiki.ros.org/rosdep) to install them. In your catkin folder run
```
sudo rosdep init
rosdep update
rosdep install --from-paths src --ignore-src -r -y
```
to install all dependencies for all packages. If you already initialized rosdep you get a warning which you can ignore.

## Eigen3
Required by g2o. Download and install instructions can be found [here](http://eigen.tuxfamily.org).
Otherwise Eigen can be installed as a binary with:
```
sudo apt install libeigen3-dev
```

**Required at least Eigen 3.1.0**. (Using Eigen 3.3.7 is OK in Ubuntu 16.04)

## Building
Go back to your catkin folder, and build the node:
```
cd ${catkin_workspace}
catkin build
```

# 3. Configuration
## Config file
To run the algorithm expects both a vocabulary file (see the paper) and a **config file with the camera- and some hyper parameters**. The vocab file ships with this repository, together with config files for the Intel RealSense r200 camera. If you want to use any other camera you need to adjust the file (you can use one of the provided ones as a template). They are at orb_slam2/config.

## ROS parameters and topics
### Parameters
There are three types of parameters right now: static- and dynamic ros parameters and camera settings from the config file.
The static parameters are send to the ROS parameter server at startup and are not supposed to change. They are set in the launch files which are located at ros/launch. The parameters are:

- **publish_pointcloud**: Bool. If the pointcloud containing all key points (the map) should be published.
- **publish_pose**: Bool. If a PoseStamped message should be published. Even if this is false the tf will still be published.
- **pointcloud_frame_id**: String. The Frame id of the Pointcloud/map.
- **camera_frame_id**: String. The Frame id of the camera position.

Dynamic parameters can be changed at runtime. Either by updating them directly via the command line or by using [rqt_reconfigure](http://wiki.ros.org/rqt_reconfigure) which is the recommended way.
The parameters are:

- **localize_only**: Bool. Toggle from/to only localization. The SLAM will then no longer add no new points to the map.
- **reset_map**: Bool. Set to true to erase the map and start new. After reset the parameter will automatically update back to false.
- **min_num_kf_in_map**: Int. Number of key frames a map has to have to not get reset after tracking is lost.
- **min_observations_for_ros_map**: Int. Number of minimal observations a key point must have to be published in the point cloud. This doesn't influence the behavior of the SLAM itself at all.

Finally, the intrinsic camera calibration parameters along with some hyperparameters can be found in the specific yaml files in orb_slam2/config.

### Published topics
The following topics are being published and subscribed to by the nodes:
- All nodes publish (given the settings) a **PointCloud2** containing all key points of the map.
- Also all nodes publish (given the settings) a **PoseStamped** with the current pose of the camera.
- Live **image** from the camera containing the currently found key points and a status text.
- A **tf** from the pointcloud frame id to the camera frame id (the position).

### Subscribed topics
- The mono node subscribes to **/camera/image_raw** for the input image.

- The RGBD node subscribes to **/camera/rgb/image_raw** for the RGB image and
- **/camera/depth_registered/image_raw** for the depth information.

- The stereo node subscribes to **image_left/image_color_rect** and
- **image_right/image_color_rect** for corresponding images.

# 4. Run
After sourcing your setup bash using
```
source devel/setup.bash
```
## Suported cameras
| Camera               | Mono                                                           | Stereo                                                           | RGBD                                                       |
|----------------------|----------------------------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------|
| Intel RealSense r200 | ``` roslaunch orb_slam2_ros orb_slam2_r200_mono.launch ```     | ``` roslaunch orb_slam2_ros orb_slam2_r200_stereo.launch ```     | ``` roslaunch orb_slam2_ros orb_slam2_r200_rgbd.launch ``` |
| Intel RealSense d435 | ``` roslaunch orb_slam2_ros orb_slam2_d435_mono.launch ```     | -                                                                | ``` roslaunch orb_slam2_ros orb_slam2_d435_rgbd.launch ``` |
| Mynteye S            | ```roslaunch orb_slam2_ros orb_slam2_mynteye_s_mono.launch ``` | ```roslaunch orb_slam2_ros orb_slam2_mynteye_s_stereo.launch ``` | -                                                          |                     |                                                            |                                                              |                                                            |

Use the command from the corresponding cell for your camera to launch orb_slam2_ros with the right parameters for your setup.

# 5. FAQ
Here are some answers to frequently asked questions.
### Using a new / different camera
You can use this SLAM with almost any mono, stereo or RGBD cam you want.
There are two files which need to be adjusted for a new camera:
1) **The yaml config file** at orb_slam2/config for the camera intrinsics and some configurations. [Here](https://docs.opencv.org/3.1.0/dc/dbb/tutorial_py_calibration.html) you can read about what the calibration parameters mean. Use [this](http://wiki.ros.org/camera_calibration) ros node to obtain them for your camera. If you use a stereo or RGBD cam in addition to the calibration and resolution you need to adjust the other parameters such as Camera.bf, ThDepth and DepthMapFactor.
2) **The ros launch file** which is at ros/launch needs to have the correct topics to subscribe to from the new camera.

### Problem running the realsense node
The node for the RealSense fails to launch when running
```
roslaunch realsense2_camera rs_rgbd.launch
```
to get the depth stream.
**Solution:**
install the rgbd-launch package with the command (make sure to adjust the ROS distro if needed):
```
sudo apt install ros-kinetic-rgbd-launch
```
