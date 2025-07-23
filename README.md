# fast-lio-converter

## Intended use 

This small toolset allows to integrate SLAM solution provided by [fast-lio](https://github.com/hku-mars/FAST_LIO.git) with [HDMapping](https://github.com/MapsHD/HDMapping).
This repository contains ROS  workspace that :
  - submodule to tested revision of fast-lio
  - a converter that listens to topics advertised from odometry node and save data in format compatible with HDMapping.

## Building

Clone the repo
```shell
mkdir -p /test_ws/src
cd /test_ws/src
git clone https://github.com/marcinmatecki/fast-lio-to-hdmapping.git --recursive
cd ..
catkin_make
```

## Usage - data SLAM:

Prepare recorded bag with estimated odometry:

In first terminal record bag:
```shell
rosbag record /cloud_registered /Odometry
```

and start odometry:
```shell 
cd /test_ws/
source ./install/setup.sh # adjust to used shell
For launch, check https://github.com/hku-mars/FAST_LIO/
rosbag play your bag file
```

## Usage - conversion:

```shell
cd /test_ws/
source ./install/setup.sh # adjust to used shell
rosrun fast-lio-to-hdmapping listener <recorded_bag> <output_dir>
```