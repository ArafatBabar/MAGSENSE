# MagSense

> Open-source magnetic field imaging platform.

---

## Overview

MagSense is a compact magnetic field imaging platform designed for scientific measurement, visualization, and experimentation.

The hardware combines five high-resolution 3-axis magnetometers with an STM32G431 microcontroller to acquire magnetic field data and stream it over USB to a desktop application for visualization and analysis.

---

## Hardware

- STM32G431CBT6
- 5 × MMC5983MA 3-axis magnetometers
- TMP112 temperature sensor
- USB Type-C (USB CDC)
- TPS2115A power multiplexer
- TPS7A02 3.3V LDO
- CAN interface
- Qwiic expansion connector
- WS2812 status LED
- 4-layer PCB

---

## Planned Software Features

- Live magnetic field visualization
- Heatmaps
- Vector field rendering
- Gradient estimation
- Calibration
- Data logging
- Session replay

---

## Current Status

- [x] System Architecture
- [x] Schematic Design
- [x] PCB Layout (Rev.2)
- [ ] PCB Manufacturing
- [ ] Hardware Bring-up
- [ ] Firmware
- [ ] Desktop Application
- [ ] Calibration

---
