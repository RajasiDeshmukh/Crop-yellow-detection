# UAV-Based Yellow Marker Detection and Geotagging for Precision Agriculture

---

##  Overview

This repository contains the **perception and localization pipeline** developed for a **UAV-based precision agriculture system**.

The objective of the system is to:

- Detect **crop stress markers (yellow indicators)** from aerial imagery  
- Convert detected pixel locations into **geographical coordinates (GPS)**  
- Enable **targeted intervention such as precision spraying**

The pipeline was developed as part of the **NIDAR (National Innovation Challenge for Drone Application and Research)** mission.

>  Some components of the complete operational system are part of **ongoing research work** and are therefore not included in this repository.

---

## 📂 Repository Structure
├── yellow_detection.py
├── pixel_to_gps.py
└── README.md

---

## System Pipeline

The system processes aerial imagery captured by the UAV and generates **geotagged target locations**.

### Main Processing Stages

1. **Image acquisition** from the UAV camera  
2. **Yellow marker detection** in aerial imagery  
3. **Pixel coordinate extraction** of detected targets  
4. **Pixel → GPS conversion** using drone telemetry  
5. **Generation of geotagged target locations**

---

## Modules

### Yellow Marker Detection

**Script:** `yellow_detection.py`

Detects crop stress markers in aerial images using **color segmentation and masking techniques**.

#### Key Challenges Addressed

- **Illumination variability** in outdoor agricultural environments  
- **Specular reflections** from wax-coated crop leaves  
- **Background color interference**

To address these issues, an **improved masking strategy** was implemented to reduce **false detections caused by reflections and background artifacts**.

**Output**

- Detected marker regions  
- Pixel coordinates of candidate targets  

---

###  Pixel-to-GPS Conversion

**Script:** `pixel_to_gps.py`

Converts detected **pixel locations** into **global GPS coordinates** using drone telemetry and camera parameters.

#### Inputs

- Drone **latitude and longitude**
- UAV **altitude**
- Drone **attitude (roll, pitch, yaw)**
- Camera **field of view / parameters**
- **Pixel coordinates** of detected targets

The algorithm projects pixel locations into the **ground reference frame** to estimate the **geographic position of detected regions**.

---

### Geotagging Detected Targets

**Script:** `geotagging.py`
inside yellow detection script itself.
Associates detected targets with computed GPS coordinates and produces **geotagged outputs**.

**Outputs**

- Latitude  
- Longitude  
- Detection metadata  

These geotagged coordinates can be used for:

-  **Targeted pesticide spraying**
-  **Mission planning**
-  **Precision agriculture analytics**

---

## Example Workflow

Typical processing workflow:

1. Capture aerial imagery from the UAV camera  
2. Run `yellow_detection.py` to detect stress markers  
3. Extract pixel coordinates of detected regions  
4. Convert pixel coordinates to GPS using `pixel_to_gps.py`  
5. Generate geotagged outputs using `geotagging.py`

---

## Applications

- Precision agriculture monitoring  
- Crop stress detection  
- Targeted pesticide spraying  
- UAV-based agricultural analytics  

---

## Made by using

- **Python**
- **OpenCV**
- **Drone telemetry data**
- **Geospatial coordinate transformation**

---

## Project Context

This work was developed as part of a **precision agriculture UAV system for the NIDAR 2025 challenge**, where cooperative UAV platforms were used for **crop monitoring and targeted spraying missions**.

Only **selected modules of the full operational pipeline** are included in this repository.

---

---

## System Deployment

The perception and geotagging pipeline was deployed on the UAV platform for real-time operation.

Key implementation aspects include:

- **Onboard inference:** The detection pipeline was deployed on an **NVIDIA Jetson Orin Nano** for real-time processing of aerial imagery.
- **Telemetry integration:** Drone telemetry (GPS, altitude, and attitude) was used for converting detected pixel locations into geographic coordinates.
- **Mission integration:** The pipeline was integrated with **multi-UAV missions during the NIDAR competition**, enabling real-time detection and localization of crop stress regions for targeted spraying operations.

---

## Future Improvements

- Improve robustness of detection under **extreme illumination variations**
- Explore **learning-based approaches for more adaptive detection**
- Extend the system for **multi-target tracking and prioritization**
- Improve **localization accuracy through camera calibration and sensor fusion**

---
 

🔗 GitHub: https://github.com/RajasiDeshmukh
