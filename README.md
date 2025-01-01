# Bird-Eye-View-Perception-for-Autonomous-Driving

In Bird's Eye View (BEV) perception, the goal is to transform the 3D world into a top-down representation that simplifies scene understanding for tasks such as autonomous driving and robotics. BEV representations are inherently 2D, offering view of the environment from above. However, cameras only capture images in perspective views, making the transition from camera data to BEV hard to perform. 

The 3D to 2D projection plays a critical role in bridging this gap. It involves mapping points from the 3D world to the 2D plane of a camera image. By projecting 3D coordinates into the corresponding 2D camera views, this task aligns the real-world spatial data with the visual perspective captured by cameras. This alignment is essential for constructing accurate BEV representations, enabling machines to interpret the world effectively in both 3D and 2D contexts.

![3D_points](https://github.com/user-attachments/assets/b9c73214-255f-4302-a560-94dba6b50658)

*3D Points*

This Python script takes a sample from the nuScenes dataset, loads images from all six cameras, extracts camera calibration parameters, generates random 3D points, projects these points onto the 2D images of each camera, and finally creates a Bird's Eye View (BEV) representation by combining the projected points from all cameras onto a single 2D grid. The BEV provides a top-down view of the scene, which is crucial for tasks like object detection, tracking, and path planning in autonomous driving.

![Image_projection_2D](https://github.com/user-attachments/assets/bccb16e9-950e-4239-8055-4d3c48bb8d7c)

*Projection of 3D points on 2D image*

## Requirements

```
Python 3.x
numpy
matplotlib
Pillow (PIL Fork)
pyquaternion
nuscenes-python (https://pypi.org/project/nuscenes-devkit/)
```

## Installation:

Bash
```
pip install numpy matplotlib Pillow pyquaternion nuscenes-python
```

## Usage

1. Download the nuScenes dataset (https://www.nuscenes.org/download).
2. Update the DATASET_DIR variable in the script to point to the downloaded dataset directory.
3. Run the script:

Bash
```
python Bird_Eye_View.ipynb
```

## Description
The script performs the following steps:

1. Loads a sample from the nuScenes dataset.
2. Retrieves images from all six cameras. `('CAM_FRONT', 'CAM_FRONT_LEFT', 'CAM_FRONT_RIGHT', 'CAM_BACK', 'CAM_BACK_LEFT', 'CAM_BACK_RIGHT')`
3. Extracts the intrinsic camera matrices (defines camera properties) and extrinsic parameters (camera pose - translation and rotation) for each camera.
4. Generates a set of random 3D points.
5. Defines a function `project_3d_2d` that takes 3D points, intrinsic matrix, extrinsic parameters, image width, and height as inputs. Uses the function to project the 3D points onto the 2D image plane of each camera, filtering out points that are outside the image boundaries.
6. Creates a subplot for each camera image and displays the original image with the projected points marked as red dots.
7. Generates a BEV image by combining the projected points from all cameras onto a single 2D grid. Points from different cameras are assigned distinct colors for better visualization.
8. Displays the BEV image, providing a top-down view of the projected points.

## Key Features
Visualizes camera images from all six nuScenes cameras in a sample.
Projects random 3D points onto each camera image.
Generates a BEV representation for a comprehensive scene understanding.
Uses color coding to differentiate points from different cameras in the BEV.

![BEV_projection](https://github.com/user-attachments/assets/02044012-b5e0-4acd-a22a-e6573d4e3004)

*BEV projection for images with color coding*

