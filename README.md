# Kismet ESP32 Scanner 📡
Send Bluetooth (BLE) scans from the [ESP32]() to Kismet!

## Installation
1. [**Flash your ESP32**](https://github.com/LyndLabs/ESP32-BLE-Recon)
2. Download the binary from this repository.

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

## Usage 

For the app, two env variables are needed:
- `KISMETURL`: Location of the kismet server, along with the port.
- `KISMETAPIKEY`: API key with scanreport permissions.

A third optional log env variable can also be specified:
- `ESP32_SOURCE_LOG`: specifies how much logging should be output to terminal. Choice of trace || debug || info || warn || error || off. If env is not specified then this defaults to error.

##### Example:
```bash
# http[s]://[url]:[port]/
$ export KISMETURL=http://localhost:2501/
# [32 char key with scanreport perms]
$ export KISMETAPIKEY=aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa

# trace will incur log "vomit", debug being most useful to a programmer, info might be useful to the user,
# warn, error and off being self-explanatory,
$ export ESP32_SOURCE_LOG=trace 
$ kismet_esp32_source

# or

$ KISMETURL='http://localhost:2501/' KISMETAPIKEY='aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa' kismet_esp32_source
```
## Notes
- Binary depends on libudev on linux hosts, which the majority of linux distributions have installed by default. Alpine has [issues](https://stackoverflow.com/questions/41753218/udevadm-does-not-show-all-attributes-inside-a-docker-container). This will be remidiated in a future release.
