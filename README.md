# OH4R-ESP32-Rotator

ESP32 based MQTT controllable rotator implementation, contains two parts:
1) ESP32 based remote unit (headless) receives MQTT messages, integrates peripherals and controls rotator via relays
2) user interface module, ESP32 unit including UI if manual controls are needed (eg. specific contesting use cases)

Node-RED ready, remote unit can be controlled purely via Node-RED dashboards
