# 🌱 Plant Pulse: Low-Power IoT Environmental Node

> **Node Zero Competition Project**
> A custom-designed PCB engineered to solve the "IoT Power Problem" for remote environmental monitoring.

**Author:** Shazmeen Siddiqui

**Academic Info:** B.Tech Electrical and Computing Engineering (4th Semester)

**University:** Jamia Millia Islamia

## 📁 Repository Structure

**Note:** All project files, including project goals, component parts lists, schematics, and KiCad design files, are located directly in the **root directory** of this repository.

## 📌 Hardware Overview

The Plant Pulse hardware was built to solve a major bottleneck in remote monitoring: the "IoT Power Problem." Most smart monitoring devices drain their batteries in a matter of days, which simply replaces the chore of manual plant monitoring with the chore of constant battery recharging.

This custom PCB was designed to execute a strict **Wake-Sense-Transmit-Sleep** cycle. By aggressively managing power consumption, the board is engineered to run for months on a single cell battery.

### Core Components

* **Microcontroller:** ESP32 (Handles processing and WiFi transmission)

* **Environmental Sensor:** BME280 (Monitors temperature, humidity, and atmospheric pressure)

## ⚡ Schematic & Power Architecture

The standout feature of this board's schematic is its custom power-gating strategy.

* **P-Channel MOSFET Switch:** To prevent the sensors from idling and draining the battery while the system sleeps, the design incorporates a P-channel MOSFET. This allows the ESP32 to effectively "gate" the power, physically cutting off the voltage to the sensors when they aren't actively taking readings. This completely eliminates unnecessary idle current draw, exponentially increasing battery life.

## 🛠️ PCB Layout & Design (KiCad)

The board was designed and routed using **KiCad**, with a strict focus on keeping the footprint compact while ensuring robust RF performance and power stability.

### Critical Design Choices:

* **Antenna Clearance Keep-Out Zone:** To ensure the WiFi signal remains strong and reliable, a strict clearance area (keep-out zone) was maintained around the ESP32 antenna. No copper pours or traces were routed in this section to prevent signal degradation and interference.

### Troubleshooting & Hardware Revisions

Building the board required real-world iterations to achieve perfect stability. Here are the hurdles crossed during development:

1. **Resolving Power Instability:** Initial testing revealed that power spikes during WiFi transmission were causing the ESP32 to unexpectedly reset. This was resolved by designing a decoupling network and adding **100nF and 10µF capacitors** to smooth out voltage drops.

2. **Footprint Mismatch Correction:** During assembly, a footprint dimension error was discovered for the BME280 sensor. The pad dimensions had to be manually corrected within the EDA tool to ensure accurate placement and reliable soldering.

## 🌍 Applications

*This hardware is built as a modular, low-power solution ready for real-world deployment.* While initially inspired by a dying houseplant, the architecture is highly scalable and perfect for:

* **Smart Agriculture & Farming**

* **Automated Greenhouses**

* **Industrial Warehouse Environmental Monitoring**
