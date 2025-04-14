Welcome to **Stretch Mapping**, a semantic mapping framework built on [Khronos](https://github.com/MIT-SPARK/Khronos)[1] and [ORB-SLAM2](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=7946260)[2] for creating a semantic map using the [Hello Robot Stretch](https://hello-robot.com) mobile manipulator. Khronos is a semantic mapping pipeline that relies on visual SLAM, and semantic segmentation from RGB-D perception, and creates a hierarchical 3-D map of the world. We utilize the Stretch manipulation platform, which is equipped with a Intel RealSense D435i. We use [semantic inference](https://github.com/harshmuriki/semantic_inference) codebase which offers ROS integration for semantic segmentation and [ORB-SLAM2](https://github.com/raulmur/ORB_SLAM2)[2] codebase with ROS integration for robot localization. This mapping framework is capable of creating hierarchical object-centric maps, tracking moving objects, and maintaining long-term object changes, and provides a rich contextual understanding for household navigation and mobile manipulation.


|![](/doc/human_moving_two_new2.gif)|![](/doc/khronos_map_orb.gif)|![](/doc/sg_khronos_noorb.gif) |
| :---: | :---: |:---:|
| Dynamic human tracking | Metric semantic mapping | Topological mapping |

[1] Lukas Schmid, Marcus Abate, Yun Chang, and Luca Carlone. Khronos: A unified approach for spatio-temporal
metric-semantic slam in dynamic environments. In Proc. of Robotics: Science and Systems (RSS), Delft, Nether-
lands, July 2024.

[2] Montiel J. M. M. Mur-Artal, Raúl and Juan D. Tardós. ORB-SLAM: a versatile and accurate monocular SLAM
system. IEEE Transactions on Robotics, 31(5):1147–1163, 2015.


[![Python 3](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Email](https://img.shields.io/badge/Email-contact-blue.svg)](mailto:nnguyen349@gatech.edu)
[![Stretch Robot](https://img.shields.io/badge/Stretch_Robot-V3-green.svg)](https://hello-robot.com/stretch-3-product)
[![Open Source](https://img.shields.io/badge/Open_Source-yes-brightgreen.svg)](https://opensource.org/)
<!-- <a href="https://www.ros.org">
  <img src="https://raw.githubusercontent.com/tandpfun/skill-icons/65dea6c4eaca7da319e552c09f4cf5a9a8dab2c8/icons/ROS-Dark.svg" alt="ROS" width="20" height="20">
</a> -->



**Table of Contents**
- [Installation 🚀 and Usage 🎮](#installation--and-usage-)
- [Quantitative Evaluation ✍🏼](#quantitative-evaluation-)
- [Support and Contribution 🤝](#support-and-contribution-)

---


## Installation 🚀 and Usage 🎮
 
This repository is tested on Ubuntu 20.04 and ROS Kinetic, but would potentially work on any ROS1 distribution. Refer to [Installation.md](doc/Installation.md) for installation instructions, and [Usage.md](doc/Usage.md) for instructions on how to run the system, both online on a robot and offline using ROS bags, and also a guide on how to tune various parameters.

---

## Quantitative Evaluation ✍🏼
<!-- [![Watch the video](https://img.youtube.com/vi/9r7H5XKUNsc/maxresdefault.jpg)](https://www.youtube.com/watch?v=9r7H5XKUNsc) -->

We assess the performance of our proactive mapping pipeline in a household environment with a person interacting with objects both in and out of the Stretch robot's field of view. We systematically evaluate our framework's ability to track moving objects and people within the robot's field of view and map objects displaced outside the robot's field of view by deploying the robot in the following four apartment scenarios:
1. [**Static Objects + No Person In View**](./doc/Static_Objects_No_Person_inView.md):
   *No people are present in the apartment and all objects remain still.*
2. [**Static Objects + Person Moving in View**](./doc/Static_Objects_Person_in_View.md):
   *A person moves inside the aparment within the robot's field of view but does not move any objects.*
3. [**Displaced Objects + No Person in View**](./doc/Displaced_Objects_No_Person_InView.md):
   *A person moves an object but remains outside the robot's field of view.*
4. [**Moving Objects + Person Moving in View**](./doc/Dynamic_Objects_Person_InView.md):
   *A person moves an object within the robot's field of view.*

For each scenario, we measure the object recall scores of both Khronos using the robot's odometry and Khronos using localization measurements from ORBSLAM2. Recall measures the mapping framework's ability to correctly capture all object instances in the environment. Please refer to each individual scenario for detailed results.

---

## Support and Contribution 🤝

If you have any questions, feel free to post an issue on this repo or please reach out to our contributers. We're happy to help! To contribute to this codebase, please open a pull request or reach out to us via email.

#### Notice for contributing changes to Submodules ⚠️

**DON'T directly make changes to the submodules in the repository and expect them to be updated.** Since they are submodules, updates require a specific workflow. Instead, follow these steps:

1. Clone the submodule repository (e.g., for Khronos) and make changes:
   ```bash
   git clone git@github.com:<githubaccount>/Khronos.git
   cd Khronos
   # Make your changes here
   git add .
   git commit -m "Your changes"
   git push origin main
   ```

2. Navigate back to the StretchMapping repository:
   ```bash
   cd /path/to/StretchMapping
   ```

3. Update the submodule reference:
   ```bash
   git submodule status
   git submodule update --init --recursive
   cd Khronos
   git remote -v
   ```

   If the URL is incorrect or missing, set the correct remote:
   ```bash
   git remote set-url origin git@github.com:<githubaccount>/Khronos.git
   git fetch
   git checkout main
   ```

4. Update the submodule pointer in StretchMapping:
   ```bash
   cd ..
   git add Khronos
   git commit -m "Update Khronos submodule to latest revision"
   git push origin main
   git submodule update --remote --merge
   ```

## Contributors:
1. Harsh Muriki: harshsuhith@gmail.com
2. Nhi Nguyen (Leona): yennhi1908hcm@gmail.com
3. Rahul Rustagi: rustagirahul24@gmail.com
