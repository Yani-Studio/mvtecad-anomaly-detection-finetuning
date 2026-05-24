<div align="center">

# 🛡️ MVTecAD Industrial Anomaly Detection
### High-Precision Computer Vision Pipeline for Quality Control

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-MPS_Backend-orange.svg)](https://pytorch.org/)
[![Hardware](https://img.shields.io/badge/Apple_Silicon-M5_Chip-lightgrey.svg)]()
[![Status](https://img.shields.io/badge/Training-Completed-brightgreen.svg)]()

*An end-to-end computer vision framework delivering sub-millimeter defect localization using self-supervised learning.*

</div>

---

## 🚀 Executive Summary
This repository houses a high-performance Anomaly Detection (AD) pipeline optimized for industrial environments. By leveraging **EfficientAd** and **Patchcore**, this project achieves near-perfect detection rates on the MVTec AD dataset.

### ⚙️ Training Infrastructure
* **Hardware:** MacBook Pro M5 (Base Chipset, 24GB RAM)
* **Optimization:** PyTorch MPS (Metal Performance Shaders) Backend
* **Training Duration:** 9 Days of continuous training
* **Convergence:** 999 Epochs per category

---

## 📊 Global Benchmarking
| Component Category | EfficientAd AUROC | Patchcore AUROC | Selection | Status |
| :--- | :---: | :---: | :---: | :--- |
| **Cable** | 89.11% | **98.88%** | **Patchcore** | ✅ Restored |
| **Metal Nut** | 99.46% | **99.80%** | **Patchcore** | ✅ Restored |
| **Grid** | **100.00%** | 98.91% | **EfficientAd** | ✅ Restored |

---

## 🔍 Detailed Analysis & Performance

### 1. Cable Component (Patchcore)
*Objective: Detect jacket tears and diameter irregularities.*

| Before Optimization | After Optimization (Threshold 0.5113) |
| :--- | :--- |
| <img src="Visualization/CABLE_Analysis/Confusion_Matrix_CABLE.png" width="300"/> | <img src="Visualization/CABLE_Analysis/Confusion_Matrix_CABLE_(Threshold_0.5113).png" width="300"/> |

#### 📈 Classification Report
| Class | Precision | Recall | F1-Score | Support |
| :--- | :--- | :--- | :--- | :--- |
| **Good** | 0.9655 | 0.9655 | 0.9655 | 58 |
| **Anomaly** | 0.9783 | 0.9783 | 0.9783 | 92 |
| **Accuracy** | | | **0.9733** | 150 |

---

### 2. Grid Component (EfficientAd)
*Objective: Identify trace disconnections and surface debris.*

| Before Optimization | After Optimization (Threshold 0.3363) |
| :--- | :--- |
| <img src="Visualization/GRID_Analysis/Confusion_Matrix_GRID.png" width="300"/> | <img src="Visualization/GRID_Analysis/Confusion_Matrix_GRID_(Threshold_0.3363).png" width="300"/> |

#### 📈 Classification Report
| Class | Precision | Recall | F1-Score | Support |
| :--- | :--- | :--- | :--- | :--- |
| **Good** | 1.0000 | 1.0000 | 1.0000 | 21 |
| **Anomaly** | 1.0000 | 1.0000 | 1.0000 | 57 |
| **Accuracy** | | | **1.0000** | 78 |

---

### 3. Metal Nut Component (Patchcore)
*Objective: Surface crack detection and assembly verification.*

| Before Optimization | After Optimization (Threshold 0.5115) |
| :--- | :--- |
| <img src="Visualization/METAL_NUT_Analysis/Confusion_Matrix_METAL_NUT.png" width="300"/> | <img src="Visualization/METAL_NUT_Analysis/Confusion_Matrix_METAL_NUT_(Threshold_0.5115).png" width="300"/> |

#### 📈 Classification Report
| Class | Precision | Recall | F1-Score | Support |
| :--- | :--- | :--- | :--- | :--- |
| **Good** | 0.9565 | 1.0000 | 0.9778 | 22 |
| **Anomaly** | 1.0000 | 0.9892 | 0.9946 | 93 |
| **Accuracy** | | | **0.9913** | 115 |

---

## 🏭 Industry Use-Cases
> 💡 **Quality Assurance Automation:** Our pipeline transforms raw pixel data into actionable quality insights, reducing manual inspection overhead by >90%.

* **Manufacturing QC:** Automated fastener and thread inspection (Metal Nut).
* **Electronics SMT:** High-precision PCB pattern analysis (Grid).
* **Continuous Extrusion:** Real-time monitoring for wiring infrastructure (Cable).

---

## 🛠️ How to Run
1. **Clone the repo:**
   ```bash
   git clone [https://github.com/YOUR_GITHUB_ID/mvtecad-anomaly-detection.git](https://github.com/YOUR_GITHUB_ID/mvtecad-anomaly-detection.git)
