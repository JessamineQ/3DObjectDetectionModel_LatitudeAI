# 3D Object Detection Model

In this project, we built a 3D object detection model that bridges the gap between 2D object detection and 3D scene understanding. Our goal is to enhance 2D detections with depth information to approximate a 3D understanding of the scene by integrating 2D object detection from Detectron2 and depth estimation from DepthAnything. 

## Approach
- Overlay 2D detection bounding boxes and segmentation masks onto depth maps.
- Use segmentation masks to calculate the median depth of pixels for estimates of object distance.
- Utilize nuScenes camera calibration data with Open3D to back-project 2D detections into 3D space and create a bird's-eye-view representation.
- Approximate object orientations by leveraging heuristics and compares 3D estimations with the ground truth data from the nuScenes dataset.

## Setup Instructions

## Option 1: Google Colab (Recommended)

We recommend using Google Colab as it provides a pre configured environment with GPU support and all necessary dependencies.

1. Open the project notebook in Google Colab
2. All installation commands are included in the notebook
3. Run the cells in sequence to install dependencies and set up the environment

## Option 2: Local Setup 

If you prefer to run this project locally, follow these steps:

### Prerequisites
- Python 3.8 or higher
- CUDA-capable GPU (recommended)
- Git

### Installation Steps

First, clone the repository and set up your environment:

```bash
# Clone the repository
git clone https://github.com/JessamineQ/3DObjectDetectionModel_LatitudeAI.git
cd 3DObjectDetectionModel_LatitudeAI

# Create and activate a virtual environment
python -m venv venv

# On Windows:
venv\Scripts\activate

# On macOS/Linux:
source venv/bin/activate
```

Install the required packages:

```bash
# Install core dependencies
pip install -q "openvino>=2024.2.0" "datasets>=2.14.6" "nncf>=2.11.0" 
pip install -q "typing-extensions>=4.9.0" eval-type-backport "gradio>=4.19"

# Install machine learning frameworks
pip install -q "torch" "depthanything" "open3d" "plotly"
python -m pip install 'git+https://github.com/facebookresearch/detectron2.git'

# Install dataset utilities
pip install -q "nuscenes-devkit"
```

Download and extract the nuScenes mini dataset:

```bash
# Download the dataset
wget https://www.nuscenes.org/data/v1.0-mini.tgz

# Create directory and extract
mkdir -p /data/sets/nuscenes
tar -xf v1.0-mini.tgz -C /data/sets/nuscenes
```
