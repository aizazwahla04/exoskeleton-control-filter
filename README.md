**Adaptive Tremor Signal Filtering using Machine Learning**
## Project Overview

This project implements a machine-learning-based adaptive filtering system designed to separate voluntary motion from tremor signals in simulated biomedical movement data.In wearable robotics and assistive exoskeleton systems, tremor suppression requires distinguishing intended motion from high-frequency involuntary oscillations in real time. Instead of using a fixed filter cutoff frequency, this project trains a regression model to predict the optimal cutoff dynamically based on tremor characteristics such as frequency and amplitude. The resulting pipeline simulates the signal-processing decision layer of an adaptive tremor-suppression controller that could be used in rehabilitation devices, prosthetic stabilization systems, or upper-limb assistive exoskeletons.

The pipeline combines signal simulation, optimization-based label generation, SQL dataset logging, regression modeling, and statistical validation to demonstrate adaptive controller design in a reproducible workflow. This project explores whether a machine learning model can predict optimal filtering parameters automatically and improve motion reconstruction accuracy compared to static filtering approaches

**Motivation**

Physiological tremor typically occurs at higher frequencies than voluntary human motion. Traditional filtering methods rely on fixed cutoff frequencies, which cannot adapt to changes in tremor severity across users or conditions.

This project explores whether a machine learning model can predict optimal filtering parameters automatically and improve motion reconstruction accuracy compared to static filtering approaches.
**Project Motivation**

Tremor noise commonly affects biomedical signals such as:
	•	EMG recordings
	•	motion tracking signals
	•	prosthetic control signals
	•	rehabilitation sensors
	•	wearable biosignal systems

Traditional filtering uses fixed cutoff frequencies, which perform poorly when tremor characteristics vary between patients or over time.

This project explores:

Can machine learning automatically select an optimal filter cutoff frequency for tremor suppression?

**Project Pipeline**

The workflow follows a research-style signal processing architecture:
Signal simulation
      ↓
Optimal cutoff search via RMSE minimization
      ↓
5000 simulation trials stored in SQL database
      ↓
Dataset extraction from stored sessions
      ↓
Regression model training
      ↓
Adaptive cutoff prediction
      ↓
Static vs adaptive filtering comparison
      ↓
Statistical significance validation

**Signal Model**

The simulated signal contains:
Observed signal = intended motion + tremor noise

Where:
	•	intended motion frequency ≈ 1 Hz
	•	tremor frequency randomly sampled between 4–8 Hz
	•	tremor amplitude controlled by severity parameter

This produces realistic variability similar to physiological tremor conditions.

**Adaptive Filtering Strategy**

Instead of selecting a fixed cutoff frequency:
cutoff = constant

the system learns:
cutoff = f(severity, tremor_frequency)

Optimal cutoff values are computed using brute-force RMSE minimization and stored as training labels.

A regression model then predicts cutoff frequency for unseen signals

**Machine Learning Model**

Model used: Random Forest Regressor
Input features: 
tremor severity
tremor frequency

Target: optimal cutoff frequency

The model acts as an adaptive filtering controller.

**Database Integration**

Simulation sessions are stored in:SQLite database

Each trial records:
severity
tremor frequency
optimal cutoff

Total stored simulations: 5000 trials
This makes the dataset persistent and reproducible across runs.
RMSE after filtering

**Performance Evaluation**

Adaptive filtering performance is compared against a traditional static cutoff filter.

Metrics used:
Root Mean Square Error (RMSE)
paired t-test significance analysis
distribution comparison (boxplots)

Example result:
Static RMSE: 0.1176
Adaptive RMSE: 0.0352
Improvement: 70.05%
p-value: 9.2 × 10⁻¹³

The improvement is statistically significant.

**Visualization Outputs**

The notebook generates:
	•	signal overlay plots
	•	RMSE comparison curves
	•	RMSE distribution boxplots
	•	adaptive cutoff behavior plots

Example comparison:
Static filtering → increasing error with severity
Adaptive filtering → stable low error

**Example Adaptive Filtering Result**

The adaptive filtered signal closely matches intended motion despite strong tremor interference.
raw signal
true motion
adaptive filtered signal
are plotted together for comparison.

**Architecture diagram**

   Sensor signal -> ML cutoff predictor -> Adaptive filter -> Tremor estimate -> Potential actuator suppression signal

**Technologies Used**
Python
NumPy
SciPy
Matplotlib
Scikit-learn
SQLite

**Skills Demonstrated**

This project demonstrates:
digital signal processing
Butterworth filter design
adaptive controller logic
regression modeling
database integration
statistical hypothesis testing
simulation-based dataset generation
performance evaluation workflows

**Author**

Developed as part of an exploration into adaptive signal-processing methods for biomedical engineering applications.
