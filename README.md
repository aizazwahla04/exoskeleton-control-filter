# exoskeleton-control-filter
# Tremor Suppression Control Simulation

## Project Overview
This project simulates the control logic for a tremor-suppression exoskeleton designed to assist patients with Parkinson's Disease. It models the separation of low-frequency intended motion (0.5 Hz) from high-frequency tremor noise (4-6 Hz) to validate the effectiveness of digital filtering before hardware implementation.

## Key Features
* **Signal Modeling:** Generates synthetic data representing hand motion overlaid with Parkinsonian tremors and sensor noise.
* **Digital Filtering:** Implements a 2nd-order Butterworth Low-Pass Filter (3Hz Cutoff).
* **Zero-Phase Validation:** Uses `filtfilt` to eliminate phase lag for accurate performance benchmarking.
* **Performance Metrics:** Calculates RMSE (Root Mean Square Error) reduction to quantify stability improvements.

## Results
The simulation demonstrates a **tremor reduction of >90%** using the optimized filter parameters.


## Tech Stack
* Python (NumPy, SciPy, Matplotlib)e filtering.
