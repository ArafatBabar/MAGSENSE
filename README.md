# MAGSENSE

MagSense is a multi-sensor magnetic field imaging platform designed for scientific measurement, magnetic field visualization, and educational research. The hardware simultaneously acquires data from five high-resolution MMC5983MA magnetometers to create real-time maps of magnetic fields.

*Note: This repository serves as a project overview, documenting our system architecture, the challenges we faced during development, and suggestions for future iterations. The schematic is provided for reference, though the final PCB layout is currently pending validation.*

## Project Goals & Achievements
The primary objective of MagSense was to build an array of magnetic sensors capable of capturing a localized magnetic field and visualizing it in real-time. We successfully achieved:
*   **Multi-Sensor Integration:** Coordinated reading of five independent MMC5983MA sensors over a single SPI bus.
*   **High-Speed Data Acquisition:** Maintained a continuous, zero-lag data stream from the microcontroller to the host PC at a baud rate of 921600.
*   **Real-Time Visualization:** Developed a custom Python-based desktop studio that successfully translates raw X, Y, Z magnetic data into interactive 2D heatmaps and 3D surface plots.

## System Architecture

### Hardware Design
The system is built around an **ESP32 DevKit V1**, chosen for its clock speed and processing capabilities. It acts as the central controller for five **MMC5983MA** magnetometers. These specific sensors were selected for their high resolution and low noise characteristics, making them ideal for precise field mapping. 

### Software Implementation (Conceptual)
The software was split into two distinct pipelines to handle the heavy data load:
1.  **The Firmware (ESP32):** Written in C++, the firmware handles the low-level hardware abstraction. It rapidly polls all five sensors via SPI, packages the raw coordinates into a structured data payload, and pushes it over a high-speed serial connection. 
2.  **The Desktop Studio (Python):** Acting as the visualization engine, the Python UI listens to the incoming serial stream, parses the packets, and feeds the data into a GUI framework. This allows the system to render live 3D surface maps and 2D heatmaps without interrupting the data acquisition process.

## Challenges & Difficulties Encountered
Developing a multi-sensor, high-speed streaming platform came with several technical hurdles:
*   **SPI Bus Capacitance & Speed:** Running five sensors on a shared SPI bus introduced signal integrity and capacitance challenges. Ensuring clean Chip Select (CS) toggling and stable clock speeds required careful timing considerations in the firmware.
*   **Data Synchronization:** Reading five independent sensors meant we had to ensure the data was sampled as close to simultaneously as possible to prevent "tearing" or lag in our visual 3D maps.
*   **Serial Bottlenecks:** Standard baud rates (like 115200) were completely insufficient for the volume of data being generated. We had to push the serial transmission to 921600 baud, which required careful handling on the Python side to prevent buffer overflows.
*   **GUI Rendering Performance:** Plotting 3D surfaces in real-time is computationally expensive. We had to optimize our Python visualization loops to ensure the GUI didn't freeze or drop frames while processing the incoming serial stream.

## Future Suggestions & Improvements
For anyone looking to replicate or expand upon this project, we recommend the following improvements:
*   **PCB Layout Validation:** The current schematic works on a breadboard/prototype level, but a properly routed PCB is essential to minimize SPI noise and interference between the closely packed sensors.
*   **Direct Memory Access (DMA):** Future firmware iterations should utilize ESP32 SPI DMA to offload the sensor reading from the main CPU, allowing for even faster polling rates.
*   **UI Optimization:** While the Python studio works, migrating the visualization engine to a more performant graphics framework (or a compiled language) would allow for even smoother 3D rendering and the integration of more sensors.
