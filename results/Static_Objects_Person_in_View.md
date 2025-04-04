---
## #2 Static Objects + People in view

This is experiment, we evaluate Khronos (with and without Orbslam). In this scenario, we do not move any objects (in the apartment) throught the run and there are no people in the view of robot as well.

Therefore there are **no** dynamic objects in the scene. The map is recorded for 1 one round of the apartment setting.

### Khronos with Stretch Odometry

[![Khronos with Stretch Odometry](https://img.youtube.com/vi/wpS3hwvFEQs/0.jpg)](https://www.youtube.com/watch?v=wpS3hwvFEQs)

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

[![Khronos with ORBSLAM2](https://img.youtube.com/vi/-J7cw7A4ItQ/0.jpg)](https://www.youtube.com/watch?v=-J7cw7A4ItQ)

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
