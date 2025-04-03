
---
## Static Objects + No Person in view

This is experiment #1 where we evaluate Khronos (with and without Orbslam). In this scenario, we do not move any objects (in the apartment) throught the run and there are no persons in the view of robot as well. The experiment was conducted on Stretch RE2 Robot.

Therefore there are **no** dynamic objects in the scene. The map is recorded for 1 one round of the apartment setting.

### Khronos with Stretch Odometry

| Khronos Prediction | Ground Truth |
|:----------:|:---------------:|
| <img src="https://github.com/user-attachments/assets/2fd1fde5-eacd-4d8e-85c7-0b4b0efed4d7" width="100%"> | <img src="https://github.com/user-attachments/assets/a4a49dfb-b562-47bd-a0c3-60003c86ad84" width="100%"> |


**Object Detection Metrics**: 
- Recall: ???
- Missed Objects: Plates, Apple, Bottle, Table, Plant, Side Drawer, Ball, TV, Wall.


**Dynamic Object Classification**: 
- F1 Score: ???
- False Positives: ???,???
- False Negatives: ???,???


**Qualitative Observation**: Smaller objects like the ones mentioned above were discarded by the algorithm. Objects like TV, wall, Plant and Side Drawer were also not registered as objcts despite being segmented by the segmentation pipeline.

### Khronos with ORBSLAM2

| Khronos Prediction | Ground Truth |
|:----------:|:---------------:|
| <img src="https://github.com/user-attachments/assets/52c210ca-6a3d-42e6-bd80-3dc530a2d3af" width="100%"> | <img src="https://github.com/user-attachments/assets/a4a49dfb-b562-47bd-a0c3-60003c86ad84" width="100%"> |


**Object Detection Metrics**: 
- Recall: ???
- Missed Objects: Plates, Apple, Bottle, Plant, Ball, TV, Wall.


**Dynamic Object Classification**: 
- F1 Score: ???
- False Positives: ???,???
- False Negatives: ???,???

**Qualitative Observation**: With the addition of ORBSLAM2, Khronos was able to register Table and Side Drawer as objects. This could be because of better mesh creation, these objects were not considered as dynamic and thereby registered as objects.
