# Kismet ESP32 Scanner 📡
Send Bluetooth (BLE) scans from the [ESP32]() to Kismet!

## Installation & Usage
1. [**Flash your ESP32**](https://github.com/LyndLabs/ESP32-BLE-Recon)
2. `Coming soon`

## Description
This app parses JSON streams over serial, and uses the Kismet [Scan Report API](https://www.kismetwireless.net/docs/api/bluetooth_scanningmode/) to send Bluetooth recon to the web interface!

#### JSON Fields:
- `ID`: ESP32's MAC Address
- `FW`: Firmware version from config.yaml
- `TYPE`: BT, BLE, iBeacon, Eddystone
- `UUID`: Unique BT Address, if applicable
- `MFR`:  Manufacturer, if found
- `NAME`: Bluetooth Device Name
- `MAC`: MAC Address
- `RSSI`:  Signal Strength
- `TX`: Reported TX power at 1 Meter, if broadcasted.
