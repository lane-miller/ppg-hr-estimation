# 00 — Exploratory Data Analysis

Initial exploration of the PPG-DaLiA dataset for a single subject. Covers data loading, signal inspection, and preprocessing design used later in classical and deep learning notebooks

## Contents

- Load and inspect subject `.pkl` file structure
- Plot ECG-derived ground truth HR
- Plot raw PPG (BVP) and 3-axis accelerometer signals
- Preprocessing:
  - Sample rate matching: PPG decimated from 64 Hz → 32 Hz, ACC from 32 Hz → 32 Hz (no change, but decimation still applied in case anti-alias filter not zero phase)
  - Bandpass filter: 4th order Butterworth, 0.4–4.0 Hz (24–240 BPM), zero-phase via `sosfiltfilt`
  - Standardization: z-score per channel

## Dataset

PPG-DaLiA — 15 subjects
- wrist-worn PPG
- 3-axis accelerometer
- chest ECG ground truth (labels provided by dataset publishers)

Data lives at `/Volumes/LPM02 storage/Datasets/Bio/DaLiA/data/SX/SX.pkl` and is never committed to repo.

**Reference:** Reiss et al., "Deep PPG: Large-Scale Heart Rate Estimation with Convolutional Neural Networks," MDPI Sensors, 2019.