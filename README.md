# 🚗 License Plate Detection and Recognition using YOLOv8

![Python](https://img.shields.io/badge/Python-3.10-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-DeepLearning-red)
![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

Real-time **License Plate Detection and Recognition** using **YOLOv8** for object detection and **EasyOCR** for optical character recognition.

---
# 👥 Team Members

| Name   | Email                                         |
| ------ | --------------------------------------------- |
| Rich Fox | [rfox72@gmail.com](mailto:rfox72@gmail.com) |
|  |  |
|  |  |

---


# 📌 Overview

Traditional traffic monitoring, toll collection, and security systems often rely on manual processes that introduce delays, labor costs, and human error.

This project builds an **end-to-end deep learning pipeline** capable of:

* Detecting license plates in images or video
* Extracting alphanumeric characters
* Operating in **near real-time environments**

The system is optimized for **high-speed inference and edge deployment**.

---

# 🧠 System Architecture

Pipeline workflow:

1️⃣ **Input Image / Video Frame**
2️⃣ **YOLOv8 Detection Model** → Detect license plate bounding box
3️⃣ **Region Cropping** → Extract plate region
4️⃣ **EasyOCR Recognition** → Convert plate image to text
5️⃣ **Output Result** → Plate number + bounding box visualization

```
Input Image
     │
     ▼
YOLOv8 Plate Detection
     │
     ▼
Crop Plate Region
     │
     ▼
EasyOCR Text Recognition
     │
     ▼
Detected License Plate Number
```

---

# 🛠 Technical Stack

| Component            | Technology            |
| -------------------- | --------------------- |
| Programming Language | Python                |
| Detection Model      | YOLOv8n               |
| OCR Engine           | EasyOCR               |
| Framework            | PyTorch               |
| Data Augmentation    | Albumentations        |
| Training Platform    | Google Colab / Kaggle |

---

# 📂 Dataset

Datasets sourced from Kaggle:

* Automatic Number Plate Recognition
* Car Number Plate Video Dataset
* License Plate Dataset

### Data Labels

* Bounding boxes in **YOLO format**
* Plate text for OCR validation

Example YOLO label format:

```
class x_center y_center width height
0 0.512 0.422 0.218 0.097
```

---

# 📊 Success Metrics

| Metric             | Target               |
| ------------------ | -------------------- |
| Detection Accuracy | **mAP@0.5 ≥ 90%**    |
| Processing Speed   | **≥ 30 FPS**         |
| Inference Latency  | **< 50ms per frame** |

---

# 📅 Project Timeline

| Week    | Date   | Task                                    | Milestone        |
| ------- | ------ | --------------------------------------- | ---------------- |
| Week 10 | Oct 30 | Dataset acquisition + environment setup | Dataset Ready    |
| Week 11 | Nov 6  | YOLOv8 training + OCR integration       | Model Working    |
| Week 12 | Nov 13 | Testing + hyperparameter tuning         | High Accuracy    |
| Week 13 | Nov 20 | Video pipeline + optimization           | Demo Ready       |
| Week 14 | Nov 27 | Documentation + final testing           | Project Complete |
| Week 15 | Dec 4  | Final presentation                      | Delivered        |

---

# ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/license-plate-detection-yolov8.git
cd license-plate-detection-yolov8
```

Install dependencies:

```bash
pip install ultralytics
pip install easyocr
pip install albumentations
pip install opencv-python
```

---

# 🚀 Training the Model

Train YOLOv8 on the dataset:

```bash
yolo detect train \
data=data.yaml \
model=yolov8n.pt \
epochs=50 \
imgsz=640
```

---

# 🔍 Running Inference

Run detection on an image:

```python
from ultralytics import YOLO
import easyocr
import cv2

model = YOLO("best.pt")
reader = easyocr.Reader(['en'])

results = model("car.jpg")

for r in results:
    for box in r.boxes.xyxy:
        x1, y1, x2, y2 = map(int, box)
        plate = img[y1:y2, x1:x2]
        text = reader.readtext(plate)
        print(text)
```

---

# 🎥 Demo

Example output:

```
Detected Plate: ABC1234
Confidence: 0.94
```

Future demo will include:

* Real-time webcam detection
* Video traffic analysis

---

# ⚠️ Risks & Mitigation

| Risk                       | Probability | Mitigation                             |
| -------------------------- | ----------- | -------------------------------------- |
| Small or angled plates     | Medium      | Use mosaic + perspective augmentation  |
| Two-stage pipeline latency | Medium      | Crop plate before OCR + FP16 inference |
| Dataset imbalance          | Low         | Combine multiple datasets              |

---

# 🤖 AI Usage Log

March 2026
AI assistance used for:

* Drafting proposal structure
* Formatting Markdown documentation
* Technical editing

---

# 📌 Project Status

* [x] Repository created
* [x] Proposal written
* [ ] Dataset acquired
* [ ] Model training started
* [ ] Demo created
* [ ] Final presentation ready

---

# 📜 License

This project is licensed under the **MIT License**.
