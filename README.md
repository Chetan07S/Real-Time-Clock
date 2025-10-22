# Real-Time-Clock
The project involved designing a Real Time Clock (RTC) that displays time in the format HH:MM:SS using Verilog HDL. The clock operates in a 24-hour format, automatically handling carry-over from seconds to minutes and from minutes to hours. It also includes a seven-segment display decoder to visualize the time output on digital displays.

The main goal of this project was to create a simple yet functional digital clock model that counts time accurately using clock pulses as input. It provides a foundational understanding of digital timekeeping systems and hardware-based counters.

The design was verified using Xilinx Vivado, where the simulation and elaboration confirmed the correct time incrementation behavior, rollover logic, and proper seven-segment display outputs.

Design Overview

The Real Time Clock consists of the following modules:

Main RTC Counter Module

Handles the incrementation of seconds, minutes, and hours.

Resets correctly after reaching 23:59:59 and starts again from 00:00:00.

Seven-Segment Display Decoder

Converts each 4-bit binary digit (0–9) into a 7-bit segment pattern.

Outputs signals suitable for display on standard seven-segment displays.

Testbench Module

Simulates the clock signal, reset signal, and observes time transitions.

Uses $monitor to display the time values at each simulation step.
