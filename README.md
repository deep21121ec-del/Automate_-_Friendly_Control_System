# Automate_-_Friendly_Control_System
IoT-based smart home automation system with environmental monitoring and appliance control using ESP8266/ESP32, Blynk, and SinricPro platforms
# IoT Smart Home Automation System

A complete IoT-based smart home automation solution featuring environmental monitoring and intelligent appliance control. This project combines two ESP modules to create a comprehensive home automation ecosystem.

## System Overview

This repository contains two integrated systems:

1. **Smart Agriculture Monitoring System** - Environmental sensing and automation
2. **CONTROL - Automate & Friendly Control System** - Multi-appliance voice and manual control

## Features

### Environmental Monitoring System (ESP8266)
- **Temperature & Humidity Monitoring** - DHT11 sensor integration
- **Soil Moisture Detection** - Analog and digital moisture sensing
- **Rain Detection** - Automatic rain sensing with notifications
- **Motion Detection** - PIR sensor for security and automation
- **Automated Motor Control** - Smart irrigation based on conditions
- **Real-time Monitoring** - Blynk IoT dashboard integration
- **Smart Notifications** - Event-based alerts for critical conditions

### Appliance Control System (ESP32)
- **4-Channel Relay Control** - Control up to 4 appliances
- **Voice Control** - Integration with Alexa/Google Assistant via SinricPro
- **Manual Override** - Physical switches for local control
- **Dual Control Mode** - Both app-based and physical switch operation
- **WiFi Connectivity** - Remote control from anywhere
- **State Persistence** - Remembers device states across power cycles

## Hardware Requirements

### For Environmental Monitoring (ESP8266)
- NodeMCU ESP8266
- DHT11 Temperature & Humidity Sensor
- Soil Moisture Sensor (Analog + Digital)
- Rain Sensor Module
- PIR Motion Sensor
- Relay Module (for motor control)
- Water pump/motor (optional)

### For Appliance Control (ESP32)
- ESP32 Development Board
- 4-Channel Relay Module
- 4x Push Buttons/Toggle Switches
- AC Appliances (lights, fans, etc.)

## Pin Configuration

### ESP8266 (Monitoring System)
| Component | Pin |
|-----------|-----|
| DHT11 Sensor | D4 |
| Rain Sensor | D1 |
| Moisture Sensor (Digital) | D3 |
| Moisture Sensor (Analog) | A0 |
| PIR Sensor | D2 |
| Motor Relay | D0 |

### ESP32 (Control System)
| Component | Relay Pin | Switch Pin |
|-----------|-----------|------------|
| Device 1 | GPIO 23 | GPIO 13 |
| Device 2 | GPIO 22 | GPIO 12 |
| Device 3 | GPIO 21 | GPIO 14 |
| Device 4 | GPIO 19 | GPIO 27 |
| WiFi LED | GPIO 2 | - |

## Software Requirements

- Arduino IDE (1.8.x or higher)
- ESP8266 Board Package
- ESP32 Board Package

### Libraries Required

**For ESP8266 Monitoring System:**
- ESP8266WiFi
- BlynkSimpleEsp8266
- DHT sensor library
- Adafruit Unified Sensor

**For ESP32 Control System:**
- WiFi (ESP32)
- SinricPro
- SinricProSwitch

## Installation & Setup

### 1. Arduino IDE Setup

Add board manager URLs:
https://arduino.esp8266.com/stable/package_esp8266com_index.json
https://dl.espressif.com/dl/package_esp32_index.json

text

### 2. Install Libraries

Open Arduino IDE → Sketch → Include Library → Manage Libraries

Search and install the required libraries listed above.

### 3. Configure Monitoring System

Open `SmartAgricultureMonitoring_ESP8266.ino` and update:

#define BLYNK_TEMPLATE_ID "YOUR_TEMPLATE_ID"
#define BLYNK_DEVICE_NAME "YOUR_DEVICE_NAME"
#define BLYNK_AUTH_TOKEN "YOUR_AUTH_TOKEN"

char ssid[] = "YOUR_WIFI_SSID";
char pass[] = "YOUR_WIFI_PASSWORD";

text

### 4. Configure Control System

Open `CONTROL-Automate-Friendly-Control-System.ino` and update:

#define WIFI_SSID "YOUR_WIFI_SSID"
#define WIFI_PASS "YOUR_WIFI_PASSWORD"
#define APP_KEY "YOUR_SINRIC_APP_KEY"
#define APP_SECRET "YOUR_SINRIC_APP_SECRET"

#define device_ID_1 "SWITCH_ID_NO_1_HERE"
#define device_ID_2 "SWITCH_ID_NO_2_HERE"
#define device_ID_3 "SWITCH_ID_NO_3_HERE"
#define device_ID_4 "SWITCH_ID_NO_4_HERE"

text

### 5. Blynk Setup (Monitoring System)

1. Create account at [Blynk.io](https://blynk.io)
2. Create new template and device
3. Configure virtual pins:
   - V0: Motor Control (Button)
   - V1: Temperature (Display)
   - V2: Humidity (Display)
   - V3: Soil Moisture (Gauge)

### 6. SinricPro Setup (Control System)

1. Create account at [SinricPro.com](https://sinric.pro)
2. Create 4 smart switch devices
3. Link with Alexa or Google Home
4. Copy device IDs to code

## Upload Instructions

1. Connect ESP8266/ESP32 to computer via USB
2. Select correct board and port in Arduino IDE
3. Click Upload button
4. Monitor serial output at 115200 baud (ESP8266) or 9600 baud (ESP32)

## Usage

### Monitoring System
- Access Blynk app to view sensor data
- Control motor manually or automatically
- Receive notifications for rain, moisture levels, and motion

### Control System
- Use voice commands: "Alexa, turn on Device 1"
- Use physical switches for manual control
- Control via SinricPro mobile app

## Features in Detail

### Automatic Irrigation
The system automatically turns off the motor when rain is detected and provides notifications when soil moisture is low.

### Motion Detection
PIR sensor detects motion with automatic reset after 60 seconds of no activity.

### Debounce Protection
Physical switches include 250ms debounce protection to prevent false triggers.

## Circuit Diagrams

*Add your circuit diagrams here*

## Troubleshooting

**WiFi Connection Issues:**
- Verify SSID and password
- Check WiFi signal strength
- Ensure 2.4GHz network (ESP8266/32 don't support 5GHz)

**Sensor Reading Issues:**
- Check wiring connections
- Verify sensor power supply
- Test sensors individually

**Relay Not Switching:**
- Check relay module power supply
- Verify GPIO pin connections
- Test relay module separately

## Future Enhancements

- [ ] Add MQTT support for local control
- [ ] Implement OTA (Over-The-Air) updates
- [ ] Add energy monitoring
- [ ] Create unified web dashboard
- [ ] Add scheduling features
- [ ] Implement geofencing

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open source and available under the MIT License.

## Acknowledgments

- Blynk IoT Platform
- SinricPro Voice Control Platform
- Arduino Community
- ESP8266/ESP32 Community

## Contact

For questions or support, please open an issue in this repository.

---

**⭐ If you find this project helpful, please consider giving it a star!**
