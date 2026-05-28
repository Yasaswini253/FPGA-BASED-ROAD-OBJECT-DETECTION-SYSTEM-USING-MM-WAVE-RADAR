# FPGA-Based Road Object Detection and Classification System Using mmWave Radar for ADAS Applications

## Project Overview

This project presents an intelligent FPGA-based road object detection and classification system using mmWave radar technology for Advanced Driver Assistance System (ADAS) applications. The proposed system integrates radar signal processing, point cloud generation, feature extraction, machine learning classification, and FPGA acceleration to achieve reliable real-time road object detection in embedded automotive environments.

The system is designed to detect and classify road objects such as vehicles, pedestrians, and trucks using radar-generated spatial and motion information. Unlike conventional camera-based systems, mmWave radar provides robust detection performance under challenging environmental conditions such as low light, fog, rain, and dust, making it highly suitable for intelligent transportation and autonomous driving applications.

The complete processing pipeline was implemented using signal processing algorithms, machine learning-based classification techniques, and FPGA-oriented optimization methods to improve computational efficiency and achieve low-latency inference.

---

# System Architecture

The proposed system consists of the following major stages:

1. Radar Signal Acquisition
2. ADC Conversion
3. Range-Doppler Processing
4. CFAR-Based Target Detection
5. Point Cloud Generation
6. Bird’s Eye View (BEV) Transformation
7. CNN-Based Feature Extraction
8. Logistic Regression Classification
9. FPGA-Based Real-Time Deployment

---

# Step 1: Radar Signal Acquisition and Preprocessing

The system begins with mmWave radar transmission using FMCW (Frequency Modulated Continuous Wave) chirp signals. The transmitted radar waves reflect from surrounding road objects including vehicles and pedestrians, and the reflected signals are captured using radar receiver antennas.

The analog reflected signals are converted into digital Intermediate Frequency (IF) signals using high-speed Analog-to-Digital Conversion (ADC) techniques for further signal processing operations.

The radar signal contains important object information including:

* Object distance (Range)
* Relative velocity (Doppler information)
* Angle of arrival (Direction)

## Raw Radar ADC Signal

<img width="564" height="514" alt="image" src="https://github.com/user-attachments/assets/3cdc336f-65e0-4adb-a6db-2a0aa400be65" />


The above figure represents the raw radar ADC signal captured in the time domain before signal processing operations.

---

# Step 2: Range-Doppler Processing

After preprocessing, FFT-based signal processing techniques are applied to estimate object distance and velocity information.

The following operations are performed:

* Range FFT for distance estimation
* Doppler FFT for velocity estimation
* Angle estimation using beamforming techniques
* Generation of Range-Doppler maps

## Range FFT and Doppler FFT Processing

<img width="534" height="387" alt="image" src="https://github.com/user-attachments/assets/3a8be46a-43ba-433c-a829-363a8417d7ac" />


The generated Range-Doppler representation helps identify moving and stationary targets within the radar field of view.

---

# Step 3: CFAR-Based Target Detection

To eliminate unwanted noise and improve target reliability, the CFAR (Constant False Alarm Rate) algorithm is implemented. CFAR dynamically estimates threshold values and detects valid radar targets while suppressing background noise.

## CFAR Detection Output

<img width="546" height="434" alt="image" src="https://github.com/user-attachments/assets/f29bd755-e0c2-4b51-8a9a-5d0b23b5ab18" />


The detected targets after CFAR processing represent valid radar object reflections used for further feature extraction and classification.

---

# Step 4: Point Cloud Generation

The detected radar targets are transformed into 3D point cloud representations containing:

* Spatial coordinates
* Velocity information
* Signal intensity values

Point cloud processing improves environmental representation and enables object-level spatial analysis.

## Point Cloud Representation

<img width="517" height="517" alt="image" src="https://github.com/user-attachments/assets/e5b277ef-78de-4ff9-bcf5-652085e4141d" />


The point cloud representation converts radar detections into structured spatial information for intelligent object analysis.

---

# Step 5: Bird’s Eye View (BEV) Transformation and Feature Extraction

The generated point cloud data is projected into Bird’s Eye View (BEV) representation to simplify spatial interpretation and reduce irrelevant environmental noise.

The BEV representation is normalized into fixed-size grid structures suitable for feature extraction and machine learning classification.

A lightweight CNN/VGG16-based feature extraction model is utilized to extract:

* Shape features
* Spatial distribution patterns
* Reflection characteristics
* Object feature vectors



---

# Step 6: Machine Learning-Based Object Classification

For object classification, Logistic Regression (LR) classifiers were implemented due to their:

* Low computational complexity
* Fast inference capability
* FPGA compatibility
* Real-time embedded suitability

The Logistic Regression model was trained using labeled radar datasets containing multiple road object categories such as:

* Car
* Pedestrian

The classification model achieved approximately **95% testing accuracy**, demonstrating reliable object recognition performance for real-time ADAS applications.

## Classification Performance

<img width="402" height="356" alt="image" src="https://github.com/user-attachments/assets/6d8dedf7-bbdc-4c5b-84a1-00ec55501bbe" />


The confusion matrix demonstrates the effectiveness of the Logistic Regression classifier in accurately identifying multiple road object categories with high precision and reduced misclassification.

---

# Step 7: Radar Object Tracking and Trajectory Smoothing

The detected objects were continuously tracked using radar trajectory estimation techniques. Since raw radar trajectories contain fluctuations caused by sensor noise and environmental disturbances, temporal smoothing techniques were applied to improve trajectory stability.

Moving average-based smoothing was implemented on X and Y positional coordinates to generate continuous and reliable motion paths.

## Radar Trajectory Smoothing

<img width="504" height="311" alt="image" src="https://github.com/user-attachments/assets/4ff3443b-531a-4dcb-bdf0-005307b8b060" />
<img width="414" height="439" alt="image" src="https://github.com/user-attachments/assets/ad978cf9-8ecc-4a98-b12a-6ff0ce5ac296" />



Trajectory smoothing significantly improves motion consistency and enhances tracking reliability for intelligent transportation systems.

---

# Final Output

The proposed system successfully performs:

* Real-time radar target detection
* Road object classification
* Multi-object tracking
* Trajectory smoothing
* Embedded FPGA acceleration

The final system provides reliable detection and classification of:

* Vehicles
* Pedestrians
* Trucks

using real-time radar-based environmental sensing.

## Final Top-View Object Detection Output
<img width="535" height="451" alt="image" src="https://github.com/user-attachments/assets/08f7f621-e6f8-408a-9b27-dfd5468e78d6" />
<img width="535" height="451" alt="image" src="https://github.com/user-attachments/assets/6a414ed1-87ad-4fa1-9fee-924adae799c5" />


The generated top-view visualization demonstrates successful object localization and classification within the radar monitoring region.

---

# FPGA-Based Implementation

The complete processing pipeline was optimized for FPGA deployment using the PYNQ-ZU FPGA platform. FPGA acceleration enables:

* Parallel processing
* Low latency
* Reduced power consumption
* High-speed computation
* Real-time embedded inference

The FPGA-oriented architecture significantly improves processing efficiency and enables deployment in embedded ADAS and autonomous vehicle systems.

---

# Technologies Used

* mmWave Radar
* FMCW Signal Processing
* FFT Processing
* CFAR Detection
* Point Cloud Generation
* CNN / VGG16 Feature Extraction
* Logistic Regression Classification
* FPGA Acceleration
* PYNQ-ZU FPGA
* Python
* Embedded AI

---

# Applications

* Advanced Driver Assistance Systems (ADAS)
* Autonomous Vehicles
* Intelligent Transportation Systems
* Smart Traffic Monitoring
* Embedded AI Systems
* Automotive Safety Systems
* Real-Time Object Detection

---

# Future Scope

The proposed system can be further enhanced using:

* Deep learning-based object detection
* Multi-object tracking algorithms
* Sensor fusion integration
* Edge AI optimization
* Real-time autonomous navigation
* Advanced FPGA acceleration
* Transformer-based radar perception models

---

# Conclusion

This project demonstrates an efficient FPGA-based mmWave radar object detection and classification framework for real-time ADAS applications. By integrating radar signal processing, CFAR target detection, point cloud generation, CNN-based feature extraction, and Logistic Regression classification, the proposed system achieves reliable and low-latency road object detection suitable for next-generation intelligent transportation and embedded automotive systems.

The achieved 95% classification accuracy validates the effectiveness of the proposed radar-based embedded AI framework for intelligent road environment perception.

---

# Author

Yasaswini,
MTech Embedded Systems
