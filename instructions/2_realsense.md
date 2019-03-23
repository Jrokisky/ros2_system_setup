## Setting up the Intel Realsense






### Instructions
1. Getting the docs
    * Navigate to the Intel Realsense sdk [repo][1]
    * Open: */docs*
    * Open: *installation_jetson.md*
    * Read the contents

2. Building CMake
    * We may need to build CMake as the librealsense library notes:

    > Cmake Note: certain librealsense CMAKE flags (e.g. CUDA) require version 3.8+ which is currently not made available via apt manager for Ubuntu LTS.

    * To check your CMake version: `cmake --version`
    * If it is not 3.8, download the [CMake Source][3] and follow the installation instructions [here][4]

3. Building the library
    * As the documentation states, we're going to follow the standard build [instructions][5] with some modifications.
    * Modification #1: in **Prepare Linux Backend and the Dev. Environment** we want to run `./scripts/install_glfw3.sh` instead of `sudo apt-get install libglfw3-dev`






[1]:https://github.com/IntelRealSense/librealsense
[2]:https://github.com/IntelRealSense/librealsense/blob/master/doc/installation.md
[3]:https://cmake.org/download/
[4]:https://cmake.org/install/
[5]:https://github.com/IntelRealSense/librealsense/blob/master/doc/installation.md
