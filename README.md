# Real-Time-Clock
The project involved designing a Real Time Clock (RTC) that displays time in the format HH:MM:SS using Verilog HDL. The clock operates in a 24-hour format, automatically handling carry-over from seconds to minutes and from minutes to hours. It also includes a seven-segment display decoder to visualize the time output on digital displays.

The main goal of this project was to create a simple yet functional digital clock model that counts time accurately using clock pulses as input. It provides a foundational understanding of digital timekeeping systems and hardware-based counters.

The design was verified using Xilinx Vivado, where the simulation and elaboration confirmed the correct time incrementation behavior, rollover logic, and proper seven-segment display outputs.

# Design Overview

The Real Time Clock consists of the following modules:

**Main RTC Counter Module**

- Handles the incrementation of seconds, minutes, and hours.

- Resets correctly after reaching 23:59:59 and starts again from 00:00:00.

**Seven-Segment Display Decoder**

- each 4-bit binary digit (0–9) into a 7-bit segment pattern.

- Outputs signals suitable for display on standard seven-segment displays.

**Testbench Module**

- Simulates the clock signal, reset signal, and observes time transitions.

- Uses $monitor to display the time values at each simulation step.

# Specifications

**Inputs**:

- **clk**: Clock input (used for counting seconds)

- **reset**: Asynchronous reset to initialize the clock to 00:00:00

**Outputs**:

- **hr_m, hr_l**: Hour tens and ones digits

- **min_m, min_l**: Minute tens and ones digits

- **sec_m, sec_l**: Second tens and ones digits

- **seg_hr_m, seg_hr_l, seg_min_m, seg_min_l, seg_sec_m, seg_sec_l**: Seven-segment display encoded outputs

# Significance of the Specifications
**Signal	Description**

- **clk**	Clock input for incrementing time
- **reset**	Resets all values to zero
- **hr_m/hr_l**	Represent hours (00–23)
- **min_m/min_l**	Represent minutes (00–59)
- **sec_m/sec_l**	Represent seconds (00–59)
- **seg_xx_x**	Output to seven-segment display

# Modules
**module RealTimeClock(clk, reset, ...)**

- This is the main clock module that handles the incrementation of seconds, minutes, and hours with proper rollover conditions.
It also integrates a seven-segment decoder to produce outputs for display.

**function seven_seg_decode(input [3:0] digit)**

- This function converts a 4-bit binary value into its equivalent 7-segment display pattern.

**module RTC_tb**

- This is the testbench used to verify the functionality of the RTC module. It simulates the clock signal, applies reset, and monitors outputs during simulation.

# Working

1) The clock signal (clk) provides pulses that simulate one-second intervals.

2) Each positive clock edge increments the seconds counter (sec_l, sec_m).

3) When seconds reach 59, the minutes counter increments by one and seconds reset to 00.

4) Similarly, when minutes reach 59, the hours counter increments by one and minutes reset to 00.

5) After 23:59:59, the system resets to 00:00:00, completing a 24-hour cycle.

6) All outputs are simultaneously decoded into seven-segment display signals.

# Example Output

**Simulation of the clock shows the following transitions**:

Time=863855000 | 23:59:45

Time=863875000 | 23:59:47

Time=863995000 | 23:59:59

Time=864005000 | 00:00:00

Time=864015000 | 00:00:01

Time=864025000 | 00:00:02

The simulation verifies that the time resets correctly from 23:59:59 → 00:00:00 and continues normally.

# Output Synthesis


**Simulation Waveform:**

<img width="1897" height="1212" alt="Screenshot 2025-10-22 190626" src="https://github.com/user-attachments/assets/16dffc86-978f-41b6-8d6d-e34a02b1ab38" />




**Tcl Console Output:**

<img width="1806" height="887" alt="Screenshot 2025-10-22 190748" src="https://github.com/user-attachments/assets/26169a73-fd1b-42c3-9ef5-39ad4fda4a75" />



**RTL Schematic:**

<img width="1893" height="1182" alt="Screenshot 2025-10-22 190508" src="https://github.com/user-attachments/assets/c9436932-76c2-4be7-ac6d-43c49a24c7b1" />


# Future Enhancements

1) Add alarm functionality

2) Include real-time synchronization using external RTC modules (like DS3231)

3) Display time on physical FPGA 7-segment displays

# Author

Chetan Sanapala - http://www.linkedin.com/in/chetansanapala07
