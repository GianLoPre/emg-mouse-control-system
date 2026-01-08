# emg-mouse-control-system
EMG-based mouse control system (Arduino + Python + AWS data layer)

# EMG-Based Mouse Control System

This project explores the design and implementation of an EMG-based human–computer interface for cursor control, with a focus on biomedical signal processing and system architecture.

## Problem Statement
Surface EMG signals are noisy, non-stationary biological signals that require proper acquisition, preprocessing and feature extraction to be used for control purposes.

The goal is to translate muscle activation patterns into reliable cursor movements while keeping low latency locally and ensuring reproducibility of experimental data.

## System Overview
The system follows an edge–cloud architecture:
- Real-time acquisition and control are performed locally for low latency and safety
- AWS is used as a structured data layer to store raw/processed signals, metadata and reports

## Architecture
- EMG sensors on antagonist forearm muscles
- Arduino for acquisition and serial streaming
- PC for processing and cursor control
- AWS S3 for data persistence

## Project Status
Currently in design and signal analysis phase.

