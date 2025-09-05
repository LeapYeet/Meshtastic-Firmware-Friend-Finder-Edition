Meshtastic Firmware: Friend Finder Edition
An enhanced version of the Meshtastic firmware featuring a real-time, compass-based module to track your friends in off-grid environments.

This custom build of the official Meshtastic firmware introduces the Friend Finder module. Developed over several months, this feature adds previously unsupported magnetometer (compass) capabilities to Meshtastic, allowing you to pair with and track your friends in real-time. The simple tracking screen shows the distance to your friend and a large directional arrow, making it easy to find each other when you get separated.

It was developed and tested in real-world conditions, including a crowded outdoor music concert, where it performed exceptionally well.

🎯 Core Features
Friend Finder Module: A new interface to securely pair with other Meshtastic devices and initiate a tracking session.

Real-Time Tracking Screen: A dedicated screen that shows the distance to your friend and a large arrow pointing in their direction. No more guessing which way to go!

Magnetometer (Compass) Support: This firmware includes the necessary drivers and logic to use a QMC5883L magnetometer with your device, a feature not yet available in the main Meshtastic repository.

Friend Map: View the locations of all your paired friends simultaneously on a simple map display.

Designed for the Outdoors: Perfect for staying connected with your group at festivals, while skiing or snowboarding, hiking in the backcountry, or at any large-scale event.

⚙️ Hardware Requirements
For the Friend Finder module to work correctly, specific hardware is required. The firmware was built and tested on the following setup:

Primary Device: Heltec Wireless Tracker (V3)

GPS Module: A u-blox M8N or any other functional GPS module is required. The device must have a satellite lock for location sharing to work.

Magnetometer: A QMC5883L magnetometer is required for the directional arrow to function.

Magnetometer Wiring
The magnetometer must be connected to the primary I²C bus. I could not get it working on other ports, though it may be possible with further development.

SDA Pin: Connect to GPIO 41

SCL Pin: Connect to GPIO 42

💾 Installation
The easiest way to install this firmware is by using the custom web flasher.

[Link to Your Web Flasher Here]

Click the link above to open the web flasher.

Plug your Heltec V3 into your computer via USB.

Click the "Connect & Install" button on the web page.

A pop-up window will appear. Select the correct COM port for your device and click "Connect".

The installation process will begin automatically. Do not unplug the device until it is complete.

🚀 Getting Started: Setup & Usage
After installation, you must calibrate the magnetometer before the tracking screen will work correctly.

Ensure GPS is Active: Before starting, make sure your GPS module is connected and has acquired a solid satellite lock.

Calibrate the Magnetometer: This step is mandatory.

Press the device button to open the main menu.

Navigate to Friend Finder -> Compass Cal.

Run both the Figure-8 Cal and Flat-Spin Cal routines, following the on-screen instructions. The device will tell you to move it in a figure-8 pattern and then spin it on a flat surface.

Once calibrated, you can also use the Set North Here option to align the compass if needed.

Pair with Friends:

From the main menu, go to Friend Finder -> Start Pairing.

Have your friend do the same on their device. The devices will discover each other and allow you to securely pair.

Track a Friend:

Navigate to Friend Finder -> Track a Friend.

Select your friend from the list to begin a mutual tracking session.

The device will switch to the tracking screen, showing the distance and a large arrow pointing towards them.

📡 Performance & Technical Notes
LoRa Settings: All testing has been conducted using the LongFast channel preset.

Update Interval: To keep channel utilization below 10-15%, position updates are sent every 20 seconds. Other, faster LoRa settings may support more frequent updates, but this will require further testing by the community.

Range: The effective tracking range depends entirely on your device, antenna, LoRa settings, and the surrounding environment (line-of-sight, obstructions, etc.).

📜 License
This project is a derivative work of the official Meshtastic firmware and is therefore licensed under the GNU General Public License v2.0 (GPL-2.0). The original LICENSE file is included in the source code. Your contributions are welcome under the same license.
