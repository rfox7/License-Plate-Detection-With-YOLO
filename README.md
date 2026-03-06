# License Plate Detection and Recognition using YOLO

## Team Members
- Rich Fox – rfox72@gmail.com


---

# Project Tier and Justification

**Project Tier:** Tier 1 
Tier 1 project was selected because I am running solo and wanted something I felt I could accomplish. 

**Justification:**  
This project implements a high-complexity two-stage computer vision pipeline: real-time object detection of small, localized targets (license plates) and subsequent Optical Character Recognition (OCR). By utilizing a state-of-the-art anchor-free model (YOLOv8) combined with a specialized OCR engine, the project addresses the technical challenges of detecting varying-scale objects at high speeds, fitting the criteria for a mid-to-high complexity implementation.

---

# Problem Statement

Traditional traffic monitoring, toll collection, and security systems are often crippled by manual inefficiencies and high latency, leading to significant labor costs and data entry errors. To modernize these industries, there is a critical need for a latency-sensitive, automated solution that can reliably detect and recognize license plates in real-time.  

This project solves the need for fast, efficient, and precise identification in high-volume environments where processing speed is as vital as accuracy.

---

# Solution Overview

The proposed system is an end-to-end deep learning pipeline designed for high-throughput license plate identification. It utilizes the **YOLOv8n (nano)** architecture for high-speed localization (Detection) and integrates the **EasyOCR** library for alphanumeric character extraction (Recognition).

By leveraging YOLOv8’s lightweight design, the system provides an optimal balance of low inference latency and precise recognition, making it ideal for edge deployment in traffic and security surveillance.

---

# Technical Approach

**CV Technique:**  
- Object Detection (localization)  
- Optical Character Recognition (text extraction)

**Model:**  
- **YOLOv8n (Nano variant from Ultralytics)** for the detection stage  
- **EasyOCR** (based on CRAFT and CRNN) for the recognition stage

**Framework:**  
- Python / PyTorch  
- Libraries: `ultralytics`, `EasyOCR`, `albumentations`

**Why this approach:**  
YOLOv8n is selected for its superior inference speed on low-end GPU systems and embedded hardware. Architecturally, it introduces a **Decoupled Head** (separating classification and regression) and a **Task-Aligned Assigner**, which significantly improves performance on small objects like license plates compared to previous versions.

The **anchor-free design** allows for more flexible bounding box predictions at varying angles. EasyOCR is chosen for its robust support for various fonts and lighting conditions found on international license plates.

---

# Dataset Information

**Source:** Multi-source Kaggle data pool including:

- "Automatic Number Plate Recognition"
- "Car number plate video"
- "License Plate Dataset"

**Size:**  
- This dataset contains 453 files. (1.06 G)

**Labels:**  
- License plate bounding boxes (YOLO format)  
- Alphanumeric character strings for the secondary recognition task

**Link:**  
- train_dir = "/kaggle/input/license-plate-dataset/archive/images/train"
- val_dir = "/kaggle/input/license-plate-dataset/archive/images/val"

---

# Success Metrics

**Primary Metric:**  
- **90%+ Detection Accuracy** measured at **mAP@0.5**  
  (Mean Average Precision at 0.5 Intersection over Union)

**Secondary Metrics:**  
- Real-time processing throughput (**30+ FPS**)  
- Low inference latency (**< 50ms per frame** for full pipeline)

---

# Week-by-Week Plan

| Week | Date | Tasks | Milestone |
|-----|-----|-----|-----|
| Week 10 | March 20 | Dataset acquisition from three sources; environment setup (Ultralytics & EasyOCR installation). | Dataset Ready |
| Week 11 | March 27 | Model training and fine-tuning using YOLOv8n; integration of the OCR recognition stage. | Model Working |
| Week 12 | April 3 | Testing, validation, and hyperparameter optimization for mAP@0.5 improvements. | High Accuracy Achieved |
| Week 13 | April 10 | Video processing implementation; multi-stage pipeline optimization and demo creation. | Demo Ready |
| Week 14 | April 17 | Final edge testing and comprehensive repository documentation. | Project Completion |
| Week 15 | April 24 | Final Presentation. | Presentation Delivered |

---

# Resources Needed

**Compute:**  
- Kaggle Kernels or Google Colab (Free Tier **T4 / P100 GPUs**)

**Tools:**  
- Ultralytics YOLOv8  
- EasyOCR  
- Python  
- Albumentations

**Cost:**  
- **$0** (open-source frameworks + free-tier cloud compute)

---

# Risks & Mitigation

| Risk | Probability | Mitigation |
|-----|-----|-----|
| Poor detection of small or angled plates from CCTV height | Medium | Utilize **albumentations** for Mosaic augmentation and Perspective transforms to simulate varied viewing angles. |
| High latency in the two-stage pipeline (Detection + OCR) | Medium | Optimize OCR by cropping only the license plate region and using **FP16 half-precision inference**. |
| Insufficient training data for specific regions | Low | Leverage the three distinct datasets identified in the source context for a more diverse training pool. |

---

# AI Usage Log & Current Status

## AI Usage Log
**March 2026:**  
Used AI for drafting the initial technical justification and refining the Markdown structure.

---

## Current Status

- [x] Repository created  
- [x] Proposal written  
- [ ] Dataset acquired  
- [ ] Model training started  
- [ ] Demo created  
- [ ] Final presentation ready
