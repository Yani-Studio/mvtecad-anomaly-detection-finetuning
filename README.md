# MVTecAD Anomaly Detection & Finetuning Pipeline

An end-to-end computer vision pipeline for industrial anomaly detection, finetuned on the **MVTec AD (Anomaly Detection)** dataset. This repository delivers a high-performance framework focusing on unsupervised defect localization and classification across various manufacturing categories.

---

## 🎬 Live Demos (Defect Localization Showcase)
| Cable Anomaly Detection | Grid Anomaly Detection | Metal Nut Anomaly Detection |
| :---: | :---: | :---: |
| <img src="Visualization/CABLE_Analysis/cable_final.gif" width="260"/> | <img src="Visualization/GRID_Analysis/grid_final.gif" width="260"/> | <img src="Visualization/METAL_NUT_Analysis/metal_nut_final.gif" width="260"/> |

---

## 📊 Performance & Optimization Analysis

### 1. Global Benchmarking Performance
| Seq | Component Category | EfficientAd AUROC | Patchcore AUROC | Optimal Architecture Selection | Status |
| :---: | :--- | :---: | :---: | :---: | :---: |
| 1 | **Transistor** | **99.79%** | 99.37% | **EfficientAd** | Best Model Restored ✅ |
| 2 | **Cable** | 89.11% | **98.88%** | **Patchcore** | Best Model Restored ✅ |
| 3 | **Screw** | 95.55% | **96.76%** | **Patchcore** | Best Model Restored ✅ |
| 4 | **Metal Nut** | 99.46% | **99.80%** | **Patchcore** | Best Model Restored ✅ |
| 5 | **Grid** | **100.00%** | 98.91% | **EfficientAd** | Best Model Restored ✅ |

> ⚠️ **Note on Category Exclusion:** Transistor and Screw categories encountered performance anomalies or technical degradation during the unsupervised anomaly detection baseline pipeline execution. Consequently, they were intentionally excluded from the subsequent detailed pixel-level visualization analysis and decision threshold finetuning phases.

---

### 2. Cable Component Performance Table

#### A. Anomaly Score Distribution & PR Curve
<img src="Visualization/CABLE_Analysis/Score_Distribution_CABLE_PR_Curve_CABLE.png" width="600"/>

#### B. Confusion Matrix Optimization (Side-by-Side Comparison)
| Default Model (Before Finetuning) | Optimized Threshold (After Finetuning - 0.5113) |
| :---: | :---: |
| <img src="Visualization/CABLE_Analysis/Confusion_Matrix_CABLE_Default.png" width="380"/> | <img src="Visualization/CABLE_Analysis/Confusion_Matrix_CABLE_(Threshold_0.5113).png" width="380"/> |

#### C. Failure Cases Identification
<img src="Visualization/CABLE_Analysis/Failure_Cases_CABLE.png" width="600"/>

---

### 3. Grid Component Performance Table

#### A. Anomaly Score Distribution & PR Curve
<img src="Visualization/GRID_Analysis/Score_Distribution_GRID_PR_Curve_GRID.png" width="600"/>

#### B. Confusion Matrix Optimization (Side-by-Side Comparison)
| Default Model (Before Finetuning) | Optimized Threshold (After Finetuning - 0.3363) |
| :---: | :---: |
| <img src="Visualization/GRID_Analysis/Confusion_Matrix_GRID_Default.png" width="380"/> | <img src="Visualization/GRID_Analysis/Confusion_Matrix_GRID_(Threshold_0.3363).png" width="380"/> |

*(Note: Grid achieved 100.00% AUROC post-optimization, resulting in zero failure cases.)*

---

### 4. Metal Nut Component Performance Table

#### A. Anomaly Score Distribution & PR Curve
<img src="Visualization/METAL_NUT_Analysis/Score_Distribution_METAL_NUT_PR_Curve_METAL_NUT.png" width="600"/>

#### B. Confusion Matrix Optimization (Side-by-Side Comparison)
| Default Model (Before Finetuning) | Optimized Threshold (After Finetuning - 0.5115) |
| :---: | :---: |
| <img src="Visualization/METAL_NUT_Analysis/Confusion_Matrix_METAL_NUT_Default.png" width="380"/> | <img src="Visualization/METAL_NUT_Analysis/Confusion_Matrix_METAL_NUT_(Threshold_0.5115).png" width="380"/> |

#### C. Failure Cases Identification
<img src="Visualization/METAL_NUT_Analysis/Failure_Cases_METAL_NUT.png" width="600"/>

---

## 🚀 Project Overview & Core Features
This project provides a robust multi-model industrial inspection framework powered by **Anomalib**. It automates the discovery of subtle structural and surface anomalies without requiring extensive anomalous training samples, relying purely on normal data profiles for self-supervised learning.

### 🔍 Key Pipeline Architecture
- **Multi-Model Benchmarking:** Parallel training and evaluation of **EfficientAd** (optimized for rapid inference and lightweight edge deployment) and **Patchcore** (memory-bank based architecture leveraging a Wide-ResNet50 backbone for superior pixel-level localization).
- **Dynamic Checkpoint Pruning:** Implements an automated weight management module that sweeps through candidate models, benchmarks final AUROC metrics, selects the best-performing weights, and prunes suboptimal checkpoints to preserve deployment storage.
- **Hardware & Memory Optimization:** Fully optimized for Apple Silicon configurations using PyTorch's **MPS (Metal Performance Shaders)** backend, paired with proactive garbage collection (`gc.collect()`) to prevent memory leaks during high-resolution processing.

---

## 🏭 Industrial Applications & Domain Use Cases

The unsupervised anomaly detection and pixel-level localization models developed in this project directly address critical challenges in smart factory implementations and automated manufacturing quality control.

### 1. Precision Metal Machining & Mechanical Assembly (Metal Nut, Screw)
- **Automated Quality Control (QC):** Deployed in automotive engine component lines, aerospace assembly, and heavy machinery manufacturing to inspect fasteners (bolts, nuts, screws). It automatically captures surface cracks, thread wear, and deformation, preventing critical structural failures before final product deployment.
- **Assembly Verification Systems:** Integrates into robotic pick-and-place lines to run real-time checks on whether sub-millimeter components are correctly seated and tightened, maintaining high process reliability.

### 2. Semiconductor Packaging & High-Tech Electronics (Transistor, Grid)
- **Surface Mount Technology (SMT) Inspection:** Applied during post-packaging stages to identify micro-soldering faults (voids, bridges) and component misalignments on lead frames or transistors.
- **Pattern & Mesh Filter Inspection:** Inspects fine mesh structures and complex grid patterns on printed circuit boards (PCBs) to isolate trace disconnections, warping, or microscopic foreign object debris (FOD) via high-precision anomaly heatmaps.

### 3. Continuous Infrastructure & High-Reliability Wiring (Cable)
- **Extrusion Line Monitoring:** Monitors continuous manufacturing processes for power cables, wiring harnesses, and fiber optics. The system captures insulation jacket tears, punctures, or diameter irregularities in real-time, allowing immediate automated line halts to minimize raw material waste.
- **Predictive Infrastructure Maintenance:** Automates the inspection of exposed factory power lines and network trunks, tracing structural degradation or physical geometric changes over time to prevent sudden short circuits or industrial fires.

---

## 📋 Dataset Credits & Attribution
- **Original Dataset Creator:** **MVTec Software GmbH** (Paul Bergmann, Michael Fauser, David Sattlegger, Carsten Steger).
- **Dataset Focus:** Benchmark dataset designed specifically for unsupervised anomaly detection and pixel-precise defect segmentation in real-world industrial quality inspection.
- **Data Source Download:** You can download the dataset directly from the official repository or access public mirrors via Kaggle:
  - 🔗 **Official Source:** [MVTec AD Dataset Website](https://www.mvtec.com/research-teaching/datasets/mvtec-ad)
  - 🔗 **Kaggle Link:** [MVTec Defect Detection Dataset on Kaggle](https://www.kaggle.com/datasets/avdvhh/mvtec-defect-detection-dataset)

---

## 🛠️ Repository Structure
```text
.
├── Visualization/
│   ├── CABLE_Analysis/
│   ├── GRID_Analysis/
│   └── METAL_NUT_Analysis/
└── run.ipynb (Core Pipeline & Benchmarking Notebook)
