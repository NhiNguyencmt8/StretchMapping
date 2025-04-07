## Usage 🎮

### Before Running Anything

Remember to source your workspace:
```bash
source ~/catkin_ws/devel/setup.bash
```
## Some guidelines
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

## Additional Setup for ADE20K Dataset 🖼️

This project uses an online segmentation pipeline with a module trained on the ADE20K dataset. Add the following files inside your Khronos folder:

- `ade20kfull.csv` => Place into `hydra_ros/hyra_ros/config/color`
- `ade20kfull.yaml` => Place into `hydra/config/label_repmaps`
- `ade20kfull_label_space.yaml` => Place into `hydra/config/label_spaces`

> 💡 Feel free to adjust these configurations if you are using a different model.

---
