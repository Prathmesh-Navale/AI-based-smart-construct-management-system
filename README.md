# Construction Safety AI System

## Overview

The Construction Safety AI System is an advanced AI-powered solution designed to monitor and improve safety compliance on construction sites. It uses computer vision and machine learning to detect whether workers are following safety protocols such as wearing PPE (Personal Protective Equipment) and maintaining safe behavior in real time.

---

## Features

* Real-time safety monitoring using CCTV/webcam
* PPE detection:

  * Helmet
  * Safety Vest
  * Gloves
  * Safety Shoes
* Unsafe behavior detection (optional extension)
* Live alerts for safety violations
* Bounding box visualization with labels
* Scalable for multiple camera feeds

---

## Tech Stack

* Python 3.9+
* OpenCV
* YOLOv8 (Ultralytics)
* PyTorch
* NumPy
* FastAPI (for API deployment)

---

## Architecture

1. Video input from camera/CCTV
2. Frame extraction
3. Preprocessing
4. YOLO model inference
5. Detection of PPE / violations
6. Alert generation (if violation detected)
7. Display or send results to dashboard/API

---

## Project Structure

```
project/
│
├── dataset/
│   ├── images/
│   ├── labels/
│   ├── data.yaml
│
├── models/
│   ├── best.pt
│
├── src/
│   ├── train.py
│   ├── detect.py
│   ├── alert.py
│   ├── utils.py
│
├── api/
│   ├── main.py
│
├── runs/
│   ├── train/
│
├── requirements.txt
└── README.md
```

---

## Dataset

* Custom annotated dataset in YOLO format
* Classes include:

  * helmet
  * vest
  * gloves
  * shoes
  * no_helmet (optional)
  * no_vest (optional)

---

## Installation

```bash
git clone <repo-url>
cd project
pip install -r requirements.txt
```

---

## Training the Model

```bash
yolo detect train \
  data=dataset/data.yaml \
  model=yolov8n.pt \
  epochs=50 \
  imgsz=640
```

---

## Running the System

```bash
python src/detect.py
```

Using webcam:

```bash
yolo detect predict model=models/best.pt source=0
```

---

## Alert System (Optional)

* Trigger alert if PPE missing
* Options:

  * Sound alarm (buzzer)
  * Send notification (API)
  * Log violation data

---

## Challenges Faced

* Incorrect detection due to poor annotations
* Class imbalance in dataset
* Real-time performance optimization
* False positives in complex backgrounds

---

## Solutions

* Cleaned and validated dataset annotations
* Balanced dataset with augmentation
* Optimized confidence and IoU thresholds
* Used smaller YOLO models for faster inference

---

## Results

* Improved detection accuracy
* Real-time processing capability
* Reliable PPE compliance monitoring

---

## Future Improvements

* Multi-camera tracking system
* Worker identification (face recognition)
* Dashboard for analytics and reports
* Edge deployment (Jetson Nano / Raspberry Pi)

---

## Author

Prathmesh Navale

* Portfolio: [https://prathmeshportfolio-peach.vercel.app/](https://prathmeshportfolio-peach.vercel.app/)
* LinkedIn: [https://www.linkedin.com/in/navaleprathmesh/](https://www.linkedin.com/in/navaleprathmesh/)
