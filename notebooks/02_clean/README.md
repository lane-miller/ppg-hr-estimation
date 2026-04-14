# 02 — Data Cleaning

Investigates three methods for removing motion artifacts from preprocessed PPG using the ACC reference signal; none proved effective.

- Loads preprocessed windowed PPG and ACC data from notebook 01
- Implements NLMS adaptive filtering with ACC as the reference channel
- Validates NLMS on a synthetic signal (cardiac sine + artifact sine)
- Tests NLMS on real DaLiA data across subjects, windows, filter lengths, and step sizes — finds no noise suppression benefit and occasional signal degradation
- Decomposes PPG windows using Empirical Mode Decomposition (EMD) and inspects IMFs in time and frequency domains
- Builds a synthetic PPG generator using a 3-harmonic series based on published fingertip PPG spectral ratios 
- Computes normalized cross-correlation between real PPG windows and synthetic replicas at candidate HRs
- None of the three cleaning methods improved on working directly with the preprocessed PPG and ACC
