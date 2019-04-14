## Setting up the Intel Realsense

### Instructions
1. Getting the Installation docs
    * Navigate to the Intel Realsense sdk [repo][1]
    * Open: */docs*
    * Notice that there is a Jetson specific installation: *installation_jetson.md*. As of March 23 2019, we do not want to follow the instructions here, as they are out of date.
    * Instead, we are going to follow the general ubuntu build [instructions][2] (with some modifications)

2. Building CMake
    * We may need to build CMake as the librealsense library notes:

        > Cmake Note: certain librealsense CMAKE flags (e.g. CUDA) require version 3.8+ which is currently not made available via apt manager for Ubuntu LTS.

    * To check your CMake version: `cmake --version`
    * If it is not >= 3.8, you will need to build it:
      * download the [CMake Source][3] 
      * follow the installation instructions [here][4]
      * Run `./bootstrap -- -DCMAKE_USE_OPENSSL=ON` as ros2 requires [this][8]

3. Building the library
    * Follow the [instructions][2], while making the modifications below.
    * Modifications: **Prepare Linux Backend and the Dev. Environment** 
        1. Step 4: we are going to skip this step and not patch the kernel.
            * As noted in this [discussion][5] the patch is not required.
            * As we Instructionsare running on a non-supported kernel (4.9), the patching scripts will not work.
            * If desired, you could build probably patch the 4.9 kernel on the TX2 by following what [JetsonHacks][6] does to get the d435i working on the Xavier.
    * Modifications: **Building Librealsense2 SDK**
        1. When running cmake, we want to run `cmake ../ -DBUILD_EXAMPLES=true -DFORCE_LIBUVC=true -DBUILD_WITH_CUDA=true`
            * You can read more about the build flags [here][7]
            * We are using the `FORCE_LIBUVC` flag as we did not patch the kernel.

### Testing
1. Now that the software is built and installed, we can run the realsense-viewer
   * Run `realsense-viewer`
   * When the application is launched, changed the *Stereo Module* settings to:
      * Resolution: 640 x 480
      * FPS: 6
   * Turn on the Stereo Module


[1]:https://github.com/IntelRealSense/librealsense
[2]:https://github.com/IntelRealSense/librealsense/blob/master/doc/installation.md
[3]:https://cmake.org/download/
[4]:https://cmake.org/install/
[5]:https://github.com/IntelRealSense/librealsense/issues/1039#issuecomment-359069915
[6]:https://www.jetsonhacks.com/2019/01/21/intel-realsense-d435i-on-nvidia-jetson-agx-xavier/
[7]:https://github.com/IntelRealSense/librealsense/wiki/Build-Configuration
[8]:https://github.com/ros2/ros2/issues/470#issuecomment-371141641
