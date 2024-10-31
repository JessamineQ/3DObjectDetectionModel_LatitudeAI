# 3D Object Detection Model
In this project, we aim to bridge the gap between 2D object detection and 3D scene understanding—a crucial step for applications like self-driving cars and robotics. While 2D object detection helps us identify and locate objects in images, it doesn’t tell us how far away these objects are. Knowing the distance is essential for navigating the real world safely. Our goal is to enhance 2D detections with depth information to approximate a 3D understanding of the scene.

This model integrates 2D object detection from Detectron2 and depth estimation from DepthAnything to approximate 3D scene understanding. Specifically, the model:
● Overlays 2D detection bounding boxes and segmentation masks onto depth maps.
● Uses segmentation masks to calculate the median depth of pixels for estimates of object distance.
● Utilizes nuScenes camera calibration data with Open3D to back-project 2D detections into 3D space and create a bird's-eye-view representation.
● Approximates object orientations by leveraging heuristics and compares 3D estimations with the ground truth data from the nuScenes dataset.
