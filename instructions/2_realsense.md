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
    * If it is not >= 3.8, download the [CMake Source][3] and follow the installation instructions [here][4]

3. Building the library
    * Modifications: in **Prepare Linux Backend and the Dev. Environment** 
        1. Step 2a: we want to run `./scripts/install_glfw3.sh` instead of `sudo apt-get install libglfw3-dev`
        2. Step 2b: run `sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev`
        3. Step 4: as of March 23 2019, there's a [PR open][5] that updates the jetson installation script
            * run: `cd scripts && wget https://raw.githubusercontent.com/IntelRealSense/librealsense/ce67126d1bf8903b0a537cccf366d607feef992d/scripts/patch-realsense-tx2.sh && cd ..`
            * if the file above is not found, navigate to the open pr, and get the link for the *patch-realsense-tx2.sh* script
            * run: `chmod +x scripts/patch-realsense-tx2.sh`
            * change line 35 of *patch-realsense-tx2.sh* to `[ ! -d ${kernel_name} ] && git clone https://github.com/jetsonhacks/buildJetsonTX2Kernel.git && cd buildJetsonTX2Kernel && ./getKernelSourcesNoGUI.sh && cd .. && cp /usr/src/kernel/${kernel_name} ./${kernel_name}`
            * run: `./scripts/patch-realsense-tx2.sh`

[1]:https://github.com/IntelRealSense/librealsense
[2]:https://github.com/IntelRealSense/librealsense/blob/master/doc/installation.md
[3]:https://cmake.org/download/
[4]:https://cmake.org/install/
[5]:https://github.com/IntelRealSense/librealsense/pull/1438
