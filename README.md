# Crowd Anomaly Detection with Synthetic Data
Thesis project exploring synthetic data generation and cross-dataset object detection using ASTNet to improve crowd anomaly detection in real-world surveillance scenarios.


This repository contains the experiments developed for my thesis on crowd anomaly detection using synthetic data.

The experiments are based on the ASTNet detector.

Base detector implementation:
https://github.com/marco-caruso/astnet

The pretrained model checkpoints used in the experiments are available at the following link:
https://drive.google.com/drive/folders/1DPkrXN5gMHFswe7lUv7VB_tgj7VedPeS?usp=drive_link

These `.pth` files contain the trained weights for the models used in the experiments.
The models correspond to the configurations listed below:
- training_ped2: training with 100% ped2
- training_ped2_synth: training with 50% ped2 / 50% synthetic (manual selection)
- training_ped2_synth_random: training with 50% ped2 / 50% synthetic (random selection)
- training_ped2_synth_2: training with 75% ped2 / 25% synthetic (manual selection)
- training_ped2_synth_2_random: training with 75% ped2 / 25% synthetic (random selection)
- training_ped2_synth_3: training with 90% ped2 / 10% synthetic (manual selection)
- training_ped2_synth_3_random: training with 90% ped2 / 10% synthetic (random selection)
-
Link to the synthetic dataset created_
https://drive.google.com/drive/folders/1kc7W18yDGC11MskBfprX4YQMBns6bIou?usp=drive_link

dataset structure:

synthetic_dataset/


├── anomalous/

├── normal/

└── README.txt

---

## Repository structure

experiments/ → notebooks and scripts used for experiments

results/ → evaluation results and figures

ASTNet fork → training and inference code
