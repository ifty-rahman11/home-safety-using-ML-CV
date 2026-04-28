# Automated Home Safety System using Computer Vision

## 🛡️ Overview
This project is an automated home safety system designed to provide affordable and reliable security using computer vision. The system continuously monitors its surroundings to detect potential fire hazards or unauthorized intruders, immediately sending an email alert to the homeowner upon detection. 

## ✨ Key Features
* **Intruder Detection:** Utilizes facial recognition algorithms to monitor surroundings and detect unauthorized individuals.
* **Fire & Smoke Detection:** Employs computer vision to identify fire and smoke in their preliminary stages.
* **Automated Email Notifications:** If anomalies or non-residents are detected, the system uses the `smtplib` library to send an automatic email notification that includes an image of the detected person.
* **Audio & Visual Alarms:** Triggers a siren alert (`.wav` file) and toggles physical warning LEDs via hardware integration.

## ⚠️ Important Hardware Note: Arduino Required
**Please note:** This system features hardware integration to turn physical warning LEDs on or off. **An Arduino must be connected to the system via USB.** If you attempt to run the recognition or detection scripts without an Arduino connected to the configured COM port, the code will throw a serial connection error and crash.

## 🛠️ Tech Stack & Libraries
* **Core Language:** Python
* **Computer Vision:** OpenCV, NumPy, imutils, cvzone.
* **Hardware Interfacing:** pySerial (for Arduino LED control)
* **Algorithms:** Haar Cascade Classifiers

## 📂 File Structure & Purpose
This repository contains a multi-step pipeline for facial recognition and hazard detection. Here is what each file does:

**1. Data Collection & Training:**
* `face_taker.py`: Run this script first to capture images of authorized residents via webcam and build the initial dataset.
* `names.json`: Stores the mapping of ID numbers to the actual names of the residents captured.
* `face_train.py`: Processes the captured images to train the facial recognition model.
* `trainer.yml`: The generated output file from the training script, containing the trained face model data.

**2. Execution & Detection:**
* `face_recognizer.py`: The main script that uses the webcam to identify faces in real-time, comparing them against the `trainer.yml` file to detect non-residents.
* `fireDetection.py`: Runs the fire and smoke detection logic.
* `mail.py`: A helper script dedicated to formatting and sending the custom email alerts.
* `run.bat`: A convenient Windows batch file to easily launch the system without using the command line.

**3. Models & Assets:**
* `haarcascade_frontalface_default.xml`: The pre-trained Haar Cascade model used to distinguish facial features.
* `fire_detection_cascade_model.xml`: The pre-trained cascade model used specifically for recognizing fire patterns.
* `siren-alert-96052.wav`: The audio file played when an intruder or fire is detected.
* `/images` & `/intruder_images`: Directories used to store captured logs of unauthorized individuals.


   Ensure you have Python installed, then install the required libraries:
   ```bash
   pip install opencv-python numpy imutils cvzone pyserial
