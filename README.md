# 🌳 Performance Analysis of Deep Learning Object Detection Models on UAV Imagery: YTU Davutpaşa Campus Case Study

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=flat-square&logo=python)
![Ultralytics](https://img.shields.io/badge/Ultralytics-YOLO-00FFFF?style=flat-square)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-EE4C2C?style=flat-square&logo=pytorch)
![Domain](https://img.shields.io/badge/Domain-Geomatics%20%26%20Remote%20Sensing-green?style=flat-square)

This repository contains the official dataset preparation pipeline, model training configs, and performance benchmark results for the Senior Graduation Thesis conducted at **Yıldız Technical University (YTU), Department of Geomatics Engineering**.

---

## 📌 Project Overview

Automated tree crown detection from high-resolution Unmanned Aerial Vehicle (UAV/Drone) imagery plays a vital role in urban forestry, green area inventory mapping, and ecological monitoring.

In this study, high-resolution aerial imagery ($6240 \times 4168$ pixels, ~26 MP) acquired over **YTU Davutpaşa Campus** was processed using a 50% overlapping sliding window crop technique to overcome hardware limitations and small object degradation. Five state-of-the-art YOLO architecture variants (**YOLO11s, YOLO11m, YOLO12s, YOLO12m, YOLO26m**) were benchmarked under identical hyperparameter setups.

### Key Highlights:
* **High-Resolution Dataset:** 496 high-resolution UAV images covering YTU Davutpaşa Campus annotated via Supervisely.
* **Sliding Window / Overlap Crop:** Applied $640 \times 640$ window size with a stride of 320px (50% overlap) to preserve spatial features of small tree crowns.
* **Comparative Benchmark:** Evaluated across Precision, Recall, F1-score, mAP@0.5, Matched Mean IoU, and Fitness (mAP@0.5:0.95).

---

## 📊 Benchmark & Test Set Performance Results

Evaluation on the independent test set (2,295 ground truth tree crowns):

| Rank | Model Architecture | Precision | Recall | F1-Score | mAP@0.5 | Matched Mean IoU | **Fitness (mAP@0.5:0.95)** |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 🥇 | **YOLO12s** | **0.742** | **0.748** | **0.745** | **0.771** | **0.844** | **0.515** |
| 🥈 | **YOLO11m** | 0.736 | 0.759 | 0.747 | **0.776** | 0.840 | **0.510** |
| 🥉 | **YOLO26m** | 0.732 | 0.682 | 0.706 | 0.747 | 0.826 | **0.474** |
| 4 | **YOLO11s** | 0.692 | 0.726 | 0.709 | 0.716 | 0.813 | **0.420** |
| 5 | **YOLO12m** | 0.599 | 0.627 | 0.612 | 0.566 | 0.774 | **0.278** |

* **Top Performing Model:** `YOLO12s` achieved the highest Fitness score (**0.515**) with the lowest False Negative count (396 missed trees).
* **Key Finding:** Increasing model capacity does not always guarantee performance gain on ultra-high-resolution spatial datasets (e.g., YOLO12s significantly outperformed YOLO12m).

---

## ⚙️ Preprocessing & Training Parameters

* **Input Image Resolution:** $640 \times 640$ pixels
* **Overlap Crop Strategy:** $P_w = 640$, $S = 320$ (50% Overlap)
* **Epochs:** 100
* **Batch Size:** 4
* **Optimizer:** Auto (SGD / Adam) with Initial LR $0.01$
* **Augmentations:** Mosaic ($1.0$), HSV-Hue ($0.015$), HSV-Sat ($0.7$), Translation ($0.1$), Scale ($0.5$), Random Erasing ($0.4$).

---

## 👥 Authors & Acknowledgments

* **Emirhan Yonar** — *Department of Geomatics Engineering, YTU*
* **Yaren Sude Orhan** — *Department of Geomatics Engineering, YTU*
* **Advisor:** Doç. Dr. A. Melis UZAR

*Special thanks to Arş. Gör. Dr. Onur Can BAYRAK for technical guidance.*

---
