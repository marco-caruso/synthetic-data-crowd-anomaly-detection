# Crowd Anomaly Detection with Synthetic Data

This repository contains the experiments developed for the thesis project:

**"Synthetic Data Augmentation for Crowd Anomaly Detection"**

The project investigates the impact of **synthetic crowd data** on the performance and generalization capability of anomaly detection models in surveillance scenarios.

The experiments are conducted using the **ASTNet (Attention-based Spatio-Temporal Network)** architecture.

---

# Project Overview

Crowd Anomaly Detection (CAD) aims to automatically identify abnormal events in surveillance videos involving groups of people.

A major limitation of current CAD systems is the **lack of large and diverse datasets**, especially for modeling normal crowd behavior.

This project proposes the use of **synthetic crowd videos generated using diffusion models** to augment the training dataset and improve model robustness.

The experiments analyze how different combinations of **real and synthetic data** affect anomaly detection performance.

---

# Datasets

The experiments use three datasets.

### Ped2 Dataset
Used for:

- training
- intra-dataset testing

Ped2 is a standard benchmark dataset for anomaly detection in surveillance videos.

The training set consists of 16 videos (2550 frames), while the test set consists of 12 videos (2010 frames).

---

### Synthetic Dataset

A synthetic dataset of crowd scenes was generated using the **WAN 2.2 diffusion model** through a multi-stage pipeline combining:

- **Text-to-Video generation**
- **Image-to-Video generation**

The synthetic dataset contains:

- normal crowd behavior
- controlled anomalous scenarios

Each video sequence contains 243 frames.

Due to size constraints, the dataset is **not included in this repository**.

Access is available to the research group upon request.

---

### MED Dataset

The MED dataset is used for **cross-dataset evaluation**.

It contains:

- 31 videos  
- approximately **45,000 frames**

This dataset is used to evaluate the **generalization capability** of the trained models.

---

# Training and Evaluation Protocol

The anomaly detection model follows a **one-class learning paradigm**.

Training is performed **only on normal sequences**.

### Training datasets

- Ped2 dataset
- Synthetic dataset

### Testing datasets

Two evaluation settings are considered:

**Intra-dataset evaluation**

Training on Ped2 (or Ped2 + synthetic data)  
Testing on Ped2

**Cross-dataset evaluation**

Training on Ped2 (or Ped2 + synthetic data)  
Testing on MED

The MED dataset is used to evaluate the **generalization capability of the model**.

---

# Experiments

Several training configurations were tested by varying the proportion of real and synthetic data.

| Training Configuration | Real Data | Synthetic Data |
|------------------------|-----------|---------------|
| Ped2 only (16 videos) | 100% | 0% |
| Synthetic only (114 videos) | 0% | 100% |
| 50/50 manual selection | 50% | 50% |
| 50/50 random selection | 50% | 50% |
| 75/25 manual selection | 75% | 25% |
| 75/25 random selection | 75% | 25% |
| 90/10 manual selection | 90% | 10% |
| 90/10 random selection | 90% | 10% |

Manual selection refers to a curated selection of synthetic videos, while random selection samples synthetic videos randomly.
The training configurations refer to the proportion of **frames**, not the number of videos.
---

# Experimental Results

## AUC Comparison

| Model | AUC Ped2 (%) | AUC MED (%) |
|------|-------------|-------------|
| Baseline (pre-trained) | 97.4 | 59.4 |
| Ped2 only | 97.0 | 69.4 |
| Synthetic only | 89.1 | 56.6 |
| 50/50 manual selection | 93.9 | 63.2 |
| 50/50 random selection | 95.0 | 61.3 |
| 75/25 manual selection | 93.9 | 64.8 |
| 75/25 random selection | 88.7 | 57.3 |
| 90/10 manual selection | 95.7 | **70.5** |
| 90/10 random selection | 96.8 | 66.4 |

The best cross-dataset performance on the MED dataset is obtained with the **90/10 manual selection configuration**, achieving **70.5% AUC**.

---

## Classification Metrics on MED Dataset

| Model | Accuracy | Precision | Recall | F1-score |
|------|---------|---------|--------|---------|
| Baseline (pre-trained) | 59.81% | 50.35% | 58.19% | 53.99% |
| Ped2 only | 65.01% | 56.24% | 61.59% | 58.79% |
| Synthetic only | 61.95% | 57.88% | 22.36% | 32.26% |
| 50/50 manual selection | 64.33% | 56.48% | 52.17% | 54.24% |
| 50/50 random selection | 64.36% | 57.47% | 46.29% | 51.28% |
| 75/25 manual selection | 64.82% | 55.99% | 61.59% | 58.66% |
| 75/25 random selection | 64.32% | 59.02% | 39.07% | 47.01% |
| 90/10 manual selection | **67.41%** | 59.71% | 60.18% | **59.94%** |
| 90/10 random selection | 64.97% | 56.80% | 56.65% | 56.72% |

---

# ROC Curve

The figure below shows the ROC curve obtained from the experimental evaluation on the MED dataset.

![ROC Curve](ROC_curve.png)



