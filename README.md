# DualFracNet: Bone Fracture Detection from X-ray Images

> **This research was accepted and presented at the 5th IEEE International Conference on Biomedical Engineering, Computer and Information Technology for Health (IEEE BECITHCON 2026).**

## Overview

DualFracNet is a hybrid deep learning framework for bone fracture detection from X-ray images. The proposed model combines convolutional, transformer-based, and attention-based feature extraction to capture complementary visual representations.

## Dataset

### MURA Dataset

**MURA (Musculoskeletal Radiographs)** is the primary dataset used in this research.

- 40,561 X-ray images
- 14,863 studies
- 12,173 patients
- 7 musculoskeletal study types
- Binary classification: Normal / Abnormal

**Dataset:** https://www.kaggle.com/datasets/cjinny/mura-v11

### External Dataset

An external dataset containing **506 X-ray images** was used for zero-shot evaluation.

**Dataset:** https://www.kaggle.com/datasets/bmadushanirodrigo/fracture-multi-region-x-ray-data

## Baseline Models

The following models were evaluated for comparison:

- DenseNet
- MobileNetV3
- ConvNeXt-Tiny

## Proposed Architecture

### DualFracNet

DualFracNet combines:

- **EfficientNetV2-S** — CNN-based feature extraction
- **Swin Transformer Tiny** — hierarchical and global feature representation
- **CBAM** — channel and spatial attention-based feature refinement

### Architecture

```text
                     Input X-ray Image
                              │
               ┌──────────────┴──────────────┐
               │                             │
               ▼                             ▼
        EfficientNetV2-S              Swin Transformer Tiny
               │                             │
               ▼                             ▼
        CNN Feature Maps             Transformer Features
               │                             │
               └──────────────┬──────────────┘
                              │
                              ▼
                             CBAM
                              │
                              ▼
                    Feature Refinement
                              │
                              ▼
                       Classification
                              │
                              ▼
                    Normal / Abnormal
