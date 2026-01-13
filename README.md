# 🎮 IMU-Based Gesture Recognition for Gaming Control

---

## 📌 Project Overview
This project focuses on **hand gesture recognition using IMU sensor data** to enable **touchless control of PC games** such as *Subway Surfers* and *Temple Run*.  
Gestures are captured using a **MetaWear IMU sensor**, processed through signal preprocessing and feature extraction, and classified using a **Machine Learning model (Random Forest)**.

Recognized gestures are mapped to **real-time keyboard inputs** (⬆️ ⬇️ ⬅️ ➡️), enabling intuitive and responsive game control.

The complete pipeline is implemented in **Python**.

---

## 📊 Dataset Source
The dataset is **self-recorded** using a **MbientLab MetaWear IMU sensor** worn on the hand.

Data is collected programmatically via Bluetooth Low Energy (BLE) and stored locally in CSV format.

- **Sensor:** MbientLab MetaWear (MetaMotion R / RL)
- **Sensors Used:** Accelerometer + Gyroscope
- **Data Acquisition:** Python BLE interface
- **Sampling Mode:** Continuous streaming
- **Local Storage Path:** `dataset/`

---

## 🧾 Dataset Description

- **Data Type:** Inertial Measurement Unit (IMU)
- **Signals:**  
  - Accelerometer (X, Y, Z)  
  - Gyroscope (X, Y, Z)
- **Sampling Frequency:** Sensor-defined (MetaWear default)
- **File Format:** `.csv`
- **Gestures Recorded:**
  - UP (Jump)
  - DOWN (Roll)
  - LEFT (Move Left)
  - RIGHT (Move Right)

Each gesture is recorded multiple times to build a balanced training dataset.

---

## 🧹 Preprocessing Steps
The following preprocessing steps are applied to the raw IMU data:

1. Removal of noise and irrelevant columns
2. Signal smoothing (optional)
3. Energy-based gesture segmentation
4. Extraction of active motion regions
5. Labeling segmented gestures

Processed data is stored in the `dataset_clean/` directory.

---

## 📈 Feature Extraction
From each segmented gesture window, statistical features are extracted, including:

- Mean
- Standard Deviation
- Variance
- Maximum / Minimum
- Signal Energy
- Axis-wise features for both accelerometer and gyroscope

The extracted feature vectors are compiled into a single dataset:


---

## 🤖 Machine Learning Model

- **Algorithm:** Random Forest Classifier
- **Input:** Extracted statistical features
- **Output:** Gesture class (UP, DOWN, LEFT, RIGHT)
- **Model File:** `gesture_model.pkl`

The model is trained and evaluated using standard train-test splits.

Target accuracy: **≥ 85%**

---

## 📊 Plots and Visualizations


## 🎮 Real-Time Gesture Control
The trained model is used for **live gesture recognition**, where incoming IMU data is classified in real time and mapped to keyboard events.

- **Key Simulation:** `pyautogui`
- **Latency:** Optimized using sliding windows and cooldown logic
- **Game Compatibility:** Any keyboard-controlled PC game

---

## ⚙️ Controller Fine-Tuning Parameters

| Parameter | Description |
|---------|------------|
| Trigger Threshold | Controls gesture sensitivity |
| Window Size | Samples used for prediction |
| Cooldown Time | Prevents repeated triggers |
| Probability Threshold | Accepts lower-confidence predictions |

These parameters can be adjusted in `play_gamee.py`.

---

## 📂 Project Structure

├── record.py # Records raw IMU data
├── visualisation.py # Signal & energy visualization
├── preprocessing.py # Gesture segmentation
├── feature_extraction.py # Feature generation
├── train_model.py # Model training
├── play_gamee.py # Real-time control
├── dataset/ # Raw data
├── dataset_clean/ # Processed segments
├── final_features.csv # Feature dataset
└── gesture_model.pkl # Trained model


---

## 🚀 Applications

- Gesture-based gaming
- Human–Computer Interaction (HCI)
- Wearable computing
- Assistive technology
- Smart device control

---

## 🔮 Future Enhancements

- Deep learning models (CNN / LSTM)
- Personalized gesture calibration
- Multi-sensor fusion
- Mobile and embedded deployment
- Adaptive thresholding

---

## 🧠 Author Notes
This project demonstrates the complete pipeline of **IMU signal acquisition, preprocessing, feature extraction, machine learning classification, and real-time system integration**.

It is well-suited for:
- Signal Processing projects
- Machine Learning with time-series data
- Wearable sensor research
- Final-year engineering projects

---



