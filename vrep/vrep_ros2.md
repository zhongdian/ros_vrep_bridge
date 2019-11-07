shell A:  
运行  
`roscore`

shell B:  
运行  
`vrep: cd /vrep`  
`./vrep.sh`

shell C:  
配置ros2环境：  
`. /opt/ros/dashing/setup.bash`  
启动ros_ros2_bridge:   
`ros2 run ros1_bridge dynamic_bridge`

rostopic list  
`ros2 run rqt_image_view rqt_image_view /image`