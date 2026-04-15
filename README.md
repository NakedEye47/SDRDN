<div align="center">

# 🚁 SDRDN
### Smart Disaster Response Drone Network

[![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)](https://github.com/NakedEye47/SDRDN)
[![Python](https://img.shields.io/badge/Python-3.9+-blue)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Raspberry%20Pi-lightgrey)](https://github.com/NakedEye47/SDRDN)

**An autonomous multi-drone system for real-time disaster response with AI survivor detection, wireless mesh networking, and live command dashboard.**

</div>

---

## 📋 Status

**Status:** In Progress — Local Government Proposal Project Proposal

> This project is currently under development as a CPE Design Project 2 (Research, Capstone, and Internship) proposal for local government adoption. The software stack is fully implemented and testable in simulation mode. Hardware integration is pending procurement.

**Presented by:** Alexander E. Sugian
**Academic Year:** 2025–2026

---

## 🌟 Overview

SDRDN is an autonomous multi-drone system that enhances disaster management by providing **real-time surveillance**, **AI-powered survivor detection**, and **reliable communication** through a wireless mesh network — even when traditional infrastructure fails.

When earthquakes, floods, or landslides strike, SDRDN deploys a coordinated drone fleet to survey affected areas, detect survivors using onboard AI, and relay critical data back to a central command dashboard — all without relying on cellular networks.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🚁 **Autonomous Flight** | PX4/ArduPilot autopilot with waypoint navigation and grid survey patterns |
| 🧠 **Edge AI Detection** | TensorFlow Lite + OpenCV running onboard for real-time survivor detection |
| 📡 **Mesh Network** | LoRa radio mesh — works up to 1-5km without cellular infrastructure |
| 🖥️ **Live Dashboard** | Real-time command center with tactical map, detection feed, and console |
| 💾 **Mission Logging** | SQLite database with GeoJSON export of all detections |
| 📦 **Desktop App** | Electron.js packaging as installable .exe for Windows |
| 🔄 **Simulation Mode** | Full software testable without any hardware |
| ⚡ **WebSocket** | Real-time data streaming from drones to dashboard |

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     OPERATOR DASHBOARD                       │
│         HTML · CSS · JS · WebSocket · Canvas Map            │
└────────────────────────┬────────────────────────────────────┘
                         │ WebSocket (Socket.IO) + REST API
┌────────────────────────▼────────────────────────────────────┐
│                     BASE STATION                             │
│    Flask + Socket.IO  │  MQTT (Mosquitto)  │  SQLite DB     │
└────────────────────────┬────────────────────────────────────┘
                         │ MQTT over LoRa Mesh Network
          ┌──────────────┼──────────────┐
          │              │              │
┌─────────▼──┐  ┌────────▼──┐  ┌───────▼────┐
│  DRONE-1   │  │  DRONE-2  │  │  DRONE-3   │
│ Pixhawk FC │  │ Pixhawk FC│  │ Pixhawk FC │
│ RPi 4      │  │ RPi 4     │  │ RPi 4      │
│ Camera     │  │ Camera    │  │ Camera     │
│ LoRa Radio │  │ LoRa Radio│  │ LoRa Radio │
│ TFLite AI  │  │ TFLite AI │  │ TFLite AI  │
└────────────┘  └───────────┘  └────────────┘
```

---

## 📁 Project Structure

```
SDRDN/
├── drone/                    # Drone node software (Raspberry Pi)
│   ├── ai/
│   │   ├── detector.py       # TFLite AI detection engine
│   │   └── model_loader.py   # Model verification and loading
│   ├── comms/
│   │   ├── mavlink_client.py # Pixhawk MAVLink communication
│   │   ├── mesh_router.py    # MQTT mesh networking
│   │   └── lora_client.py    # LoRa radio hardware interface
│   ├── flight/
│   │   ├── autopilot.py      # High-level autopilot commands
│   │   └── waypoint_manager.py # Mission and waypoint management
│   ├── utils/
│   │   ├── camera.py         # Camera capture service
│   │   ├── gps.py            # GPS utilities
│   │   ├── logger.py         # Logging system
│   │   └── watchdog.py       # Service health monitoring
│   ├── config.py             # Drone configuration
│   └── main.py               # Drone node entry point
│
├── base_station/             # Ground base station software
│   ├── api/
│   │   ├── routes.py         # Flask REST API endpoints
│   │   └── server.py         # Flask + SocketIO server setup
│   ├── database/
│   │   ├── models.py         # SQLAlchemy database models
│   │   └── db.py             # Database connection and init
│   ├── mqtt/
│   │   └── subscriber.py     # MQTT subscriber (receives drone data)
│   ├── websocket/
│   │   └── server.py         # WebSocket event handlers
│   ├── config.py             # Base station configuration
│   └── main.py               # Base station entry point
│
├── dashboard/                # Web-based operator dashboard
│   ├── index.html            # Main dashboard HTML
│   ├── css/style.css         # Dashboard styles
│   └── js/
│       ├── app.js            # Main app logic and state
│       ├── map.js            # Canvas tactical map renderer
│       ├── websocket.js      # Real-time WebSocket client
│       └── detection_feed.js # AI detection feed manager
│
├── electron/                 # Desktop app packaging
│   ├── main.js               # Electron main process
│   └── preload.js            # Electron preload script
│
├── tests/                    # Unit tests
│   ├── drone/
│   │   ├── test_detector.py  # AI detector tests
│   │   └── test_mavlink.py   # MAVLink client tests
│   └── base_station/
│       ├── test_api.py       # Flask API tests
│       └── test_mqtt.py      # MQTT subscriber tests
│
├── docs/                     # Documentation
│   ├── architecture.md       # System architecture details
│   ├── hardware_setup.md     # Hardware wiring and setup
│   ├── software_setup.md     # Software installation guide
│   └── deployment.md         # Deployment instructions
│
├── scripts/                  # Windows batch scripts
│   ├── setup.bat             # Full system setup
│   ├── install_deps.bat      # Install dependencies
│   ├── start_base.bat        # Start base station
│   └── start_drone.bat       # Start drone simulation
│
├── requirements.txt          # Python dependencies
├── package.json              # Node.js / Electron config
└── README.md                 # This file
```

---

## 🔧 Tech Stack

| Layer | Technology |
|-------|-----------|
| **Flight Controller** | PX4 / ArduPilot · MAVLink (C/C++) |
| **Companion Computer** | Python 3.9+ on Raspberry Pi 4 |
| **AI Detection** | TensorFlow Lite · OpenCV · YOLOv8 nano |
| **Mesh Network** | LoRa RFM95W · ESP-NOW · MQTT |
| **IoT Messaging** | Mosquitto MQTT Broker |
| **Backend** | Flask · Flask-SocketIO · SQLAlchemy |
| **Database** | SQLite |
| **Dashboard** | HTML · CSS · JavaScript · Canvas API |
| **Desktop App** | Electron.js |
| **Hardware** | Pixhawk 4 · Raspberry Pi 4 · FLIR Lepton |

---

## 🚀 Quick Start

### Requirements
- Python 3.9+
- Node.js 18+
- Git
- Windows 10/11 (for base station)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/NakedEye47/SDRDN.git
cd SDRDN

# 2. Run setup (installs all dependencies)
scripts\setup.bat

# 3. Start Mosquitto MQTT Broker (run as Administrator)
net start mosquitto

# 4. Start the base station
scripts\start_base.bat

# 5. Open dashboard in browser
# Navigate to: http://localhost:5000
```

### Running as Desktop App

```bash
npm start
```

### Building Installer (.exe)

```bash
npm run build
# Output: out/SDRDN Setup.exe
```

---

## 🧪 Testing (No Hardware Required)

The full system runs in **simulation mode** automatically when no drones are connected:

```bash
# Start base station
scripts\start_base.bat

# Open dashboard — simulation starts automatically
http://localhost:5000
```

**In simulation mode you get:**
- 3 virtual drones moving on the tactical map
- Random AI detections (survivor, fire, thermal, collapse)
- Full mission progress tracking
- Complete console and command system
- All REST API endpoints working

### Run Unit Tests

```bash
# All tests
python -m pytest tests/

# Specific modules
python -m pytest tests/drone/test_detector.py -v
python -m pytest tests/base_station/test_api.py -v
```

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health` | System health check |
| GET | `/api/drones` | All active drone statuses |
| GET | `/api/detections` | Recent AI detections |
| GET | `/api/detections/export` | Export as GeoJSON |
| GET | `/api/missions` | List missions |
| POST | `/api/missions` | Create new mission |

---

## 🔑 Key Performance Targets

| Metric | Target |
|--------|--------|
| AI Detection Accuracy | ≥ 90% |
| Detection Latency | < 5 seconds |
| Mesh Network Range | Up to 1 km (LoRa) |
| Flight Time | 20–30 minutes per battery |
| Video Feed Delay | ≤ 2 seconds |
| Coverage per Drone | 200–500m radius |

---

## 🔌 Hardware Required

**Per Drone Node:**
- Pixhawk 4 Flight Controller
- Raspberry Pi 4 (4GB RAM)
- Raspberry Pi Camera Module v2
- FLIR Lepton 3.5 (thermal, optional)
- M8N GPS Module
- RFM95W LoRa Radio Module
- 4S LiPo Battery (5000mAh)
- F450 Quadcopter Frame + Motors + ESCs

**Base Station:**
- Windows PC / Laptop
- RFM95W LoRa Gateway Module

> 📄 See [docs/hardware_setup.md](docs/hardware_setup.md) for detailed wiring diagrams and setup instructions.

---

## 📖 Documentation

| Document | Description |
|----------|-------------|
| [Architecture](docs/architecture.md) | System design and data flow |
| [Hardware Setup](docs/hardware_setup.md) | Wiring diagrams and component setup |
| [Software Setup](docs/software_setup.md) | Installation guide |
| [Deployment](docs/deployment.md) | Field deployment instructions |
| [Installation Guide](SDRDN_Installation_Guide.txt) | Complete step-by-step guide |

---

## 🤝 Contributing

This is a capstone research project. For inquiries about collaboration or the local government proposal, please contact the developer.

---

## 📄 License

MIT License — Copyright © 2025 Alexander E. Sugian

---

<div align="center">

**SDRDN — Smart Disaster Response Drone Network**

*Saving lives through autonomous aerial intelligence*

[GitHub](https://github.com/NakedEye47) · [LinkedIn](https://linkedin.com/in/alexanderdgreat/)

</div>
