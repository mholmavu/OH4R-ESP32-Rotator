# OH4R-ESP32-Rotator

ESP32 based MQTT controllable rotator implementation, contains two parts:
1) ESP32 based remote unit (headless) receives MQTT messages, integrates peripherals and controls rotator via relays
2) user interface module, ESP32 unit including UI if manual controls are needed (eg. specific contesting use cases)

Node-RED ready, remote unit can be controlled purely via Node-RED dashboards

Currently only azimuthal support implemented

## Overview of MQTT commands

The MQTT topics will follow a hierarchical structure to ensure clarity and organization. The base topic will be `rotator/**id**/`.
Each device will have unique ID when joining / subsribing to MQTT bus

### Command Topics
Commands will be published to control the antenna rotator. The command topics will include:

- `rotator/id/command/move_azimuth`: Command to rotate the antenna to heading in payload.
- `/rotator/id/command/stop`: Command to stop the antenna rotation.
- `/rotator/id/command/rotate_CW`: Command to turn to CW until STOP command
- `/rotator/id/command/rotate_CCW`: Command to turn to CCW until STOP command
- `/rotator/id/command/park`: Command to park mast/antenna to defined PARK position
- `/rotator/id/command/reset`: Reset remote unit (MCU reset)
- `/rotator/id/command/ping`: Reset remote unit (MCU reset)

### Status Topics
Status updates from the antenna rotator will be published to the following topics:

- `/rotator/id/status/position`: Current position of the antenna.
- `/rotator/id/status/status`: Current status of the rotator (e.g., rotating, stopped, error).
- `/rotator/id/status/error`: Any error messages or codes.

### Configuration Topics
Configuration settings for the antenna rotator will be published and subscribed to the following topics:

- `/rotator/id/config/`: 


## MQTT Commands

### Rotate Command
**Topic:** `rotator/id/command/move_azimuth`  
**Payload:** JSON object containing the direction and angle to rotate.
```json
{  
  "angle": <angle in degrees>
}
