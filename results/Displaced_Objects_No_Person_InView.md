---
## #3 Displace Objects + No Person in view

In this experiment, we evaluate Khronos (with and without ORBSLAM2). In this scenario, objects (in the apartment) are displaced while the robot maps the environment throught the run and there are no persons in the view of robot while it happens.

Therefore there are **no** dynamic objects in the scene, however objects are displaced but are still considered as static. The map is recorded for one round of the apartment setting and objects are moved such that the robot is able to observe it in a single complete round.

### Khronos with Stretch Odometry

| Khronos Prediction | Ground Truth |
|:----------:|:---------------:|
| <img src="https://github.com/user-attachments/assets/fa1e57ff-a8a2-4a81-aaee-35a21c28022a" width="92%"> | <img src="https://github.com/user-attachments/assets/a4a49dfb-b562-47bd-a0c3-60003c86ad84" width="100%"> |


**Object Detection Metrics**: 
- Recall: ???
- Missed Objects: Plates, Apple, Bottle, Table, Plant, Side Drawer, Ball, TV, Wall, Lamp.


**Dynamic Object Classification**: 
- F1 Score: ???
- False Positives: ???,???
- False Negatives: ???,???

**Qualitative Observation**: Smaller objects such as the ones mentioned above were discarded by the algorithm. Objects such as TV, wall, Plant and Side Drawer were also not registered as objcts despite being segmented by the segmentation pipeline.

### Khronos with ORBSLAM2

| Khronos Prediction | Ground Truth |
|:----------:|:---------------:|
| <img src="https://github.com/user-attachments/assets/79a546e8-023a-4255-92f0-3af3a5d90b6d" width="92%"> | <img src="https://github.com/user-attachments/assets/a4a49dfb-b562-47bd-a0c3-60003c86ad84" width="100%"> |


**Object Detection Metrics**: 
- Recall: ???
- Missed Objects: Plates, Apple, Bottle, Table, Plant, Side Drawer, Ball, TV, Wall, Lamp.


**Dynamic Object Classification**: 
- F1 Score: ???
- False Positives: ???,???
- False Negatives: ???,???

**Qualitative Observation**: With the addition of ORBSLAM2, Khronos did not perform substantially better. Same results were seen.
