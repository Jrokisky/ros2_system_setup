# Setting up ROS2

## Background Information
We will be building ROS2 from source using the ROS2 installation on Linux instructions.

## Instructions
  * Follow the instructions for Ubuntu 18.04 [here][1]
  * If you run into the error: `Protocol "https" not supported or disabled in libcurl`, it may been an issue with CMake not using OpenSSL as seen [here][2].

## Testing

### Testing Locally
  * Run the examples [here][3]
  
### Testing Remotely
  * Run the examples above, but run the listener on the remote machine
    * You need to be on a network with udp multicast for this to work


[1]:https://index.ros.org/doc/ros2/Installation/Linux-Development-Setup/
[2]:https://github.com/ros2/ros2/issues/470#issuecomment-371141641
[3]:https://index.ros.org/doc/ros2/Installation/Linux-Development-Setup/#try-some-examples
