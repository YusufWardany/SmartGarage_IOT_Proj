# 🚗 Smart Garage Monitor - IoT Parking Solution


## 📌 Project Overview
The **Smart Garage Monitor** is a fully automated, cloud-connected IoT system designed to detect real-time parking occupancy. Built as a proof-of-concept for the Al-Alamein Smart City initiative, this project reduces traffic congestion and fuel consumption by allowing drivers to check parking availability remotely.

## ✨ Key Features
*   **Real-Time Detection:** Uses ultrasonic sensors to detect vehicle presence accurately.
*   **Local Visual Feedback:** LED indicators (Red/Green) provide immediate status to drivers inside the garage.
*   **AWS Cloud Integration:** Secure data transmission using MQTT over TLS via **AWS IoT Core**.
*   **Serverless Dashboard:** A live web dashboard hosted on **Amazon S3** using WebSockets and **Amazon Cognito** for authentication[cite: 2].
*   **Automated Alerts:** Sends instant email notifications via **AWS SNS** whenever a parking spot changes state[cite: 2].
*   **Infrastructure as Code:** Fully automated cloud resource provisioning using **Terraform**[cite: 2].

## 🛠️ Hardware Requirements
*   1x **Raspberry Pi 4** (Gateway)[cite: 2]
*   2x **HC-SR04** Ultrasonic Distance Sensors[cite: 2]
*   2x **Red LEDs** & 2x **Green LEDs**[cite: 2]
*   4x **330Ω Resistors** (for LEDs)[cite: 2]
*   2x **1kΩ & 2kΩ Resistors** (Voltage dividers for sensor ECHO pins)[cite: 2]
*   Jumper Wires & Breadboard

## 🔌 Wiring & Pinout (BCM Mode)
| Component | Spot 01 | Spot 02 |
| :--- | :--- | :--- |
| **HC-SR04 TRIG** | GPIO 17 | GPIO 24 |
| **HC-SR04 ECHO** | GPIO 27 | GPIO 25 |
| **Red LED (Occupied)** | GPIO 22 | GPIO 5 |
| **Green LED (Available)**| GPIO 23 | GPIO 6 |

> **⚠️ CRITICAL:** The HC-SR04 ECHO pin outputs 5V. A voltage divider (1kΩ + 2kΩ) is **mandatory** to step it down to a 3.3V safe level for the Raspberry Pi GPIO[cite: 2].

## 🏗️ Project Structure
```text
smart-garage-2cars/
├── terraform/       # IaC files (AWS IoT, SNS, S3, Cognito)
├── raspberry-pi/    # Python gateway firmware & TLS certs
├── website/         # Frontend HTML/CSS/JS (Serverless)
└── scripts/         # deploy.sh for one-click deployment
