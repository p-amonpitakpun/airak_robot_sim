# airak_robot_sim

prerequisite
  - ros foxy
  - gazebo
  - gazebo_ros_pkgs


Clone the repository
```Shell
$ mkdir -p ~/ros2_ws/src
$ git clone https://github.com/p-amonpitakpub/airak_gazebo_ros_plugins.git
```

build the package with colcon
```Shell
$ cd ~/ros2_ws
$ colcon build --symlink-install 
```

first run this code to setup the model path
```Shell
$ export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:~/ros2_ws/src/airak_gazebo_ros_plugins/models
```

start gazebo with
```shell
$ cd ~/ros2_ws/src/airak_gazebo_ros_plugins
$ gazebo world/demo_ddbot.world
```

use tf for camera_link and for lidar_link
```Shell
$ ros2 run tf2_ros static_transform_publisher 0.03 0 0.25 -1.57 0 -1.57 base_link camera_link
$ ros2 run tf2_ros static_transform_publisher 0 0 0.16 0 0 0 base_link lidar_link
```

the ddbot can be driven with geometry_msgs/Twist /ddbot/cmd_vel

use Navigation 2 for reference
https://navigation.ros.org/
