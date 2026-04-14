# 01 — Preprocessing

Resamples, filters, and windows raw PPG and ACC signals from the DaLiA dataset for all 15 subjects, saving the result to disk.

- Loads raw PPG (64 Hz) and ACC (32 Hz) data per subject from pickle files
- Resamples PPG from 64 Hz to 32 Hz via `resample_poly`; ACC is already at 32 Hz
- Applies a 4th-order Butterworth bandpass filter (0.4–4.0 Hz) to both PPG and ACC
- Segments signals into 8-second windows (256 samples) with a 2-second stride (64 samples)
- Stores both BPF-only windows (for spectral analysis) and z-score normalized windows (for deep learning)
- Saves all windowed data and preprocessing parameters to a single pickle file
