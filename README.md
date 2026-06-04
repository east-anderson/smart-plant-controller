# Smart Plant Environmental Controller

An embedded environmental monitoring and irrigation control system designed to help maintain healthy plant conditions using real-time sensor feedback, automatic watering, local display output, and planned wireless data logging.

This is a personal project being developed as a practical, resume-worthy embedded systems project focused on sensor integration, control logic, low-voltage hardware design, data logging, and system documentation.

## Project Status

**Current status:** Planning and initial repository setup  
**Hardware build:** Not started  
**Firmware:** Not started  
**Target completion:** Summer 2026

## Project Goals

The goal of this project is to build an affordable and safe smart plant controller that can monitor a plant's environment and automatically control watering based on soil moisture conditions.

Planned features include:

- Soil moisture sensing
- Temperature and humidity sensing
- Ambient light sensing
- Automatic watering using a small low-voltage pump
- Manual watering override button
- Low-water reservoir detection
- OLED display for live system status
- Wi-Fi dashboard for monitoring
- CSV data logging
- Pump cooldown and overwatering protection
- Optional grow light control
- Optional solar-assisted battery charging

## Planned System Overview

The system will use an ESP32-based microcontroller to read environmental sensors, determine whether watering is needed, control a small pump through a MOSFET driver circuit, and display real-time status information on an OLED screen.

The control logic will be designed to avoid overwatering by using threshold-based soil moisture checks, timed pump activation, cooldown periods, and post-watering re-checks.

```text
+------------------------------------------------------+
|            Smart Plant Environmental Controller       |
|                                                      |
|  +------------------+                                |
|  |  Soil Moisture   |                                |
|  |  Sensor          |                                |
|  +--------+---------+                                |
|           |                                          |
|  +--------v---------+        +--------------------+  |
|  |                  |        | Temperature /      |  |
|  |      ESP32       |<-------+ Humidity Sensor    |  |
|  |                  |        +--------------------+  |
|  |  Control Logic   |                                |
|  |  Wi-Fi Dashboard |        +--------------------+  |
|  |  Data Logging    |<-------+ Light Sensor       |  |
|  |                  |        +--------------------+  |
|  +---+----------+---+                                |
|      |          |                                    |
|      |          |                                    |
|      v          v                                    |
| +---------+  +------------------+                    |
| | OLED    |  | MOSFET Pump      |                    |
| | Display |  | Driver Circuit   |                    |
| +---------+  +--------+---------+                    |
|                       |                              |
|                       v                              |
|                +-------------+                       |
|                | 5V Water    |                       |
|                | Pump        |                       |
|                +-------------+                       |
|                                                      |
| +------------------+      +------------------------+ |
| | Manual Override  |      | Low Water Detection    | |
| | Button           |      | Float Switch / Sensor  | |
| +------------------+      +------------------------+ |
|                                                      |
+------------------------------------------------------+
