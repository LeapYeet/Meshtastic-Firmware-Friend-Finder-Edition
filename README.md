<div align="center">

# Meshtastic Firmware: Friend Finder Edition



**An enhanced version of Meshtastic with real-time, compass-based friend tracking.**

</div>

<div align="center">

![License](https://img.shields.io/badge/License-GPL--2.0-blue.svg)
![Version](https://img.shields.io/badge/Version-2.7.x--FF-brightgreen)
![Hardware](https://img.shields.io/badge/Tested_On-Heltec_V3-orange)
![Status](https://img.shields.io/badge/Status-Community_Beta-yellow)

</div>

This custom build of the official Meshtastic firmware introduces the **Friend Finder** module. Developed over several months, this feature adds previously unsupported magnetometer (compass) capabilities, allowing you to pair with and track your friends in real-time. The simple tracking screen shows the distance and a directional arrow, making it easy to find each other when you get separated.

It was developed and tested in real-world conditions, including a crowded outdoor music concert, where it performed exceptionally well.

---

## 📖 Table of Contents

- [Core Features](#-core-features)
- [Screenshots](#-screenshots)
- [Hardware Requirements](#️-hardware-requirements)
- [Installation](#-installation)
- [Getting Started: Setup & Usage](#-getting-started-setup--usage)
- [Performance & Technical Notes](#-performance--technical-notes)
- [License](#-license)

---

## 🎯 Core Features

-   🛰️ **Friend Finder Module**: A new interface to securely pair with other devices and initiate a tracking session.
-   🧭 **Real-Time Tracking Screen**: A dedicated screen shows the distance to your friend and a large arrow pointing in their direction. No more guessing which way to go!
-   🗺️ **Friend Map**: View the locations of all your paired friends simultaneously on a simple map display.
-   ⚙️ **Native Magnetometer Support**: Includes all necessary drivers and logic to use a QMC5883L magnetometer, a feature not yet available in the main Meshtastic repository.
-   🏞️ **Designed for the Outdoors**: Perfect for staying connected at festivals, while skiing, hiking, or at any large-scale event.

---

## 🖼️ Screenshots

A preview of the main tracking screen in action. The top shows the target's name, the large arrow points in their direction, and the footer contains distance and other peer metrics.



---

## ⚙️ Hardware Requirements

For the Friend Finder module to work correctly, specific hardware is **required**. The firmware was built and tested on the following setup:

| Component | Model / Specification | Notes |
| :--- | :--- | :--- |
| **Primary Device**| Heltec Wireless Tracker (V3) | Other ESP32-S3 devices may work but are untested. |
| **GPS Module** | u-blox M8N (or similar) | A satellite lock is **required**. |
| **Magnetometer** | QMC5883L | A compass is **required** for the direction arrow. |

> **IMPORTANT: Magnetometer Wiring**
> The magnetometer **must** be connected to the primary I²C bus. Other ports were tested without success.
> ```text
> Magnetometer -> Heltec V3
> --------------------------
> SDA            -> GPIO 41
> SCL            -> GPIO 42
> ```

---

## 💾 Installation

The easiest way to install this firmware is by using the custom web flasher.

### **➡️ [Install via Web Flasher](https://your-url-here.github.io/your-repo/)**

1.  Click the link above to open the web flasher.
2.  Plug your Heltec V3 into your computer via USB.
3.  Click the **Connect & Install** button.
4.  A pop-up window will appear. Select the correct COM port for your device and click "Connect".
5.  The installation will begin automatically. Do not unplug the device until it is complete.

---

## 🚀 Getting Started: Setup & Usage

After installation, you **must** calibrate the magnetometer for the tracking screen to work correctly.

1.  **Ensure GPS is Active**
    * Before starting, make sure your GPS module is connected and has acquired a solid satellite lock.

2.  **Calibrate the Magnetometer (Mandatory)**
    * On the device, navigate to the main menu.
    * Go to `Friend Finder` -> `Compass Cal`.
    * Run both the **Figure-8 Cal** and **Flat-Spin Cal** routines, following the on-screen instructions.
    * Once calibrated, you can also use the `Set North Here` option to align the compass if needed.

3.  **Pair with Friends**
    * From the main menu, go to `Friend Finder` -> `Start Pairing`.
    * Have your friend do the same on their device. The devices will discover each other and allow you to securely pair.

4.  **Track a Friend**
    * Navigate to `Friend Finder` -> `Track a Friend`.
    * Select your friend from the list to begin a mutual tracking session.
    * The device will switch to the tracking screen, showing the distance and a large arrow pointing towards them.

---

## 📡 Performance & Technical Notes

-   **LoRa Settings**: All testing has been conducted using the **LongFast** channel preset.
-   **Update Interval**: To keep channel utilization below 15%, position updates are sent every **20 seconds**. Faster LoRa settings may support more frequent updates, but this requires further community testing.
-   **Range**: The effective tracking range depends entirely on your device, antenna, LoRa settings, and the surrounding environment.

---

## 📜 License

This project is a derivative work of the official Meshtastic firmware and is therefore licensed under the **GNU General Public License v2.0 (GPL-2.0)**. The original `LICENSE` file is included in the source code.
