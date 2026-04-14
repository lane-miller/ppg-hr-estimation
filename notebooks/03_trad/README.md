# 03 — Traditional DSP HR Estimation

Implements a classical frequency-domain heart rate estimator using spectral peak selection with ACC-based penalty, and evaluates it on the full DaLiA dataset.


- Implements `hr_est_spectral`: an FFT-based HR estimator with SNR gating, physiological range masking, previous-HR tracking constraint, top-N peak selection, and per-channel ACC spectral penalty
- Runs a parameter sweep (hr_delta, SNR threshold, number of peaks, penalty factor) over 250 random chronological trial chunks
- Evaluates best parameters on the full dataset — achieves an overall MAE of 19.24 BPM
- Performance is poor: algorithm tends to underestimate HR or latch onto previous estimates, and FFT bin resolution at 32 Hz / 8 s imposes a 7.5 BPM quantization floor
