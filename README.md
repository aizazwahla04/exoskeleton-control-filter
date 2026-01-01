Exoskeleton Control: AI-Optimized Bio-Signal Stabilization
Project Overview

This project simulates an active exoskeleton control system designed to stabilize hand tremors in patients with Parkinson’s disease. By integrating Digital Signal Processing (DSP), SQL Data Engineering, and Random Forest Machine Learning, I developed a system capable of predicting tremor suppression efficiency with 99% accuracy (R 
2
 =0.99).

Technical Architecture
1. Bio-Physics Simulation

To model a real-world scenario, I generated synthetic sensor data representing a patient's hand movement :


Intended Motion: A 0.5 Hz sine wave representing the user's voluntary movement.



Pathological Tremor: A 5.0 Hz high-frequency oscillation typical of Parkinsonian tremors .


Sensor Noise: Gaussian white noise to simulate electrical interference from hardware components.


2. Digital Signal Processing (DSP)

I implemented a 4th-order Butterworth Low-Pass Filter to isolate voluntary movement from involuntary tremors:

Zero-Phase Filtering: Utilized signal.filtfilt to eliminate phase lag, ensuring real-time exoskeleton responsiveness.


Validation: Performance was quantified using Root Mean Square Error (RMSE), comparing the filtered output against the target motion .


3. SQL-Backed Monte Carlo Simulation

To validate the system across a diverse range of patient conditions, I built an automated data pipeline :

Automated Trials: Executed a simulation of 5,000 trials, varying tremor severity and filter cutoff frequencies.


Data Persistence: Developed a SQLite database to store results, providing a structured dataset for machine learning analysis .

4. Machine Learning Optimization

I trained a Random Forest Regressor to analyze the system's behavior and predict optimal control settings :


Feature Engineering: Implemented interaction features (Severity × Cutoff) to enhance model depth.

Performance Metrics:

Mean Absolute Error (MAE): 0.17%.

R-Squared (R 
2
 ) Score: 0.99.

Feature Importance: The model identified Filter Cutoff Frequency as the primary driver of successful tremor suppression .

Key Results
Efficiency: Successfully reduced simulated tremor interference by over 90% in standard configurations.

Precision: Developed a predictive model with a margin of error of only 0.17%.

Discovery: Quantitatively proved that adaptive filter tuning is critical for maintaining performance across varying patient tremor profiles.
