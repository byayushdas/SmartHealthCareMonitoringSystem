# Smart Health Care Monitoring System

A smart health care monitoring system built with an ESP32, multiple biomedical and environmental sensors, and an MQTT + Node-RED pipeline for real-time data collection and CSV logging.

## Prototype

The ESP32 reads health and motion data, publishes it to a public MQTT broker, and Node-RED subscribes to the same topic to save the incoming JSON payload as CSV for later analysis and AI/ML experiments.

## Features

- Real-time sensor monitoring from health, motion, environmental, and GPS modules.
- Wireless communication using MQTT over the public broker `test.mosquitto.org`.
- Structured JSON payloads for easy integration with dashboards and data pipelines.
- Node-RED flow to receive MQTT messages and write them to a CSV file.
- Dataset preparation workflow for AI/ML-based health monitoring experiments.

## Hardware Components

- Microcontroller: NodeMCU ESP32 Devkit V1
- Heart Rate & SpO2 Sensor: MAX30100
- Motion Sensor: MPU6050
- ECG Sensor: AD8232
- Pressure & Temperature Sensor: BMP180
- UV Sensor: CJMCU-GUVA-S12SD
- GPS Module: GY-GPSV3 NEO-M8N

## Assembly Instructions

Please follow the pin configuration defined in `esp32.ino` during hardware assembly and sensor wiring.

## Getting Started

### Software Interface

1. **ESP32 Setup**: Open `esp32.ino` in the Arduino IDE, update the WiFi credentials if needed, and upload it to the ESP32.
2. **MQTT Broker**: The ESP32 publishes data to the topic `ahmm` on `test.mosquitto.org`.
3. **Node-RED Setup**: Import `node-red-flow.json` into Node-RED and deploy the flow.
4. **CSV Logging**: Update the file path in the Node-RED file node if needed so the incoming data is saved to your desired CSV location.
5. **AI/ML Workflow**: Use the generated CSV data with the notebook `Development_of_Smart_Healthcare_Monitoring_System_Based_on_Machine_Learning_Techniques.ipynb` for preprocessing, dataset preparation, and model experimentation.

## Data Flow

1. Sensors connected to the ESP32 collect live readings.
2. The ESP32 packages the readings into a JSON payload.
3. The JSON payload is published to MQTT topic `ahmm`.
4. Node-RED receives the message and appends it to a CSV file.
5. The CSV dataset can then be used for machine learning and health analysis.
