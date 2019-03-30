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
* We are going to be following the instructions [here](https://docs.nvidia.com/sdk-manager/download-run-sdkm/index.html).

# Second: Using the SDK Manager to Install Jetpack
* We are going to be following the instructions [here](https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html). Any needed modifications or pain points will be outlined below. Please review them first.
* If you run into the error: `could not load the NDVIDIA sdk details`:
  * Shut down the SDK Manager
  * run `rm -rf ~/.nvsdkm`
  * try again
* I reccomend running the installation in 2 steps due to potential issues with installing all software on the host machine:
  * First run: select "Host Machine" Hardware Configuration box and skip flashing the jetson. Then shutdown the sdk manager.
  * Second run: unselect "Host Machine" Hardware Configuration box and now flash the jetson
* When it is time to flash the TX2, we are going to want to manually force recovery mode by following the given instructions.

## Verifying Installation
