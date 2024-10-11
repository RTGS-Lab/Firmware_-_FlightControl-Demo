# Flight Control Firmware
The GEMS Sensing v3 Hardware (e.g. (Project Flight)[https://github.com/GEMS-sensing/Project-Flight]) solves the problem of scalable and flexible open source hardware for interfacing with environment sensors over SDI-12, I2C, and analog. This repository provides firmware to drive that hardware system.

# Hardware Platform Overview
The microcontroller for the v3 system is the Particle BSoM M.2 (see [Project-Kestrel](https://github.com/GEMS-sensing/Project-Kestrel?tab=readme-ov-file)). The Particle BSoM M.2 has two I/O expanders (PinsIO Alpha, PinsIO Beta). PinsIOAlpha monitors the Kestrel board itself. PinsIOBeta connects to the five ports/talons indexed (0, 1, 2, 3, 4). Port 4 handles power (e.g. Gonk). Ports 0-3 manage interface boards called "talons".

Three types of interface boards can be plugged into ports 0-3. These include I2C, SDI-12, and AUX. Each has a class that manages the port type, subclassed as a "talon". SDI-12 Talons need to be passed to the sensor in order to function. I2C and AUX talons need to be handled according to their own protocols.

# Firmware Composition
|-- src // has the main controller file
  |-- FlightControl.ino
  |-- FlightControl.cpp
  |-- GlobalPins.h
|-- lib // contains all of the hardware drivers as github submodules
  |-- ...
