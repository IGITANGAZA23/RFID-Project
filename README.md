# IoT RFID Architecture - Team Shield

Efficient bridging of RFID hardware with a web dashboard using MQTT and WebSockets.

## Live site
- http://157.173.101.159:9201/

## MQTT Topics
- `rfid/iot_shield_2026/card/status`: ESP8266 publishes card UID and balance when detected.
- `rfid/iot_shield_2026/card/topup`: Backend publishes top-up commands.
- `rfid/iot_shield_2026/card/balance`: ESP8266 publishes confirmation of balance update.
- `rfid/iot_shield_2026/device/status`: MQTT Last Will (online/offline).
- `rfid/iot_shield_2026/device/health`: Periodic health metrics (IP, RSSI, Memory).

## HTTP API Endpoints
- `GET /balance/:uid`: Retrieve the current balance for a specific card.
- `POST /topup`: Send a top-up command (`uid`, `amount`) to the MQTT broker.

## Hardware Connections (ESP8266 + RC522)
| RC522 Pin | ESP8266 Pin (NodeMCU) | Function |
|-----------|-----------------------|----------|
| 3.3V      | 3V3                   | Power    |
| RST       | D3 (GPIO0)            | Reset    |
| GND       | GND                   | Ground   |
| MISO      | D6 (GPIO12)           | SPI MISO |
| MOSI      | D7 (GPIO13)           | SPI MOSI |
| SCK       | D5 (GPIO14)           | SPI Clock|
| SDA (SS)  | D4 (GPIO2)            | SPI SS   |

