# STM32-Jetson-IGV-Robot-Platform

A full-stack embedded robotics platform that combines register-level firmware development on STM32, wireless communication via ESP32, and AI/vision-ready high-level processing on Jetson Nano.

## Project Overview

This project is a modular Intelligent Ground Vehicle (IGV) base platform built for real-world embedded system integration. It was designed and developed end-to-end, including mechanical assembly, power electronics, motor control firmware, inter-controller communication, and high-level compute integration.

The objective was to create a scalable robot architecture that is stable under load, easy to expand, and ready for autonomy and AI workloads.

## System Architecture

### Multi-Controller Design

- **STM32F407 (Bare Metal):** Real-time motor control, sensor interfacing, low-level firmware
- **ESP32:** Wireless communication bridge (Wi-Fi/Bluetooth), telemetry-ready interface
- **Jetson Nano Super 8GB:** High-level compute for camera, AI inference, and decision logic

### Communication Interfaces

- UART (STM32 <-> ESP32 <-> Jetson)
- SPI / I2C (sensor and peripheral expansion)
- GPIO (direction control, status, control lines)

### Software Layering

- Low-level hardware drivers
- Middleware for communication and control
- High-level Linux/Python processing on Jetson

## Mechanical and Drive Platform

- Aluminum extrusion T-slot chassis (modular and serviceable)
- 4-wheel mecanum drive for omnidirectional motion
- High-torque geared DC motors with precision mounting
- Motion support for:
  - Forward / reverse
  - Lateral translation
  - In-place rotation
  - Vector-based mixed motion

## Motor Control and Embedded Firmware

### STM32 Firmware (Embedded C, Bare Metal)

- Custom register-level drivers:
  - GPIO, UART, SPI, I2C
  - Timer, PWM, ADC
- Interrupt-driven architecture with prioritized ISR handling
- Timer-based cooperative scheduling (bare-metal task framework)
- Quadrature encoder-ready closed-loop design
- PID-ready motor control architecture
- Fault handling and watchdog integration path
- Modular driver + application separation for scalability

### Motor Driver Integration

- High-current motor control with dual driver modules
- PWM speed control + GPIO direction control
- Heat sink assisted thermal management
- Encoder feedback hardware-ready for accurate speed estimation

## Jetson Application Layer

- Jetson Nano Super 8GB Linux environment
- High-level control logic in Python
- Serial control link to STM32
- Camera integration pipeline for real-time streaming
- Ready for:
  - OpenCV image processing
  - YOLO-based object detection
  - GPU-accelerated AI inference

## Power and Electronics Design

- Battery-powered architecture (4S LiPo / Li-ion class pack)
- Multi-rail power distribution:
  - Motor rail (high current)
  - 5V logic rail
  - 3.3V sensor/controller rail
- DC-DC buck conversion and distribution blocks
- XT60 connectors + terminal blocks for robust wiring
- Domain-aware separation between motor noise and logic electronics
- Protection and reliability features:
  - Fuse protection
  - Reverse polarity protection (implemented/planned by stage)
  - Current monitoring support

## Communication and Telemetry

- ESP32 Wi-Fi control channel for remote operation
- UART bridge forwarding between subsystems
- Telemetry-ready architecture for remote monitoring
- Expandable path for MQTT/cloud logging workflows

## Development Workflow

- Incremental bring-up strategy:
  - Power system validation
  - Motor actuation tests
  - Firmware and control loop validation
  - Communication link validation
- Rapid prototyping on breadboard/proto board before permanent integration
- Debugging workflow:
  - UART logging
  - Multimeter and oscilloscope-based electrical verification
  - Iterative software-hardware tuning

## Tools and Technologies

- **Firmware:** Embedded C, bare-metal STM32 firmware development
- **Boards/Compute:** STM32F407, ESP32, Jetson Nano Super 8GB
- **Software:** STM32CubeIDE, Arduino IDE, Python, Linux
- **Vision/AI Stack:** OpenCV, GStreamer pipeline support, YOLO-ready integration
- **Version Control:** Git, GitHub
- **Debugging Tools:** Logic analyzer, multimeter, oscilloscope

## Key Engineering Highlights

- Designed and integrated a complete multi-controller robot architecture
- Built a robust motor + power control stack suitable for high-current loads
- Developed low-level firmware drivers and control logic from scratch
- Integrated Jetson as a high-level AI/vision compute node
- Delivered a modular platform ready for autonomous robotics extensions

## Project Gallery

### Full Robot Assembly and Compute Unit

![Jetson compute unit build](Images/WhatsApp%20Image%202026-04-20%20at%205.10.11%20PM.jpeg)
![Integrated robot platform](Images/WhatsApp%20Image%202026-04-20%20at%205.10.11%20PM%20(1).jpeg)
![Robot front profile](Images/WhatsApp%20Image%202026-04-20%20at%205.10.11%20PM%20(2).jpeg)
![Alternate robot integration view](Images/WhatsApp%20Image%202026-04-20%20at%205.10.12%20PM%20(1).jpeg)
![Jetson + control electronics integration](Images/WhatsApp%20Image%202026-04-20%20at%205.10.12%20PM.jpeg)
### Chassis, Drive, and Electronics Integration

![IGV chassis and motor layout](Images/WhatsApp%20Image%202026-04-20%20at%205.10.09%20PM%20(1).jpeg)
![Top integration view](Images/WhatsApp%20Image%202026-04-20%20at%205.10.09%20PM%20(2).jpeg)
![Wired platform integration](Images/WhatsApp%20Image%202026-04-20%20at%205.10.09%20PM.jpeg)
![Drive and electronics side view](Images/WhatsApp%20Image%202026-04-20%20at%205.10.10%20PM%20(1).jpeg)
![Electronics top view](Images/WhatsApp%20Image%202026-04-20%20at%205.10.10%20PM%20(2).jpeg)
![Mechanical base frame](Images/WhatsApp%20Image%202026-04-20%20at%205.10.10%20PM.jpeg)
