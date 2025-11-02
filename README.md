# Portable-Health-Monitoring-Device-MAX30102-Arduino-
An Arduino Nano-based pulse oximeter and heart rate monitor using the MAX30102 sensor and a 0.96” OLED display. Displays SpO₂ and BPM in real-time, with push-button control and buzzer alerts. Compact, low-cost prototype for health monitoring and biomedical applications.

![WhatsApp Image 2025-11-03 at 01 11 00_adbe09b7](https://github.com/user-attachments/assets/5cf32474-ef50-4b42-a041-e5a4b20c9b29)

# Project Overview

This project is a Pulse Oximeter and Heart Rate Monitor built using an Arduino Nano, MAX30102 sensor, 0.96" OLED display, push buttons, and a buzzer. The system measures and displays the user’s SpO₂ (oxygen saturation) and heart rate (BPM) in real time on the OLED screen. The MAX30102 sensor uses infrared and red light to detect blood oxygen levels and pulse rate, while the Arduino Nano processes the sensor data and controls the display and alerts.

Designed to be compact, affordable, and reliable, this device serves as a portable health monitoring solution suitable for biomedical projects, DIY health devices, and academic research.

Let's get started..

![WhatsApp Image 2025-11-03 at 01 52 47_71ba6f60](https://github.com/user-attachments/assets/fa06f33c-ec9d-4b48-af69-86f4d810b911)


# Features
- It is compact.
- Low Cost.
- Battery Powered.
- Portable.


# Applications

- Personal Health Monitoring: Track heart rate and oxygen levels at home.
- Wearable Devices: Can be integrated into smart health wearables.
- Biomedical Research: Useful for physiological signal measurement and data analysis.
- Student Projects: Ideal for academic and IoT-based health monitoring projects.
- Clinical Prototyping: Serves as a low-cost prototype for testing patient monitoring systems.

# Core Components used in this project
- Arduino nano (Main MCU).
- MAX30102 Sensor.
- 0.96 inch oled display.
- 5v onboard buzzer.
- Push button.
- 1K ohm resistor.
- On - Off toggle switch.
- 9v bettery.
- Wires
- Zero pcb / Vero board.

# MAX303012 Sensor
The MAX30102 is an integrated sensor module that acts as a heart rate monitor and pulse oximeter, used in wearable and health-monitoring devices. It works by shining red and infrared light through the skin (like a fingertip) and measuring the light's absorbance with a photodetector to calculate blood oxygen levels and heart rate. The device communicates via an I2C interface and has low-power features, including a shutdown mode that allows it to remain powered at all times.

<img width="470" height="426" alt="MAX30102-Module-Pinout" src="https://github.com/user-attachments/assets/1d740e20-63be-4788-a6bf-865efb6f4de9" />

Technical Specifications -->
Here are the technical specifications:

- Power supply	-- 3.3V to 5.5V
- Current draw	-- ~600μA (during measurements)~0.7μA (during standby mode)
- Red LED Wavelength	-- 660nm
- IR LED Wavelength	-- 880nm
- Temperature Range	-40˚C to +85˚C
- Temperature Accuracy	±1˚C

How it works -->
- Integrated components: It combines an integrated pulse oximeter and heart rate sensor into a single module, with internal LEDs (red and infrared), photodetectors, and low-noise electronics.
- Light measurement: It uses two LEDs (red and infrared) to emit light and a photodetector to measure how much light is absorbed by the blood.
- Algorithm: Proprietary algorithms and a built-in ambient light cancellation (ALC) feature help provide accurate readings by filtering out external light interference.
- Data storage: It features a 16-deep FIFO buffer to store data, allowing the sensor to collect data even when the microcontroller is busy and then retrieve it later. 

Key features -->
- Heart Rate and Pulse Oximetry: Measures both heart rate and blood oxygen saturation (SpO2).
- I2C Interface: Communicates with a host microcontroller using a standard I2C-compatible interface.
- Low Power: Features an ultra-low-power mode that allows it to be powered down via software with a negligible standby current.
- Motion Artifact Resilience: Built-in features make it robust against motion artifacts.
- Programmable: It is fully configurable through software, including the sample rate and LED current for power savings.

Typical applications -->
- Wearable devices
- Fitness trackers
- Medical monitoring devices
- Mobile and portable health devices

# Working Principle
The MAX30102 is an optical sensor that measures heart rate and blood oxygen levels (SpO₂) using light. It contains two LEDs—red (660 nm) and infrared (880 nm)—along with a photodetector.

These two wavelengths interact differently with oxygenated and deoxygenated blood. By shining both lights through a thin part of the body, such as a fingertip or earlobe, the sensor detects variations in the amount of light absorbed and reflected. The photodetector captures these changes, and the data is processed using a technique called Photoplethysmography (PPG)—a method for measuring blood volume fluctuations caused by the heartbeat.

In essence, the MAX30102 converts tiny changes in light absorption into accurate readings of pulse rate and SpO₂ levels, making it ideal for compact and non-invasive health monitoring applications.

<img width="358" height="274" alt="MAX30102-Pulse-Detection-Photoplethysmogram" src="https://github.com/user-attachments/assets/839bee05-1053-46b2-9ad3-21ad069393e2" />


# Measuring Your Heart Rate
Your blood transports oxygen using a protein called hemoglobin. When hemoglobin is carrying oxygen—called oxygenated hemoglobin (HbO₂)—it absorbs more infrared light.

With each heartbeat, oxygen-rich blood flows into your fingertip, increasing the amount of oxygenated hemoglobin. As a result, more infrared light is absorbed, and less light is reflected back to the photodetector.

Between heartbeats, the oxygen level in your fingertip slightly decreases, causing less infrared light to be absorbed and more light to reach the detector. These tiny variations in light intensity help the sensor determine both heart rate and oxygen saturation (SpO₂). By continuously shining the infrared light and measuring these changes in the amount of light detected, the sensor can see a pattern that matches your heartbeat. It counts these “pulses” of changing light intensity to calculate how many times your heart beats per minute – your heart rate!

<img width="600" height="332" alt="Pulse-Detection-Heart-Rate-Sensor-Working-Photoplethysmogram" src="https://github.com/user-attachments/assets/099149b5-fda4-4b55-be7d-8f550767da03" />

# Measuring Blood Oxygen Levels (Pulse Oximetry)
To measure the oxygen level in your blood, the MAX30102 cleverly uses both the red and infrared lights. The key idea here is that oxygenated hemoglobin (HbO2) and deoxygenated hemoglobin (Hb) absorb light differently:
- Oxygenated hemoglobin absorbs more infrared light (880nm)
- Deoxygenated hemoglobin absorbs more red light (660nm)
The absorption-spectrum graph below shows how oxygenated hemoglobin and deoxygenated hemoglobin absorb different wavelengths of light at different rates.
By comparing how much red light and how much infrared light is absorbed, the MAX30102 can calculate what percentage of your hemoglobin is carrying oxygen. This percentage is your SpO2 level, which indicates how well-oxygenated your blood is.

<img width="557" height="362" alt="Absorption-Spectrum-of-Hb-and-HbO2" src="https://github.com/user-attachments/assets/d674f44d-0b36-4f1d-a3aa-b5fed1b0a40c" />


# Video Presentation
Link - ![YouTube](https://youtu.be/Zvhejq2pKcI?si=6f5SvCnFc173LdaP)
