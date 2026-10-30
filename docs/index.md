---
title: Welcome
tags:
- tag1
- tag2
---
<center>
<font size= "6">Gabriel Toneser Facchin</font><br>
as part of<br>
<font size= "8"> GripRx</font><br>
for<br>
<font size= "5"> Team 103 </font><br>

**Submission: month, DD, YYYY**
</center>

## Introduction

* This datasheet documents the design and development of the Motor Board for GripRx, a team project developed in EGR 304 – Embedded Systems Design at Arizona State University.

The purpose of this document is to present the Motor Board's electrical architecture, component selection, schematic design, power requirements, and integration with the other subsystems. It provides technical information supporting the design, implementation, and testing of the motor control system.

### Project Summary

* GripRx is a proposed rehabilitation device designed to provide adjustable resistance for hand-grip exercises. The system is divided into three main subsystems: the User Interface Board, Force Board, and Motor Board.

The User Interface Board allows the user to select exercise settings. The Force Board measures the applied force and communicates control and safety information. The Motor Board adjusts the resistance mechanism by controlling a DC gear motor.

The Motor Board uses a Microchip PIC18F57Q43 Curiosity Nano microcontroller to control a Texas Instruments DRV8871DDAR H-bridge driver and a DFRobot FIT0492-A DC gear motor. Two Omron D2F-01L limit switches detect the mechanical travel limits.

The planned system uses a 9V, 3A DC power supply provided by the professor, along with an L7805ABV-DG voltage regulator for the 5V electronics.

For more information about the complete GripRx system, including the overall system architecture, team design decisions, and integration of the three subsystems, visit our official team project website.

**[View Team 103 – GripRx Project Website](https://egr304-2026-f-103.github.io/)**


### My Contribution

* My primary responsibility within Team 103 is the electrical design and development of the GripRx Motor Board.

* My responsibilities include:

- Developing the Motor Board block diagram and identifying electrical connections.
- Comparing and selecting the major electrical components.
- Designing the Motor Board schematic and PCB using KiCad.
- Integrating the PIC18F57Q43 microcontroller with the H-bridge motor driver.
- Implementing motor speed and direction control using PWM and digital signals.
- Connecting the home and end limit switches.
- Establishing communication with the Force Board through UART.
- Evaluating electrical protection and power requirements.
- Supporting subsystem integration and testing.

The Motor Board receives commands and safety information from the Force Board and uses them to control the resistance-adjustment mechanism.

The following sections document the electrical design and development of my subsystem.

To review the details listed of the material used to construct the subsection, you can review it in the ["BOM"](https://embedded-systems-design.github.io/EGR304DataSheetTemplate/03-BOM/BOM/) section of the datasheet.

To review the Motor Board design and its electrical connections, see the ["Block Diagram"](01-Block-Diagram/Block-Diagram.md) section of this datasheet.

## Component Selection

The major components for the GripRx Motor Board were evaluated based on electrical specifications, cost, performance, and compatibility.

The planned components include:

| Component | Selected Part |
|---|---|
| Microcontroller | Microchip PIC18F57Q43 Curiosity Nano |
| Motor Driver | Texas Instruments DRV8871DDAR |
| DC Gear Motor | DFRobot FIT0492-A |
| Voltage Regulator | STMicroelectronics L7805ABV-DG |
| Limit Switches | Omron D2F-01L |
| Power Supply | 9V, 3A DC wall adapter BestCH |
[View Component Selection](02-Component-Selection/Component-Selection.md)

## Power Budget

The GripRx Motor Board is designed to operate from a 9V DC,
3A power supply provided by the professor.

The power supply has a maximum rated output capacity of 27W.
The L7805ABV-DG voltage regulator is intended to provide
a regulated 5V supply for the control electronics.

The detailed power budget will be completed after the
electrical requirements of the individual components
have been evaluated.

[View Power Budget](05-Power-Budget/Power-Budget.md)
