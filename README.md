<div align="center">

# Meshtastic Firmware: Friend Finder Edition



**An enhanced version of Meshtastic with real-time, compass-based friend tracking.**

</div>

<div align="center">

![License](https://img.shields.io/badge/License-GPL--2.0-blue.svg)
![Version](https://img.shields.io/badge/Version-2.7--FF-brightgreen)
![Hardware](https://img.shields.io/badge/Tested_On-Heltec_V3-orange)
![Status](https://img.shields.io/badge/Status-Work_In_Progress-yellow)

</div>

This is a custom build of the official Meshtastic firmware that introduces the **Friend Finder** module. This feature allows you to pair with and track your friends in real-time. The tracking screen shows their distance, and if you have a magnetometer installed, a directional arrow makes it easy to find each other when you get separated.

It was developed and tested in real-world conditions, including a crowded outdoor music concert, where it performed exceptionally well.

---

## 📖 Table of Contents

- [Core Features](#-core-features)
- [UI Showcase](#-ui-showcase)
- [Hardware Requirements](#️-hardware-requirements)
- [Installation](#-installation)
- [Getting Started: Setup & Usage](#-getting-started-setup--usage)
- [Project Status & Future Goals](#-project-status--future-goals)
- [Performance & Technical Notes](#-performance--technical-notes)
- [License](#-license)

---

## 🎯 Core Features

-   🛰️ **Friend Finder Module**: A new interface to securely pair with other devices and initiate a tracking session.
-   🧭 **Real-Time Tracking Screen**: Shows the live distance to your friend. With a magnetometer, it also displays a large arrow pointing in their direction.
-   🗺️ **Friend Map**: View the locations of all your paired friends simultaneously on a simple map display.
-   ⚙️ **Optional Magnetometer Support**: Includes all necessary drivers and logic to use a QMC5883L magnetometer for directional tracking.
-   🏞️ **Designed for the Outdoors**: Perfect for staying connected at festivals, while skiing, hiking, or at any large-scale event.

---

## ✨ UI Showcase

| Main Menu | Tracking (with Magnetometer) | Tracking (without Magnetometer) | Calibration Menu |
| :---: | :---: | :---: | :---: |
| <img src="https://raw.githubusercontent.com/LeapYeet/Meshtastic-Firmware-Friend-Finder-Edition/main/home_menu.jpg" width="200"> | <img src="https://raw.githubusercontent.com/LeapYeet/Meshtastic-Firmware-Friend-Finder-Edition/main/tracking_with_mag.jpg" width="200"> | <img src="https://raw.githubusercontent.com/LeapYeet/Meshtastic-Firmware-Friend-Finder-Edition/main/tracking_no_mag.jpg" width="200"> | <img src="https://raw.githubusercontent.com/LeapYeet/Meshtastic-Firmware-Friend-Finder-Edition/main/cal_menu.jpg" width="200"> |
| *Friend Finder on the main menu.* | *Arrow points to your friend.* | *Only the distance is displayed.* | *Easy access to compass calibration.* |

---

## ⚙️ Hardware Requirements

For the Friend Finder module to work, specific hardware is required. The firmware was built and tested on the following setup:

| Component | Model / Specification | Notes |
| :--- | :--- | :--- |
| **Primary Device**| Heltec Wireless Tracker (V3) | Other ESP32-S3 devices may work but are untested. |
| **GPS Module** | Any Meshtastic-compatible GPS | **Required.** Any module supported by the base firmware will work. The u-blox M8N is recommended for its high accuracy. |
| **Magnetometer** | QMC5883L | **Highly Recommended.** The directional arrow makes finding friends in crowded spaces much easier. Other magnetometers may work but are untested. |

> **IMPORTANT: Magnetometer Wiring**
> If you choose to install a magnetometer, it **must** be connected to the primary I²C bus. Other ports were tested without success.
> ```text
| Magnetometer | Pin | Heltec V3 | Pin |
| :--- | :---: | :--- | ---: |
| **SDA** | -> | **GPIO 41** | |
| **SCL** | -> | **GPIO 42** | |
> ```

---

## 💾 Installation

The easiest way to install this firmware is by using the custom web flasher.

### **➡️ [Install via Web Flasher](https://leapyeet.github.io/Meshtastic-Firmware-Friend-Finder-Edition/)**

1.  Click the link above to open the web flasher.
2.  Plug your Heltec V3 into your computer via USB.
3.  Click the **Connect & Install** button.
4.  A pop-up window will appear. Select the correct COM port for your device and click "Connect".
5.  The installation will begin automatically. Do not unplug the device until it is complete.

---

## 🚀 Getting Started: Setup & Usage

1.  **Ensure GPS is Active**
    * Before starting, make sure your GPS module is connected and has acquired a solid satellite lock.

2.  **Calibrate the Magnetometer (If Installed)**
    * This step is only necessary if you have a magnetometer.
    * On the device, navigate to the main menu.
    * Go to `Friend Finder` -> `Compass Cal`.
    * Run both the **Figure-8 Cal** and **Flat-Spin Cal** routines, following the on-screen instructions.
    * **Flat-Spin Cal** requires you to rotate the device **CLOCKWISE** face-up on a table for 15 seconds
    * **Figure-8 Cal** requires you to hold the device at arms length and wave the device in a figure-8 pattern. (Like flying a toy airplane)

3.  **Pair with Friends**
    * From the main menu, go to `Friend Finder` -> `Start Pairing`.
    * Have your friend do the same on their device. The devices will discover each other and allow you to securely pair.

4.  **Track a Friend**
    * Navigate to `Friend Finder` -> `Track a Friend`.
    * Select your friend from the list to begin a mutual tracking session.
    * The device will switch to the tracking screen.

---

## 🚧 Project Status & Future Goals

Please be aware that this entire project is a **work in progress**.

-   **Source Code**: The source code is avalible [**HERE**](https://github.com/LeapYeet/firmware)
-   **End Goal**: The ultimate goal is to refine this module and merge it with the official Meshtastic firmware repository so everyone can benefit from it.
-   **Testing Needed**: Before an official merge is possible, extensive testing is required across different devices, hardware configurations, and LoRa settings. Community feedback and testing are highly encouraged!

---

## 📡 Performance & Technical Notes

-   **LoRa Settings**: All testing has been conducted using the **LongFast** channel preset.
-   **Update Interval**: To keep channel utilization low, position updates are sent every **20 seconds**. Faster LoRa settings may support more frequent updates, but this requires further community testing.
-   **Range**: The effective tracking range depends entirely on your device, antenna, LoRa settings, and the surrounding environment. Hops may not be supported, this hasn't been tested.

---

## 📝 Notes:

1. 
    * If the tracking compass is rotating the wrong way: You need to redo the flat-spin calibration **CLOCKWISE ->**
    * When installing the magnetometer chip to the device, keep it away from other components and wires for better accuracy. Make sure it's firmly secured and flat.
    * As said above, use ports SDA=41, SCL=42. If it doesn't work, try flipping the wires.
    * A decent GPS module is recommended. All testing was done with u-blox m8n chips. My testing showed they were accurate to 1-3m when used outdoors.
    * The Meshtastic Android app is fully usable with this custom firmware.
    * If you want to stop a friend tracking you permanently, you will have to remove them as a friend on the "Track a friend" menu.
    * I recommend a 3000mah battery when paried with a heltec v3 if you want it to last a full day.

---

## Final words:
This project as been my main focus since Feburary 2025. I've had lots of fun developing it and I feel like it will be a great addition to the offical firmware when it's fully polished. It's really exciting to see how everyone will be using it. 

I tested it at a large 1 day music festival in Milton Keynes in august and it worked great. Security didn't know what to think when getting in but saw no issue after showing them how it worked. I was able to walk into the crowd and later find my friends with no issues at all. I simply started a tracking session and the arrow pointed me to the group from 350 meters away.

I love you all, have fun!


## 📜 License

This project is a derivative work of the official Meshtastic firmware and is therefore licensed under the **GNU General Public License v3.0 (GPL-2.0)**. The original `LICENSE` file is included in the source code.
