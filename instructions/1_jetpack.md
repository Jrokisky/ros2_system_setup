# Setting Up Jetpack


## What is Jetpack?
> NVIDIA JetPack SDK is the most comprehensive solution for building AI applications. Use the JetPack installer to flash your Jetson Developer Kit with the latest OS image, install developer tools for both host PC and Developer Kit, and install the libraries and APIs, samples, and documentation needed to jumpstart your development environment.

[More Info](https://developer.nvidia.com/embedded/jetpack)

## Background Information
* We are going to be using the [NVIDIA SDK Manager](https://docs.nvidia.com/sdk-manager/index.html) to install Jetpack on the TX2. I reccomend spending some time


## Installation Instructions
* The instructions provided by NVIDIA are straightforward and easy to follow

# First: Installing the SDK Manager
* Create an NVIDIA Develepor account [here](https://developer.nvidia.com/)
* We are going to be following the instructions [here](https://docs.nvidia.com/sdk-manager/download-run-sdkm/index.html). Any needed modifications or pain points will be outlined below. Please review them first.

# Second: Using the SDK Manager to Install Jetpack
* We are going to be following the instructions [here](https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html). Any needed modifications or pain points will be outlined below. Please review them first.
* If you run into the error: `could not load the NDVIDIA sdk details`:
  * Shut down the SDK Manager
  * run `rm -rf ~/.nvsdkm`
  * try again
* When it is time to flash the TX2, we are going to want to manually force recovery mode
  * To place system in Force USB Recovery Mode
    1. Power down the device. If connected, remove the AC adapter from the device. The device must be powered OFF, and not in a suspend or sleep state.
    2. Connect the Micro-B plug on the USB cable to the Recovery (USB Micro-B) Port on the device and the other end to an available USB port on the host PC.
    3. Connect the power adapter to the device.
    4. With the system powered on:
      a. Press and hold the RECOVERY FORCE buon.
      b. While depressing the RECOVERY FORCE buon, press and release the RESET buon.
      c. Wait 2 seconds and release the RECOVERY FORCE buon.
