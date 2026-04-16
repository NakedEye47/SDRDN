# SDRDN — Live Demo
### Smart Disaster Response Drone Network

[![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)](https://github.com/NakedEye47/SDRDN)
[![Demo](https://img.shields.io/badge/Live%20Demo-Online-brightgreen)](https://nakedeye47.github.io/SDRDN)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

> ⚠️ This repository contains the **live demo (simulation mode only)**.  
> The complete functional system with drone software, AI detection, and mesh networking is kept private for local government proposal purposes.

---

## 🔴 Live Demo

**[▶ Open Live Dashboard](https://nakedeye47.github.io/SDRDN)**

---

## 📸 What You'll See

The demo runs in **full simulation mode** — no hardware required:

- 🗺️ **Tactical Map** — 3 virtual drones moving in real-time on a satellite-style map
- 🧠 **AI Detection Feed** — Simulated survivor, fire, thermal, and structural collapse detections
- 📊 **System Stats** — Live drone count, coverage %, mesh packets, detection count
- 🎮 **Mission Control** — Active missions with progress tracking and ETA
- 💻 **Console** — Live system log with command input (`status`, `rth`, `help`)
- 📡 **Drone Fleet** — Battery levels, altitude, speed, signal strength per drone

---

## 🚁 About SDRDN

SDRDN is an autonomous multi-drone system designed for disaster response operations. When earthquakes, floods, or landslides strike, SDRDN deploys a coordinated drone fleet to:

- Survey affected areas autonomously
- Detect survivors using onboard AI (TensorFlow Lite + OpenCV)
- Relay real-time data via LoRa mesh network (no cellular required)
- Display everything on a live command dashboard

**Status:** In Progress — Local Government Proposal Project Proposal  
**Developer:** Alexander E. Sugian  
**Academic Year:** 2025–2026

---

## 🛠️ Full System Tech Stack

| Layer | Technology |
|-------|-----------|
| Flight Controller | PX4 / ArduPilot · MAVLink · C/C++ |
| Companion Computer | Python 3.9+ on Raspberry Pi 4 |
| AI Detection | TensorFlow Lite · OpenCV · YOLOv8 |
| Mesh Network | LoRa RFM95W · MQTT · ESP-NOW |
| Backend | Flask · Socket.IO · SQLite |
| Dashboard | HTML · CSS · JS · Canvas API |
| Desktop App | Electron.js |

---

## 📄 License

MIT License — Copyright © 2025 Alexander E. Sugian

---

<div align="center">

**[LinkedIn](https://linkedin.com/in/alexanderdgreat/) · [GitHub](https://github.com/NakedEye47)**

*Saving lives through autonomous aerial intelligence*

</div>
