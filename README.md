![Digital Twins](https://github.com/abizovnuralem/go2_ros2_sdk/assets/33475993/ddbe30ab-21d1-46fd-b44b-198efba92771)

About This Fork
This repository is a fork of [go2_omniverse](https://github.com/abizovnuralem/go2_omniverse), modified to support Isaac Sim 4.2.0 and IsaacLab 1.2.0. This fork includes adjustments to ensure compatibility with these versions and may contain additional updates or enhancements specific to this setup.


# Welcome to the Unitree Go2/G1 Digital Twins Project!

[![IsaacSim](https://img.shields.io/badge/IsaacSim-orbit-gold.svg)](https://docs.omniverse.nvidia.com/isaacsim/latest/overview.html)
[![Python](https://img.shields.io/badge/python-3.10-blue.svg)](https://docs.python.org/3/whatsnew/3.10.html)
[![Linux platform](https://img.shields.io/badge/platform-linux--64-orange.svg)](https://releases.ubuntu.com/22.04/)
[![License](https://img.shields.io/badge/license-BSD--2-yellow.svg)](https://opensource.org/licenses/BSD-2-Clause)

We are thrilled to announce that the Unitree Go2/G1 robot has now been integrated with the Nvidia Isaac Sim (Orbit), marking a major step forward in robotics research and development. The combination of these two cutting-edge technologies opens up a world of possibilities for creating and testing algorithms in a variety of simulated environments.

Get ready to take your research to the next level with this powerful new resource at your fingertips!


## Real time Go2 Balancing:

<p align="center">
<img width="1280" height="600" src="https://github.com/akoshouta/go2_omniverse/assets/33475993/60c2233a-7586-49b6-a134-a7bddc4dd9ae" alt='Go2'>
</p>


## Real time G1 Balancing:

<p align="center">
<img width="1280" height="600" src="https://github.com/akoshouta/go2_omniverse/assets/33475993/d035f72a-8996-461c-a902-38e68052d029" alt='Go2'>
</p>


## Go2 Ros2 Camera stream:

<p align="center">
<img width="1200" height="440" src="https://github.com/akoshouta/go2_omniverse/assets/33475993/c740147b-ce00-4d7c-94de-0140be135e3e" alt='Go2'>
</p>


## URDF real-time joints sync:

<p align="center">
<img width="1200" height="440" src="https://github.com/akoshouta/go2_omniverse/assets/33475993/a8060b6e-e9b7-4d30-89f2-8a50b7510a2b" alt='Go2'>
</p>

## Foot force data stream:

<p align="center">
<img width="1200" height="440" src="https://github.com/akoshouta/go2_omniverse/assets/33475993/95a34b03-471e-496a-88cc-38e7c4e1906d" alt='Go2'>
</p>


## Real-time RTX lidar stream:

<p align="center">
<img width="1200" height="440" src="https://github.com/akoshouta/go2_omniverse/assets/33475993/3f078bf2-e4b6-45ca-8807-36537a4125b5" alt='Go2'>
</p>


## Custom envs (Office):

<p align="center">
<img width="1200" height="440" src="https://github.com/akoshouta/go2_omniverse/assets/33475993/e2e9bdd0-1f40-41a8-86bc-c1097ab3fd7b" alt='Go2'>
</p>


## Custom envs (Warehouse):

<p align="center">
<img width="1200" height="440" src="https://github.com/akoshouta/go2_omniverse/assets/33475993/5db6f331-60be-40bd-9b4b-ead44064ee44" alt='Go2'>
</p>


## VR support:

<p align="center">
<img width="1200" height="440" src="https://github.com/akoshouta/go2_omniverse/assets/33475993/d5b82fac-d945-4462-8b3d-4026456847f4" alt='Go2'>
</p>


## Project RoadMap:
1. PPO balancing algorithm :white_check_mark: 
2. Keyboard real time control :white_check_mark: 
3. Camera stream to ROS2 :white_check_mark: 
4. RTX Lidar stream to ROS2 :white_check_mark:
5. IMU data stream to ROS2 :white_check_mark: 
6. URDF real-time joints sync :white_check_mark:
7. Foot force data stream :white_check_mark:
8. Real-time control from ROS2 :white_check_mark:
9. Nav2 with Slam_toolbox :white_check_mark:
10. Bunch of RL-envs for custom dog training :white_check_mark:
11. Custom numbers of robots :white_check_mark:
12. Added G1 Unitree support :white_check_mark:

## Your feedback and support mean the world to us. 

If you're as enthusiastic about this project as we are, please consider giving it a :star: star on our GitHub repository. 

Your encouragement fuels our passion and helps us develop our RoadMap further. We welcome any help or suggestions you can offer!

Together, let's push the boundaries of what's possible with the Unitree Go2/G1 and ROS2!


## System requirements and installation
You need to install:
1. Ubuntu 22.04
2. Nvidia Isaac Sim 4.2.0
3. Nvidia IsaacLab 1.2.0
4. Ros2 Humble


Full instruction:
```
# Step 1: Clone the IsaacLab repository
git clone --branch v1.2.0 https://github.com/isaac-sim/IsaacLab.git

# Step 2: Set necessary environment variables (add to ~/.bashrc for persistence)
export ISAACSIM_PATH="${HOME}/.local/share/ov/pkg/isaac-sim-4.2.0"
export ISAACSIM_PYTHON_EXE="${ISAACSIM_PATH}/python.sh"
echo 'export ISAACSIM_PATH="${HOME}/.local/share/ov/pkg/isaac-sim-4.2.0"' >> ~/.bashrc
echo 'export ISAACSIM_PYTHON_EXE="${ISAACSIM_PATH}/python.sh"' >> ~/.bashrc
source ~/.bashrc

# Step 3: Create a symbolic link for Isaac Sim inside the IsaacLab directory
cd IsaacLab
ln -s ${ISAACSIM_PATH} _isaac_sim

# Step 4: Set up the Conda environment
./isaaclab.sh --conda

# Step 5: Activate the Conda environment "isaaclab"
conda activate isaaclab

# Step 6: Install CMake and build-essential
sudo apt install cmake build-essential -y

# Step 7: Install required extensions inside IsaacLab
./isaaclab.sh --install

# Step 8: Verify installation
python source/standalone/tutorials/00_sim/create_empty.py

# Step 9: Check if "Isaac Sim Python 4.2.0 - New Stage" is displayed at the top of the Isaac Sim window
# If there are no issues at this step, proceed to the next step

# Step 10: Clone the go2_omniverse repository in the same directory level as IsaacLab
cd ../
git clone https://github.com/akoshouta/go2_omniverse/ --recurse-submodules -j8 --depth=1

# Step 11: Copy the Unitree L1 LiDAR configuration file (work from the directory with IsaacLab and go2_omniverse folders)
mkdir -p ./IsaacLab/source/exts/omni.isaac.sensor/data/lidar_configs
cp go2_omniverse/Isaac_sim/Unitree/Unitree_L1.json IsaacLab/source/exts/omni.isaac.sensor/data/lidar_configs/Unitree_L1.json

# Step 12: Copy files from the material_files folder
mkdir -p IsaacLab/source/data/material_files
cp -r ${ISAACSIM_PATH}/kit/mdl/* IsaacLab/source/data/material_files/

# Step 13: Run the simulation (ensure the Conda environment is deactivated) >> make sure conda commands work in the (base) environment
conda deactivate
./run_sim.sh

```

Some suggestions:
1. You need to check nvidia-smi, it should work, before installing Isaac Sim
2. You need to install Miniconda and execute: conda config --set auto_activate_base false
3. Install Omniverse launcher and then install Isaac Sim.
4. You need to install ROS2 on your system and configure it:

```
https://docs.omniverse.nvidia.com/isaacsim/latest/installation/install_ros.html#isaac-sim-app-install-ros
```

## Usage
The current project was tested on Ubuntu 22.04, IsaacSim 2023.1.1 with Orbit 0.3.0 and Nvidia Driver Version: 545.
To start the project with Unitree GO2, execute:

```
./run_sim.sh
```

To start the project with Unitree G1, execute:

```
./run_sim_g1.sh
```

You can control the dog using "WASD" keyboard commands

## ROS2 SDK

You can use https://github.com/abizovnuralem/go2_ros2_sdk as a basement for your ROS2 setup.


## Select custom env

To use predifined custom envs, you need to download files from https://drive.google.com/drive/folders/1vVGuO1KIX1K6mD6mBHDZGm9nk2vaRyj3?usp=sharing and place them to /envs folder.
Then you can execute it modifying run_sim.sh script with --custom_env=office and --terrain flat commands. If you are doing it first time, it will take 2-3 minutes to configure the env. Please, wait.


## Development

To contribute or modify the project, refer to these resources for implementing additional features or improving the existing codebase. PRs are welcome!

## VR support

To enable VR support on linux will take some time, but it works!
I have tested it on:
1. Ubuntu 22.04
2. Nvidia drivers are 545.29.06 
3. SteamVR 2.4.4 (IMPORTANT! It should be 2.4.4) and you need to go to Compatibility tab (Inside Steam app) and "Force the use of a specific Steam Play compatibility tool" and switch to "Steam-Play-None", additional info you can find in ALVR github issues tab.
4. ALVR streamer 20.8.1 + Oculus Quest 2 (client ALVR you can install via SideQuest app) (How to install it: https://github.com/alvr-org/ALVR)
5. Execute IsaacSim, Go to Window -> Extensions, find STEAMVR INPUT/OUTPUT then enable it and enable AutoLoad. Reopen IsaacSim. Use OpenXR mode.
6. Enjoy Omniverse in VR mode!


## Troubleshooting:

### The version of Isaac Simulator 2023.1.1 is no longer available on Omniverse Launcher, what should I do? 

1. Go to [Container Installation](https://docs.omniverse.nvidia.com/isaacsim/latest/installation/install_container.html) and follow all the steps in the **Container Deployment** section up to step 5).
2. Modify the command in step 6) with: 
```bash
docker pull nvcr.io/nvidia/isaac-sim:2023.1.1
```
3. Now run this command: 
```bash
docker run --name isaac-sim --entrypoint bash -it --runtime=nvidia --gpus all -e "ACCEPT_EULA=Y" --rm --network=host \
    -e "PRIVACY_CONSENT=Y" \
    -v ~/docker/isaac-sim/cache/kit:/isaac-sim/kit/cache:rw \
    -v ~/docker/isaac-sim/cache/ov:/root/.cache/ov:rw \
    -v ~/docker/isaac-sim/cache/pip:/root/.cache/pip:rw \
    -v ~/docker/isaac-sim/cache/glcache:/root/.cache/nvidia/GLCache:rw \
    -v ~/docker/isaac-sim/cache/computecache:/root/.nv/ComputeCache:rw \
    -v ~/docker/isaac-sim/logs:/root/.nvidia-omniverse/logs:rw \
    -v ~/docker/isaac-sim/data:/root/.local/share/ov/data:rw \
    -v ~/docker/isaac-sim/documents:/root/Documents:rw \
    nvcr.io/nvidia/isaac-sim:2023.1.1
```
4. Open another terminal and run the command ```bash docker ps``` to find the container's ID.
5. From the terminal inside the container, run this command to copy the entire Isaac 2023.1.1 folder to a folder on your computer (*I suggest naming it isaac-sim-2023.1.1 so that the setup commands above work*):
```bash
docker cp <id_container>:isaac-sim/. <your_local_machine_folder> # absolute path
```
6. On your PC, you will have a folder named **isaac-sim-2023.1.1**. Move it to the following path:
```bash
.local/share/ov/pkg/
```

### Could not import 'rosidl_typesupport_c' for package 'go2_interfaces'

If running ```./run_sim.sh``` results in the error **"Could not import 'rosidl_typesupport_c' for package"**, refer to this [thread](https://github.com/ros2/examples/issues/303).


## Thanks
Special thanks to 
1. Leul Tesfaye for his expertise in Orbit lidars;
2. Tamas @tfoldi for contributing to this project;
3. @ShaoshuSu for his hardwork in investigating the speed issues with new version of Orbit (IsaacLab 4.0 and 4.1);


## License

This project is licensed under the BSD 2-clause License - see the [LICENSE](https://github.com/abizovnuralem/go2_omniverse/blob/master/LICENSE) file for details.
