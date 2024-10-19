# Enhancing Transportation Security: Automated Prohibited Object Detection for Baggage Inspection

## Overview

This repository contains the code and methodology for developing an automated system for prohibited object detection in X-ray images. Our system leverages **YOLO-NAS** to enhance security and expedite baggage inspections at transportation hubs like airports and subway stations. The model was trained and evaluated using the **SIXray** dataset, achieving a **mean Average Precision (mAP)** of **0.924**, outperforming its predecessor YOLOv8 by 12%.

---

## ![Visual of Detected Threat Items in X-ray Images](path/to/image.jpg)

*Sample images from the SIXray dataset demonstrating detected prohibited items such as guns and knives.*

---

## Published Paper

**[Enhancing Transportation Security: Automated Prohibited Object Detection - IEEE ICCCIS 2023](https://yourpaperlink.com)**

---

## Table of Contents

- [Introduction](#introduction)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Experiment Analysis](#experiment-analysis)
- [Results and Discussion](#results-and-discussion)
- [Conclusion](#conclusion)
- [Link to the Published Paper](#link-to-the-published-paper)

---

## Introduction

The increase in human traffic across transportation sectors has necessitated a faster and more reliable baggage inspection system. Traditional manual inspections are prone to errors and cause delays at checkpoints. To tackle this, we developed a real-time prohibited object detection system using **YOLO-NAS** (You Only Look Once – Neural Architecture Search).

---

## Dataset

We used the **SIXray dataset**, consisting of over **1,059,231 X-ray images** sourced from subway stations. These images are annotated for six prohibited item categories: **guns, knives, wrenches, pliers, hammers, and scissors**.

Here’s a breakdown of the dataset distribution:

![Class Distribution in SIXray Dataset](path/to/class-distribution-image.jpg)

*Figure: Distribution of prohibited objects across six classes.*

For the experiment, we split the dataset using a **70-10-20 ratio** for training, validation, and testing, respectively.

---

## Methodology

Our system is built upon **YOLO-NAS**, an advanced real-time object detection model known for its balance between precision, speed, and computational efficiency. The architecture consists of:

- **Backbone**: Extracts features using Quantization-Aware RepVGG blocks.
- **Neck**: Merges and adjusts features at different scales for better representation.
- **Head**: Detects objects at varying scales.

Below is a schematic of the YOLO-NAS architecture used:

![YOLO-NAS Architecture](path/to/yolo-nas-architecture.jpg)

*Figure: YOLO-NAS architecture showing the Backbone, Neck, and Head components.*

We trained the YOLO-NAS-l (large) model using a **NVIDIA Tesla P100 GPU** for **50 epochs**, utilizing techniques such as **Quantization-Aware Training (QAT)** to optimize the model for edge computing.

### Loss and Metrics Progression

Below is the training progression, comparing key metrics such as **Precision, Recall**, and **mAP50** for YOLO-NAS and YOLOv8:

![Training Metrics Comparison](path/to/training-metrics-comparison.jpg)

*Figure: Comparison of Precision, Recall, and mAP between YOLO-NAS and YOLOv8 models.*

---

## Experiment Analysis

In our experiment, we compared YOLO-NAS against YOLOv8 using the same environment and dataset. We observed a **12% improvement** in mAP with YOLO-NAS, which achieved an mAP of **0.924**. The hyperparameters used for YOLO-NAS include a **cosine annealing learning rate** with **Adam optimizer**.

- **Training Time**: YOLO-NAS: 13.4 hours | YOLOv8: 4.5 hours
- **Input Image Size**: 640x640 pixels
- **Optimizer**: Adam with a weight decay of 0.0001

---

## Results and Discussion

### Sample Detection Results

![Sample Detection Results](path/to/detection-results.jpg)

*Figure: Detection results from the test dataset.*

Our model achieved the following class-specific mAP scores:

| Class    | mAP50 |
|----------|-------|
| Guns     | 0.981 |
| Knives   | 0.896 |
| Pliers   | 0.931 |
| Scissors | 0.912 |
| Wrenches | 0.882 |

The overall mAP of **0.924** surpasses the performance of YOLOv8 by a notable margin of **12%**.

---

## Conclusion

Our research demonstrates that **YOLO-NAS** can significantly improve the accuracy and speed of prohibited object detection in baggage inspections, reducing congestion at transportation hubs. In future work, we plan to explore **3D imaging** and **object segmentation** techniques to further enhance the detection process.

---

## Link to the Published Paper

**[Enhancing Transportation Security: Automated Prohibited Object Detection - IEEE ICCCIS 2023](https://yourpaperlink.com)**

---


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
