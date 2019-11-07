# Ubuntu 18.04下ROS1 melodic+catkin安装
根据[官网](http://wiki.ros.org/melodic/Installation)教程来即可。

# vrep安装

## 下载vrep

[登录官网](http://www.v-rep.eu/downloads.html),找到对应的版本下载安装即可

## 运行vrep

下载完解压后，在终端运行如下命令即可启动： 
`cd vrep`  
`. /vrep.sh`  

# 配置RosInterface

## 创建一个单独的工作空间  
将以下4个功能包下载的src文件夹中：
```
git clone https://github.com/CoppeliaRobotics/ros_bubble_rob2  
git clone https://github.com/CoppeliaRobotics/vrep_skeleton_msg_and_srv.git  
git clone https://github.com/CoppeliaRobotics/vrep_plugin_skeleton.git  
git clone --recursive https://github.com/CoppeliaRobotics/v_repExtRosInterface.git  
```
或者  
`git clone https://github.com/zhongdian/ROS2/tree/master/vrep/vrep_ros_interface`  

## 返回到工作空间 
在该目录下打开终端：  
配置ros1环境：  
`. /opt/ros/melodic/setup.bash`   
导入vrep路径：  
`export VREP_ROOT=~/vrep`  
进行编译：  
`catkin_make`  
将工作空间下/dev/lib文件夹中的libv_repExtRosSkeleton.so文件复制到vrep的根目录中。即可完成配置。


# 问题报错与解决

1. 链接libv_repExtRosSkeleton.so动态库时显示“/usr/bin/ld: cannot find -lroslib....collect2: error: ld returned 1 exit status"

* 这是因为下的包里默认支持到kinetic，需打开vrep_plugin_skeleton文件夹里的CMakeLists.txt文件，在里面添加一句link_directories("/opt/ros/melodic/lib")即可解决问题

2. ”python: can't open file '/home/pcwl/vrep_ros_interface/src/external/v_repStubsGen/generate.py': [Errno 2] No such file or directory"

* 这是v_repStubsGen文件夹的路径问题，根据报错将文件放入正确的路径即可