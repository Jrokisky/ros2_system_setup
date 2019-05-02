# Setting up the Realsense Ros2 Node

## Instructions

### Create a Ros2 workspace
  * run: `mkdir -p ~/ros2_realsense_node/src`
  * run: `cd ~/ros2_realsense_node/src`
  
### Installing Dependencies
  * Clone the cv_bridge node [repository][2] into the `src` directory
    * run: `cd vision_opencv`
    * run: `git checkout ros2`
  * Clone the image_transport node [repository][4] into the `src` directory
    * run: `cd image_common`
    * run: `git checkout ros2`
  
### Installing Realsense Ros2 Node
  * Clone the intel ros2 realsense node [repository][1] into the `src` directory
  * We will not be using the installation instructions provided in the readme, instead build as follows:
    1. run: `source ~/ros2_ws/install/setup.bash` to source ROS2 (if you installed ROS2 in a different workspace than `ros_ws`, use the source script from there)
    2. run: `cd ~/ros2_realsense_node` 
    3. run: `MAKE_FLAGS="-j4" colcon build --symlink-install` to build the node & its dependencies
    4. run: `wget https://raw.githubusercontent.com/Jrokisky/ros2_system_setup/master/settings.yaml` to get the node settings file

### Testing the Realsense Ros2 Node
  * run: `source ~/ros2_realsense_node/install/local_setup.bash` to source our node
  * run: `sudo jetson_clocks` to increase performance on the Jetson
  * run: `cd ~/ros2_realsense_node`
  * run: `ros2 run realsense_ros2_camera realsense_ros2_camera __params:=settings.yaml` to start the node
  * Open another terminal and run: `source ~/ros2_ws/install/setup.bash` followed by `rviz2` to launch a visualization tool
    * If you run into any errors while launching, try to relaunch.
    * When Rviz opens select: `Add` > `By Topic` > `/camera/depth/image_rect_raw/Image` > `OK`
    * You should now see the greyscale depth image. If it freezes, remove the topic, and re-add it
  * On the remote machine:
    * run: `source ~/ros2_ws/install/setup.bash`
    * run: `rivz2` and follow the steps above to add the depth topic visualizer

[1]:https://github.com/intel/ros2_intel_realsense.git
[2]:https://github.com/ros-perception/vision_opencv
[3]:https://github.com/ros-perception/vision_opencv/tree/ros2/cv_bridge
[4]:https://github.com/ros-perception/image_common/tree/ros2
