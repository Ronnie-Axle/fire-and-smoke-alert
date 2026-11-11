This program is a Custom Fire and Smoke Detection System built using computer vision and deep learning.

Here is a breakdown of what the program accomplishes and how its components work together:

1. The Core Objective
The program trains and runs a custom artificial intelligence model using Ultralytics YOLOv8 (You Only Look Once, version 8). Instead of relying on generic object detection, it is specifically trained on your custom dataset (exported from Roboflow) to recognize and localize two distinct classes in real time: fire and smoke.   
Roboflow

2. Key Components of the Project
The Dataset (dataset/): Contains your training and validation images along with their bounding box annotations. The data.yaml configuration file acts as a map that tells the YOLO trainer where to find these image folders and defines your target classes (fire and smoke).

The Training Script (train.py):

Loads a pre-trained lightweight YOLOv8 model (yolov8n.pt) as a starting point (transfer learning).   
Roboflow

Feeds your custom fire and smoke images through the model across multiple passes (epochs) so it learns the visual patterns of flames and smoke.

Outputs the optimized weights file (best.pt), which represents your fully trained, custom detection brain.   
Medium

The Live Detection Script (detect.py):

Opens your computer's webcam using OpenCV (cv2.VideoCapture).

Captures live video frames and passes them through your custom model (best.pt) to scan for hazards.

Draws bounding boxes and confidence scores around any detected fire or smoke directly onto the video feed in real time.
