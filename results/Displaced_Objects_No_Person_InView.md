---
## #3 Displaced Objects + No People in view

In this experiment, we evaluate Khronos (with and without ORBSLAM2). In this scenario, objects (in the apartment) are displaced while the robot maps the environment throught the run and there are no people in the view of robot while it happens.

Therefore there are **no** dynamic objects in the scene, however objects are displaced but are still considered as static. The map is recorded for **two** rounds of the apartment setting and objects are first static while robot completes 1st round after which they are displaced during robot's 2nd round.

### Khronos with Stretch Odometry

| Khronos Prediction after round 1| Ground Truth (after round 1) |
|:----------:|:---------------:|
| <img src="https://github.com/user-attachments/assets/c9dc990e-4f2d-4bd7-ab4a-eb9fc75ead27" width="97%"> | <img src="https://github.com/user-attachments/assets/b90eaa47-be16-47b4-ab9e-a7c63f214b4e" width="100%"> |
| **Khronos Prediction after round 2** | **Ground Truth (after round 2)** |
| <img src="" width="97%"> | <img src="https://github.com/user-attachments/assets/6dd9b859-3424-4aa1-b30e-91efcc4e338c" width="100%"> |
**Object Detection Metrics**: 
- Recall: ???
- Missed Objects: Plates, Apple, Bottle, Table, Plant, Side Drawer, Ball, TV, Wall, Lamp.

**Dynamic Object Classification**: 
- F1 Score: ???
- False Positives: ???,???
- False Negatives: ???,???

**Qualitative Observation**: Smaller objects such as the ones mentioned above were discarded by the algorithm. Objects such as TV, wall, Plant and Side Drawer were also not registered as objcts despite being segmented by the segmentation pipeline.

### Khronos with ORBSLAM2

| Khronos Prediction with ORBSLAM2 after round 1| Ground Truth (after round 1) |
|:----------:|:---------------:|
| <img src="https://github.com/user-attachments/assets/4e277384-db7c-41f9-8d7c-43adec773648" width="97%"> | <img src="https://github.com/user-attachments/assets/b90eaa47-be16-47b4-ab9e-a7c63f214b4e" width="100%"> |
| **Khronos Prediction with ORBSLAM2 after round 2** | **Ground Truth (after round 2)** |
| <img src="https://github.com/user-attachments/assets/f7c66edf-e399-4066-a742-c39731559599" width="97%"> | <img src="https://github.com/user-attachments/assets/6dd9b859-3424-4aa1-b30e-91efcc4e338c" width="100%"> |


**Object Detection Metrics**: 
- Recall: ???
- Missed Objects: Plates, Apple, Bottle, Table, Plant, Side Drawer, Ball, TV, Wall, Lamp.


**Dynamic Object Classification**: 
- F1 Score: ???
- False Positives: ???,???
- False Negatives: ???,???

**Qualitative Observation**: With the addition of ORBSLAM2, Khronos did not perform substantially better. Same results were seen.
