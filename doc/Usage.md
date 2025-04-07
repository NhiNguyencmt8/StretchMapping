# Usage 🎮


## Setup

Remember to source your workspace:
```bash
source ~/catkin_ws/devel/setup.bash
```

#### Additional Setup for ADE20K Dataset 🖼️

This project uses an online segmentation pipeline with a module trained on the ADE20K dataset. Add the following files inside your Khronos folder:

- `ade20kfull.csv` => Place into `hydra_ros/hyra_ros/config/color`
- `ade20kfull.yaml` => Place into `hydra/config/label_repmaps`
- `ade20kfull_label_space.yaml` => Place into `hydra/config/label_spaces`

> 💡 Feel free to adjust these configurations if you are using a different model.



## Run segmentation and localization
To run `segmentation_inference` pipeline:
```bash
roslaunch semantic_inference_ros semantic_inference.launch
```
Remember to switch the ROS topic input in the launch file with your image topic. Sometimes there is some mismatch between your image raw input, the segmentation pipeline and Khronos input. Therefore, check the image type and sizes before running Khronos (you can also check our `script/reshape.py` for reference).

To run `ORB_SLAM`:
```bash
rosrun ORB_SLAM ORB_SLAM PATH_TO_VOCABULARY PATH_TO_SETTINGS_FILE
```
Note: You might want to check our depth camera performance and tune of config it to make sure the output is at best.

## Run Khronos

You can run either offline using ROS-bags or online on a real Stretch.

### Running Khronos with Bag Files (Offline) 🗂️

To process a bag file:
```bash
roslaunch khronos_ros stretch_mapping_offline.launch bag_path:=/your/path/to/bag/file
```

### Running Khronos Live (Online) 🟢

For live mapping, set up the `segmentation_inference` module and run:
```bash
roslaunch khronos_ros stretch_mapping_online.launch
```

### Tuning Khronos ☕
If you want your performance to be better on the robot, it is best to tune it. The tunning configs can be found at `config/mapper/yourconfig.yaml` file. Here is some of our intuition notes while tuning that might help:

| Params                               | Original Value | Best Value (for our Stretch) | Intuition/What does it affect when you change it                                                                                                                                  | Definition                                                                                                                                 |
|--------------------------------------|----------------|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| min_output_separation                | 0.0            | 5-10s      | Depends on how slow you want Khronos to run - time between outputs                                                                                                               | Min time between outputs                                                                                                                   |
| temporal_window                      | 3              | 10 - 100   | Updating slower                                                                                                                                                                  | Time duration (s) defining how long the observation should be considered for processing the window                                            |
| min_cluster_size                     | 50             | 100        | Removes the smaller detections                                                                                                                                                   | In motion detection, it filters small, insignificant movements. In object detection, it ensures only sufficiently large objects are are considered |
| use_full_connectivity                | true           | false      | Cleaner mesh and objects/bounding box                                                                                                                                           | Determines if full connectivity should be used when clustering objects in the detection process                                               |
| min_object_volume                    | 0.005          | 0.5        | Detected objects' min volume                                                                                                                                                      | Specifies the minimum volume (in m³) that an object must have to be considered valid for extraction and tracking                              |
| min_object_reconstruction_confidence | 0.5            | 0.70       | Only if really high, removing a few bounding boxes otherwise the confidence score is very high for the objects?                                                                    | Minimum confidence threshold (0 to 1) required for an object to be considered successfully reconstructed                                      |
| ray_policy                           | Middle         | FirstAndLast | Gives better detections                                                                                                                                                           |                                                                                                                                             |
---
