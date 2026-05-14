# Galaxeye-change-detection
# EO/SAR Change Detection for Satellite Imagery

Lightweight deep learning pipeline for EO/SAR satellite image change detection using semantic segmentation techniques. This project was developed as part of the GalaxEye Space AI Research Intern Technical Assessment.

---

## Overview

The objective of this project is to detect structural and environmental changes between pre-event and post-event satellite imagery using a lightweight semantic segmentation architecture.

The pipeline uses:

- U-Net segmentation architecture
- MobileNetV2 encoder backbone
- Binary semantic segmentation
- EO/SAR image fusion
- Mixed precision training for memory optimization

The implementation focuses on computational efficiency and reproducibility under constrained cloud GPU environments.

---

## Problem Statement

Given:
- Pre-event satellite imagery
- Post-event satellite imagery

The goal is to:
- Identify regions of change
- Generate binary segmentation masks representing changed and unchanged areas

This problem is highly relevant for:
- disaster assessment
- infrastructure monitoring
- environmental analysis
- remote sensing applications

---

## Dataset Structure

The dataset contains:

```text
train/
    pre/
    post/
    target/

val/
    pre/
    post/
    target/

test/
    pre/
    post/
    target/

Where:

pre/ contains pre-event imagery
post/ contains post-event imagery
target/ contains segmentation masks
Methodology
Preprocessing
Raster data loading using Rasterio
Min-max normalization
Channel-wise concatenation of pre/post imagery
Binary label remapping
Image resizing to 128×128
Model Architecture
U-Net decoder
MobileNetV2 encoder
Binary segmentation output
Training Strategy
PyTorch-based implementation
BCE + Dice Loss combination
Mixed precision training
Lightweight memory-efficient setup
Architecture
Encoder: MobileNetV2
Decoder: U-Net
Framework: PyTorch
Segmentation Library: segmentation-models-pytorch
Resource-Constrained Optimization

Due to cloud GPU memory and runtime limitations, experiments were conducted using a lightweight MobileNetV2-based U-Net architecture with mixed precision training and reduced spatial resolution (128×128) to prioritize end-to-end pipeline validation and reproducibility.

The following optimizations were applied:

Mixed precision training
Lightweight encoder backbone
Reduced batch size
Reduced image resolution
Memory-efficient evaluation workflow
Installation

Clone the repository:

git clone https://github.com/shafiqahmed-786/galaxeye-change-detection.git
cd galaxeye-change-detection

Install dependencies:

pip install -r requirements.txt
Training

Run the notebook:

Shafiq_Ahmed_GalaxEye.ipynb

The notebook contains:

preprocessing
dataset loading
training pipeline
evaluation workflow
visualization utilities
Evaluation Metrics

The following metrics were used:

IoU (Intersection over Union)
Precision
Recall
Challenges Encountered

Several engineering challenges were encountered during experimentation:

Large dataset transfer limitations
GPU memory exhaustion
Cloud runtime instability
Validation-time memory pressure

To address these constraints:

mixed precision training was enabled
lightweight architectures were adopted
image resolution was reduced
evaluation workflows were optimized
Future Improvements

Potential future enhancements include:

Higher resolution training
Attention-based segmentation
Advanced augmentations
Multi-scale feature fusion
Improved SAR preprocessing
Longer stable training schedules
Class imbalance optimization using focal loss
Repository Contents
README.md
requirements.txt
Shafiq_Ahmed_GalaxEye.ipynb
Shafiq_Ahmed_GalaxEye_Report.pdf
LICENSE
Author

Shafiq Ahmed Khan
Indian Institute of Information Technology Bhagalpur

License

This project is released under the MIT License.
