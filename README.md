# Face-Mask-Detection_Using_YOLOV5
![image](https://github.com/user-attachments/assets/a5c714dd-867f-42e1-ba6e-20f7220496b5)

An automated system to detect whether people are wearing masks in public areas using YOLOv5. This project is designed to enhance public health safety by monitoring mask compliance in real-time.

## Features
- Real-time face mask detection.
- High accuracy and speed using YOLOv5.
- Binary classification: `Mask` and `No Mask`.
- Scalable for deployment on edge devices or cloud platforms.

## Table of Contents
- [Overview](#overview)
- [Setup and Installation](#setup-and-installation)
- [Dataset](#dataset)
- [Model Training](#model-training)
- [Results](#results)
- [Deployment](#deployment)
- [Future Improvements](#future-improvements)

---

## Overview
This project utilizes the YOLOv5 object detection model to identify whether individuals are wearing masks properly. The system is trained on a custom dataset, fine-tuned for high precision and recall. The final model is capable of:

- Detecting masks in real-time through webcam or video feeds.
- Providing metrics such as Precision, Recall, and mAP to evaluate performance.

---

## Setup and Installation
### Step 1: Clone the Repository
```bash
!git clone https://github.com/ultralytics/yolov5.git
cd yolov5
```

### Step 2: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Download Pre-trained Weights
```bash
!wget https://github.com/ultralytics/yolov5/releases/download/v6.0/yolov5m.pt
```

---

## Dataset
- The dataset consists of images labeled with two classes: `Mask` and `No Mask`.
- **Structure:**
  - Training Images: `train/`
  - Validation Images: `valid/`
  - Labels: `labels/`

### Configuration
Modify the `data.yaml` file:
```yaml
train: path_to_train_dataset
val: path_to_validation_dataset
nc: 2
names: ['Mask', 'No Mask']
```

---

## Model Training
### Command
```bash
!python train.py --img 640 --batch 8 --epochs 300 --data data.yaml --weights yolov5m.pt --cache
```
### Training Parameters
- **Image Size:** 640x640 pixels
- **Batch Size:** 8
- **Epochs:** 300
- **Optimizer:** SGD
- **Augmentations:** Flipping, scaling, and color adjustments

---

## Results
- **Precision (P):** 82.8%
- **Recall (R):** 78.0%
- **mAP@50:** 83.6%
- **mAP@50-95:** 51.1%

### Example Output
Sample detection results:
- Image with Mask: ![Mask Detection](![image](https://github.com/user-attachments/assets/c9ea06cb-b006-431c-bf12-1a88f44115ba)
)
- Image without Mask: ![No Mask Detection](![RTX7CCFN_jpg rf 501a9e3af09662fc1fbd288a32904267](https://github.com/user-attachments/assets/fa60ba7d-12f0-4425-8b59-eae3d374fb31)
)

---

## Deployment
### Real-time Detection
Run the following command to start real-time detection:
```bash
!python detect.py --weights runs/train/exp/weights/best.pt --img 640 --source 0
```
---

## Future Improvements
- Expand the dataset for greater diversity in lighting and environments.
- Add a multi-class detection feature to distinguish between `Proper Mask`, `Improper Mask`, and `No Mask`.
- Optimize for edge devices like Raspberry Pi and Jetson Nano.
- Integrate with CCTV systems for large-scale monitoring.

---

## Contributing
Contributions are welcome! Feel free to fork this repository and submit a pull request with your enhancements.

---

*Thank you for checking out this project! Feel free to leave a star if you find it helpful.*
