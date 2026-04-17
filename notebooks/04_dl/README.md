# 04 — Deep Learning HR Estimation

Trains a CNN+BiLSTM model to estimate heart rate from PPG and accelerometer windows, evaluated via leave-one-subject-out (LOSO) cross-validation on all 15 DaLiA subjects.

- Defines `PPGDataset`: concatenates PPG + 3-axis ACC into (N_WIN, 4) windows with normalized HR labels and previous-window HR as an auxiliary input
- Implements `PPGHeartRateModel`: two Conv1d+BN+ReLU+AvgPool blocks → bidirectional LSTM → global average pooling → late fusion of previous HR (with Gaussian noise + dropout during training) → dense head outputting normalized HR
- Training uses MAE loss in normalized [0,1] HR space with ReduceLROnPlateau scheduling and early stopping (patience 25)
- Previous-HR injection uses Gaussian noise (5 BPM std) and 10% dropout during training to prevent over-reliance
- Full LOSO evaluation: fresh model per fold, best weights checkpointed on validation MAE in BPM
- Overall LOSO MAE: **5.27 ± 1.93 BPM** (range 3.12–9.68 BPM)
- S5 and S6 are outliers (~9.4 and ~9.7 BPM) due to significantly higher mean HR distributions; excluding them gives 4.61 BPM
