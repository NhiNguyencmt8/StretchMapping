# Stretch Mapping:  A semantic household tidying project using the Stretch robot
🤖🧹👕🧸👓 ⊂(▀¯▀⊂ )

---

## Installation 🚀

### Setup a Catkin Workspace 🛠️

1. Install required tools:
   ```bash
   sudo apt install python3-catkin-tools python3-vcstool python3-tk
   ```

2. Create and configure a Catkin workspace:
   ```bash
   mkdir -p ~/catkin_ws/src
   cd ~/catkin_ws
   catkin init
   catkin config --extend /opt/ros/$ROS_DISTRO
   catkin config --cmake-args -DCMAKE_BUILD_TYPE=RelWithDebInfo -DGTSAM_TANGENT_PREINTEGRATION=OFF -DGTSAM_BUILD_WITH_MARCH_NATIVE=OFF -DOPENGV_BUILD_WITH_MARCH_NATIVE=OFF
   catkin config --merge-devel
   ```

### Install System Dependencies 📦

```bash
sudo apt install ros-$ROS_DISTRO-gtsam libgoogle-glog-dev nlohmann-json3-dev
```

### Clone the Repository 📂

1. Navigate to the `src` folder of your Catkin workspace:
   ```bash
   cd ~/catkin_ws/src
   ```

2. Clone the Stretch Mapping repository:
   ```bash
   git clone git@github.com:NhiNguyencmt8/StretchMapping.git
   ```

3. Navigate to the Khronos submodule:
   ```bash
   cd StretchMapping/path/to/khronos
   ```

4. Import additional dependencies:
   ```bash
   vcs import . < install/ssh.rosinstall
   ```

5. Navigate back to the Catkin workspace root and build:
   ```bash
   cd ~/catkin_ws
   catkin build khronos_ros
   ```

---

## Additional Setup for ADE20K Dataset 🖼️

This project uses an online segmentation pipeline with a module trained on the ADE20K dataset. Add the following files inside your Khronos folder:

- `ade20kfull.csv` => Place into `hydra_ros/hyra_ros/config/color`
- `ade20kfull.yaml` => Place into `hydra/config/label_repmaps`
- `ade20kfull_label_space.yaml` => Place into `hydra/config/label_spaces`

> 💡 Feel free to adjust these configurations if you are using a different model.

---

## Usage 🎮

### Before Running Anything

Remember to source your workspace:
```bash
source ~/catkin_ws/devel/setup.bash
```

### Running Khronos with Bag Files (Offline) 🗂️

To process a bag file:
```bash
roslaunch khronos_ros stretch_mapping_offline.launch bag_path:=/your/path/to/bag/file
```

### Running Khronos Live (Online) 🔴

For live mapping, set up the `segmentation_inference` module (TBD) and run:
```bash
roslaunch khronos_ros stretch_mapping_online.launch
```

---

## Support 🤝 (*ΦωΦ*)

If you have any questions, please reach out to **Harsh** or **Leona**. We're happy to help!
