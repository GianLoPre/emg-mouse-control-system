# EMG Signal Notes (Design Rationale)

## What is EMG?
Surface EMG is the electrical activity produced by skeletal muscles, measured via electrodes on the skin. It is noisy, non-stationary, and highly dependent on electrode placement, skin impedance and motion artifacts.

## Why preprocessing is needed
Raw EMG cannot be used directly for control because it contains:
- motion artifacts and baseline drift (low frequencies)
- power-line interference (50 Hz in Europe)
- high-frequency noise

## Typical frequency content
Useful EMG content is roughly in the 20–450 Hz range (depending on setup). Sampling rate should be high enough to avoid aliasing.

## Standard preprocessing pipeline
1) Band-pass filter (e.g., 20–450 Hz)
2) Notch filter at 50 Hz (optional but often useful)
3) Rectification: abs(x)
4) Envelope extraction: low-pass filter of rectified signal OR RMS over a moving window

## Why envelope / RMS
Control needs a stable signal correlated with muscle activation intensity.
Envelope/RMS provides a smooth estimate of activation that is easier to map to cursor velocity.

## Why two antagonist muscles
Using antagonist muscles (e.g., forearm flexor vs extensor) enables differential control:
- bidirectional movement based on relative activation
- better robustness to fatigue and baseline drift vs single-threshold control
