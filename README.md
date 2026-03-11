# ESP32-S3 Keyboard & Mouse to Gamepad Adapter

Convert a USB keyboard and mouse into a wireless Xbox-style Bluetooth gamepad using an ESP32-S3.
Configure every binding, sensitivity, macros, and profiles through a built-in Wi-Fi configuration page.

<img width="1068" height="1261" alt="webUI" src="https://github.com/user-attachments/assets/65610d99-1ec1-4418-a884-e21110ae10f7" />

## Hardware

| Part | Notes |
|---|---|
| **ESP32-S3** dev board | Tested on ESP32-S3-DevKitC-1 |
| **USB Hub** | Connect keyboard and mouse to the single USB-OTG port |
| USB keyboard | Any standard HID boot-protocol keyboard |
| USB mouse | Any standard HID boot-protocol mouse |

> **Why ESP32-S3?** It is the only ESP32 variant with a built-in USB OTG controller capable of acting as a USB host. Standard ESP32, S2, and C3 do not support USB host without an external controller IC.

1. To enable OTG capabilities on the ESP32, bridge the two pins labeled `USB-OTG` with solder.
2. Power the ESP32-S3 through its USB-C power port (`COM`) or with a 5V power source via the 5V/GND pins.
> The USB-OTG port on the ESP32-S3 is the second USB port (labelled `USB`).
3. Connect your USB Hub to a USB-C OTG cable. Connect the OTG cable to the `USB` USB-C port on the ESP32.
4. Connect your USB mouse and keyboard to the hub.

## Flash the firmware

1. Connect your ESP32 to a PC using the `COM` USB-C port.
2. Go to https://web.esphome.io/ (use Chrome or Edge).
3. Click **Connect**, select your COM port and click **Connect**.
4. Click **Install**.
5. Click **Choose file** and select the [ESP32 Gamepad firmware file](https://github.com/kaminoer/ESP32-Gamepad/releases) you downloaded.
6. Click **Install** and wait for the process to complete.
7. Once the installation is completed, power cycle the ESP32.

## First-Time Setup

1. After flashing, the ESP32 creates a Wi-Fi AP:
   - **SSID:** `ESP32-Gamepad`
   - **Password:** `gamepad19`

2. Connect to that network and open **http://192.168.4.1**

3. From the config page you can:
   - Rebind any button (click a slot on the controller diagram or binding table, then press a key)
   - Adjust mouse sensitivity and joystick dead-zone
   - Create macros (one key triggers multiple buttons)
   - Save/load profiles
  
    Remember to save your changes. 

4. Pair with the ESP32 (`ESP32 Gamepad` in v0.1 or `Xbox Wireless Controller` in v0.2) in Bluetooth settings on your phone.

5. Once configured, click **Disable WiFi Hotspot** for minimum input latency.
   To reconfigure later, power-cycle the ESP32 — the hotspot reactivates on boot.
