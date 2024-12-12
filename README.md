# Raspberry Pi IoT Project

This project enables remote control of a robot using a Flask-based web app. It also features live video streaming using the Raspberry Pi camera module.

## Features

- **Remote Control**: Control the robot's movement (forward, backward, left, right, stop) via a web interface.
- **Live Video Streaming**: Stream live video from the Raspberry Pi camera to the web app.
- **Motor Control**: Manage motor movements using GPIO pins on the Raspberry Pi.
- **Containerization**: Easily deploy the app using Docker.

---

## Table of Contents

1. [Requirements](#requirements)
2. [Installation](#installation)
3. [Usage](#usage)
4. [File Descriptions](#file-descriptions)
5. [Testing](#testing)
6. [Deploying with Docker](#deploying-with-docker)
7. [License](#license)

---

## Requirements

- **Hardware**:
  - Raspberry Pi (tested on Pi 5 Model B)
  - Raspberry Pi Camera Module
  - Motor Driver (L298N or similar)
  - Motors and power supply
  - Internet connectivity (Wi-Fi)

- **Software**:
  - Python 3.9+
  - Flask
  - OpenCV
  - Picamera2
  - Docker (optional for containerization)

---

## Installation

### 1. Setting Up the Raspberry Pi
1. Install the latest Raspberry Pi OS.
2. Enable the camera interface via `sudo raspi-config`.
3. Ensure the GPIO pins and camera module are connected.

### 2. Clone the Repository
```bash
git clone https://github.com/dlsmzhhh/iotproj.git
cd iotproj
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Test the Motors
Ensure your motor connections are correct:
```bash
sudo python3 test_motors.py
```

---

## Usage

### 1. Run the App
```bash
sudo python3 app.py
```
Access the web app in your browser at `http://<your-pi-ip>:5000`.

### 2. Controls
- **Forward**: Moves the robot forward.
- **Backward**: Moves the robot backward.
- **Left**: Turns the robot left.
- **Right**: Turns the robot right.
- **Stop**: Stops all motor movements.

### 3. Live Video Streaming
The live video stream will be displayed on the web interface.

---

## File Descriptions

- **`app.py`**: Main Flask app for web controls and video streaming.
- **`motors.py`**: Handles motor control using GPIO pins.
- **`test_motors.py`**: Test script to verify motor movements.
- **`requirements.txt`**: List of Python dependencies.
- **`Dockerfile`**: Docker configuration for containerization.
- **`templates/index.html`**: Web interface for controlling the robot.
- **`.dockerignore`**: Specifies files to ignore during Docker builds.

---

## Testing

### Test the Motors
```bash
sudo python3 test_motors.py
```

### Test the Camera
```bash
libcamera-hello
```

### Test the Web App
Start the app and control the robot via the browser:
```bash
sudo python3 app.py
```

---

## Deploying with Docker

### 1. Build the Docker Image
```bash
sudo docker build -t rpi-flask .
```

### 2. Run the Docker Container
```bash
sudo docker run --rm -p 5000:5000 --privileged rpi-flask
```

---

## Notes

1. **GPIO Pin Configuration**:
   - Pin 16 (GPIO 23): Motor 1 Forward
   - Pin 18 (GPIO 24): Motor 1 Backward
   - Pin 11 (GPIO 17): Motor 2 Forward
   - Pin 15 (GPIO 22): Motor 2 Backward

2. **Reverse Motor Directions**:
   Adjust the logic in `motors.py` to suit your motor driver's requirements.

---

## License

This project is licensed under the MIT License.

---

## Acknowledgments

- Thanks to the Raspberry Pi and Python communities for their resources and tools.
- Special thanks to my CCIoT Prof Jiang Wenchao and TA Du Xiao for the guide.
```

