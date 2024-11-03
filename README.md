# Heart Rate Monitor - Signal Processing and Transmission Project

## Overview
This project focuses on developing a **connected heart rate monitor** using **photoplethysmography (PPG)**, a method for measuring the changes in blood volume in the microvascular bed of tissue. The monitor captures, processes, and transmits heart rate data, providing real-time insights into cardiovascular health. This README provides an outline of the key technical processes involved, including **signal detection, amplification, filtering, and digital processing**.

---

## Table of Contents
1. [Introduction](#introduction)
2. [Signal Processing](#signal-processing)
   - [Signal Detection and Amplification](#signal-detection-and-amplification)
   - [Noise Reduction and Filtering](#noise-reduction-and-filtering)
3. [Measurements and Health Indicators](#measurements-and-health-indicators)
   - [Heart Rate Measurement (BPM)](#heart-rate-measurement-bpm)
   - [Pulse Wave Velocity (PWV)](#pulse-wave-velocity-pwv)
   - [Perfusion Index (PI)](#perfusion-index-pi)
4. [Conclusion](#conclusion)
5. [Future Improvements](#future-improvements)

---

## Introduction
The goal of this project was to design a **connected heart rate monitor** that measures, processes, and analyzes heart rate data. The monitor's functionality relies on **PPG technology**: variations in blood flow produce changes in the intensity of light absorbed, which are detected by a photodiode sensor. The project encompasses several key components:

- **Analog Signal Detection and Amplification**
- **Analog-to-Digital Conversion**
- **Signal Filtering and Processing**
- **Data Transmission**

### Team
- **Students**: Yasmine Ramoul, Robin Antoine, Khadija Boudabous, Taha Bouzid
- **Supervisors**: O. Bernal, E. Peuch, H. Kaouach, H.C. Seat, G. Prigent

---

## Signal Processing

### Signal Detection and Amplification
The PPG signal is detected by a **photodiode sensor** that converts variations in light intensity into electrical signals. Key stages in this process include:

1. **Photodiode Characterization**: The SHF7070 photodiode specifications were analyzed to determine the optimal light wavelength and photocurrent parameters.
2. **Amplification Stages**: The signal is amplified through a series of stages to ensure that it is robust for processing. Each stage was carefully calibrated for sensitivity and frequency response, including:
   - **Differential Amplifiers**: To isolate the signal from background noise.
   - **Current-to-Voltage Conversion**: Using resistive feedback to improve signal integrity.

### Noise Reduction and Filtering
Given the susceptibility of PPG signals to noise, a **comprehensive filtering system** was developed:

- **Low-Pass Filters**: Used to isolate the low-frequency components (1-10 Hz) containing the heart rate signal.
- **Finite Impulse Response (FIR) and Infinite Impulse Response (IIR) Filters**: Various filter types were tested, including FIR with Hamming windows and IIR filters (Butterworth and Chebyshev), to find the best balance of computational efficiency and phase response.
- **Savitzky-Golay Filtering**: Applied to smooth the first derivative of the signal, making it easier to identify systolic and diastolic peaks without losing essential signal characteristics.

---

## Measurements and Health Indicators

### Heart Rate Measurement (BPM)
With the filtered PPG signal, the system calculates **Beats Per Minute (BPM)** by measuring the intervals between systolic peaks:

1. **Peak Detection**: Using MATLAB, a custom peak detection algorithm identified systolic peaks based on local maxima, allowing calculation of average periods between beats.
2. **Statistical Analysis**: To determine health conditions, statistical tests on BPM variability were performed. Patients with high standard deviation in BPM may exhibit arrhythmia, detected through hypothesis testing.

### Pulse Wave Velocity (PWV)
**PWV** was calculated to assess arterial stiffness, which correlates with cardiovascular health:

- **Calculation**: PWV was determined based on the time delay between systolic and diastolic peaks, using the formula:
  \[
  \text{PWV} = \frac{2 \cdot d_{\text{heart→finger}}}{\Delta T}
  \]
  where \( \Delta T \) is the average interval between peaks, and \( d_{\text{heart→finger}} \) is the distance from the heart to the fingertip.
- **Categorization**: PWV values were classified according to standard categories, allowing us to identify potential risks of hypertension.

### Perfusion Index (PI)
The **Perfusion Index** provides an indication of blood flow strength:

- **Formula**: PI is calculated using the AC and DC components of the PPG signal:
  \[
  PI = \frac{\text{AC}_{\text{TOP}} - \text{AC}_{\text{LOW}}}{\text{DC}} \times 100\%
  \]
- **Significance**: This index helps evaluate the strength of pulse signals, offering further health insights.

---

## Conclusion
Through this project, we successfully created a heart rate monitor capable of real-time signal acquisition, processing, and analysis. The **signal processing techniques** and **health metrics** implemented, including BPM, PWV, and PI, provide valuable insights into cardiovascular health. This project has deepened our understanding of both hardware design (sensor, amplification) and software processing (filtering, peak detection, statistical analysis).

---

## Future Improvements
While the current system provides a functional baseline for monitoring heart rate and related metrics, future enhancements could include:

- **Automated Signal Processing**: Optimizing code to make data extraction more seamless.
- **Advanced Filtering Techniques**: Implementing adaptive filters to improve signal clarity.
- **Enhanced Data Analysis**: Integrating machine learning models to detect health anomalies with higher accuracy.
- **Improved Portability and Usability**: Designing a more compact form factor for wearable applications.

---

This README serves as a summary of our work on the **Heart Rate Monitor Project**, reflecting our efforts to build a robust, reliable, and informative health-monitoring device using PPG technology.
