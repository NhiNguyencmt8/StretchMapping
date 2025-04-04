---
## #4 Dynamic Objects + Person Walking in view

In this experiment, we evaluate Khronos (with and without ORBSLAM2). In this scenario, objects (in the apartment) are moved by a person in view of robot while it maps the environment throught the run.

Therefore there are objects and people as dynamic objects in the scene. The map is recorded for **one** round of the apartment setting and objects are moved such that the robot is able to observe it being moved by a person. Since Khronos's map after 2 consecutive rounds was comparitively cluttered, we cinducted evaluation based on one round itself.

### Khronos with Stretch Odometry


[![Khronos with Stretch Odometry](https://img.youtube.com/vi/M61HHTHAjOE/0.jpg)](https://www.youtube.com/watch?v=M61HHTHAjOE)


| Ground Truth (after round 1) | **Ground Truth (after round 2)**|
|:----------:|:---------------:|
| <img src="https://github.com/user-attachments/assets/f2b72798-91da-4bad-9eed-abb3c47eeedb" width="97%"> | <img src="https://github.com/user-attachments/assets/e409aaa8-7c10-458a-a637-5481dacd5879" width="100%"> |
| **Khronos prediction without ORBSLAM2**|
| <img src="https://github.com/user-attachments/assets/041a66ee-b055-4d1f-82d6-27b147b8fca2" width="100%"> |


**Object Detection Metrics**: 
- Recall: ???
- Missed Objects: Plates, Apple, Bottle, Table, Plant, Side Drawer, Ball, TV, Wall, Lamp.

**Dynamic Object Classification**: 
- F1 Score: ???
- False Positives: ???,???
- False Negatives: ???,???

**Qualitative Observation**: Smaller objects such as the ones mentioned above were discarded by the algorithm. Objects such as TV, wall, Plant and Side Drawer were also not registered as objcts despite being segmented by the segmentation pipeline.

### Khronos with ORBSLAM2

[![Khronos with ORBSLAM2](https://img.youtube.com/vi/yU0WspPV09g/0.jpg)](https://www.youtube.com/watch?v=yU0WspPV09g)

| Ground Truth (after round 1) | **Ground Truth (after round 2)**|
|:----------:|:---------------:|
| <img src="https://github.com/user-attachments/assets/f2b72798-91da-4bad-9eed-abb3c47eeedb" width="97%"> | <img src="https://github.com/user-attachments/assets/e409aaa8-7c10-458a-a637-5481dacd5879" width="100%"> |
| **Khronos prediction without ORBSLAM2**|
| <img src="https://github.com/user-attachments/assets/4f727960-aad4-41ad-9e95-2a0246433b21" width="100%"> |


**Object Detection Metrics**: 
- Recall: ???
- Missed Objects: Plates, Apple, Bottle, Table, Plant, Side Drawer, Ball, TV, Wall, Lamp.


**Dynamic Object Classification**: 
- F1 Score: ???
- False Positives: ???,???
- False Negatives: ???,???

**Qualitative Observation**: With the addition of ORBSLAM2, Khronos did not perform substantially better. Same results were seen.
