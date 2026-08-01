# MagSense

<p align="center">
<img src=""C:\Users\babar\Documents\GitHub\MAGSENSE\Images\IMG_20260801_172536.png"" />
" width="750">
</p>

<p align="center">

**An open-source multi-sensor magnetic field imaging platform.**

</p>

---

## Overview

MagSense is designed to measure the spatial distribution of magnetic fields rather than a single magnetic field value.

Instead of relying on one sensor, MagSense uses a synchronized array of five high-resolution magnetometers to capture magnetic field information at multiple locations simultaneously. This enables magnetic field visualization, gradient estimation and future magnetic source localization algorithms.

The project is being developed as an open-source hardware platform intended for research, education and experimentation.

---

# What's New in Rev.2

Rev.2 is a complete hardware redesign focused on improving signal integrity, reliability and manufacturability.

### Hardware Changes

- Migrated to STM32G431 with native USB support
- Redesigned 4-layer PCB architecture
- Added USB Type-C interface with ESD protection
- Implemented automatic power source selection
- Integrated CAN transceiver for future industrial communication
- Added Qwiic expansion connector
- Added onboard temperature sensor for future compensation
- Added RGB status indicator
- Improved debugging interface and test points
- Optimized routing for the magnetometer array

---

# Hardware

| Component | Device |
|------------|----------------|
| MCU | STM32G431CBT6 |
| Magnetometers | 5 × MMC5983MA |
| Temperature Sensor | TMP112 |
| USB | Native USB FS |
| Power MUX | TPS2115A |
| LDO | TPS7A0233 |
| CAN | TLT9251 |
| Expansion | Qwiic |

---

# Sensor Geometry

```
        Top

Left   Center   Right

      Bottom
```

Each outer sensor is positioned 20 mm from the center.

All sensors maintain identical orientation to simplify calibration and gradient calculations.

---

# Why Five Sensors?

Most low-cost magnetic sensing platforms use a single sensor and can only report the magnetic field at one location.

MagSense measures the magnetic field at five synchronized points, allowing future implementation of:

- Magnetic field interpolation
- Gradient estimation
- Vector field visualization
- Magnetic source localization
- Multi-point magnetic field analysis

---

# Repository

```
Hardware/
Firmware/
Software/
Documentation/
```

---

# Current Status

## Hardware

- [x] Architecture
- [x] Schematic
- [x] PCB Layout (Rev.2)
- [ ] PCB Fabrication
- [ ] Bring-up
- [ ] Validation

---

## Next Steps

- Prototype manufacturing
- Hardware validation
- Firmware development
- Sensor calibration
- Desktop visualization software

---

## License

Hardware: CERN-OHL-S v2

Firmware & Software: MIT
