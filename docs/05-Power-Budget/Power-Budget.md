# Power Budget

## Overview

This power budget documents the electrical power requirements of the GripRx Motor Board, developed by Team 103 for EGR 304 – Embedded Systems Design at Arizona State University.

The Motor Board controls the resistance-adjustment mechanism using a PIC18F57Q43 Curiosity Nano microcontroller, a DRV8871 H-bridge motor driver, and a DFRobot FIT0492-A DC gear motor.

The design uses a nominal 9 V, 3 A DC power adapter. An L7805ABV-DG linear voltage regulator supplies 5 V to the microcontroller and control electronics.

The purpose of this power budget is to estimate the current consumption of the major components, evaluate the available power capacity, and identify electrical and thermal limitations.

## Power Supply Specifications

| Parameter | Value |
|---|---|
| Input Supply | 9 V DC |
| Maximum Supply Current | 3 A |
| Maximum Rated Input Power | 27 W |
| Logic Supply | 5 V DC |
| Voltage Regulator | L7805ABV-DG |
| Motor Driver | DRV8871DDAR |
| Motor | DFRobot FIT0492-A |
| Reverse-Polarity Protection | 1N5822 Schottky diode |

The maximum rated power of the adapter is calculated using:

**P = V × I**

P = 9 V × 3 A

**P = 27 W**

The 27 W value represents the maximum rated output capacity of the adapter, not the continuous power consumption of the Motor Board.

## Power Budget Table

The following table summarizes the known electrical requirements and the values that still require verification.

| Component | Supply Voltage | Current | Power / Notes |
|---|---|---|---|
| PIC18F57Q43 Curiosity Nano | 5 V | To be measured | Depends on operating mode and peripherals |
| DRV8871 Motor Driver | Nominal 9 V | Depends on operating state | Includes driver losses; motor current accounted for separately |
| DFRobot FIT0492-A Motor | Nominal 9 V | To be measured | Rated current is 0.68 A at 12 V |
| L7805ABV-DG Regulator | 9 V input / 5 V output | Depends on logic load | Dissipates excess voltage as heat |
| HOME Limit Switch Circuit | 5 V | Up to 0.5 mA through R5 | Up to 2.5 mW in pull-up resistor |
| END Limit Switch Circuit | 5 V | Up to 0.5 mA through R6 | Up to 2.5 mW in pull-up resistor |
| FORCE_OK Pull-Down (R2) | Signal dependent | Up to 0.5 mA | Up to 2.5 mW at 5 V |
| Debug Button Pull-Up (R7) | 5 V | Up to 0.5 mA | Up to 2.5 mW when pressed |
| Green Power LED (D2) | 5 V | Depends on LED forward voltage | Limited by 1 kΩ resistor |
| Red Debug LED (D3) | GPIO output | Depends on LED forward voltage | Limited by 1 kΩ resistor |

The resistor currents are calculated from the schematic values. Microcontroller and motor operating currents require measurement or additional device specifications.

Capacitors are not treated as continuous DC loads because their main purpose is filtering, decoupling, and temporary energy storage.

## Motor Power Calculation

The selected DFRobot FIT0492-A motor has the following published specifications at 12 V:

| Parameter | Value |
|---|---|
| Rated Voltage | 12 V |
| No-Load Current | 0.17 A |
| Rated Current | 0.68 A |
| Locked-Rotor Current | 2.19 A |
| Published Power Rating | 5 W |

Using the rated current and voltage:

P = V × I

P = 12 V × 0.68 A

**P = 8.16 W electrical input at the rated operating point**

The calculated electrical input at the published rated operating point is 8.16 W. The manufacturer's separate 5 W rating should not be interpreted as the electrical input calculated from the listed voltage and current without further clarification of the rating.

The GripRx Motor Board is designed to operate the motor from a nominal 9 V supply. Therefore, the published 12 V current values cannot be assumed to represent the actual current at 9 V.

The actual motor current will be measured during operation.

## Motor Driver Current Regulation

The DRV8871 motor driver uses an external resistor to configure its current regulation threshold.

The schematic includes:

**R4 = 64.9 kΩ**

According to the DRV8871 datasheet:

I_TRIP = 64 / R_ILIM(kΩ)

I_TRIP = 64 / 64.9

**I_TRIP ≈ 0.986 A**

Therefore, the nominal current regulation threshold is approximately 0.99 A.

This threshold helps control motor current during high-load conditions. Actual current regulation varies with device tolerances and operating conditions.

## 5 V Regulator Power Calculation

The L7805ABV-DG linear regulator converts the input supply to a regulated 5 V output.

The voltage difference is approximately:

ΔV = V_IN - V_OUT

Using the nominal 9 V supply before diode losses:

ΔV = 9 V - 5 V

**ΔV = 4 V**

The approximate power dissipated by the regulator due to its load current is:

P_DISS ≈ (V_IN - V_OUT) × I_LOAD

For an illustrative 100 mA logic load:

P_DISS ≈ 4 V × 0.100 A

**P_DISS ≈ 0.40 W**

This example excludes regulator ground current and the voltage drop across the reverse-polarity protection diode.

The actual regulator dissipation depends on the measured 5 V load current and the regulator input voltage.

Appropriate thermal management may be necessary.

## Limit Switch Power Calculation

The HOME and END limit switches use 10 kΩ pull-up resistors connected to the 5 V rail.

For each switch circuit when its contact connects the signal to ground:

I = V / R

I = 5 V / 10,000 Ω

**I = 0.0005 A = 0.5 mA**

The resistor power dissipation is:

P = V × I

P = 5 V × 0.0005 A

**P = 0.0025 W = 2.5 mW**

With both limit switches activated:

I_TOTAL = 0.5 mA + 0.5 mA

**I_TOTAL = 1.0 mA**

The total pull-up resistor dissipation is:

**P_TOTAL = 5 mW**

These currents occur when the corresponding switch contacts pull the signals LOW.

## Safety Margin

A 25% planning margin is considered when evaluating the total expected current consumption.

I_DESIGN = 1.25 × I_EXPECTED

The final expected current must include the motor driver supply current, motor operating demand, regulator input current, and other board loads.

The design should remain within the adapter's 3 A output rating during expected operating conditions.

A numerical total with the safety margin will be completed after the operating currents are verified.

## Conclusions

The GripRx Motor Board uses a nominal 9 V, 3 A supply with a maximum rated capacity of 27 W.

The 5 V logic rail is generated by the L7805ABV-DG regulator, while the DRV8871 H-bridge controls the DC gear motor.

The 64.9 kΩ current-limit resistor configures the DRV8871 for an approximately 0.99 A nominal current regulation threshold.

The limit switch pull-up circuits require relatively little current compared with the motor.

The motor is rated for 12 V operation, while the proposed system uses a 9 V supply. Motor performance and current consumption at 9 V must therefore be verified experimentally.

The final power budget will be confirmed by measuring the motor current, 5 V logic current, regulator temperature, and total adapter current during operation.

## Resources

- [GripRx Motor Board Schematic](../04-Schematic/schematic.md)
- [Texas Instruments DRV8871 Datasheet](https://www.ti.com/lit/ds/symlink/drv8871.pdf)
- [DFRobot FIT0492-A Motor Datasheet (PDF)](https://media.digikey.com/pdf/Data%20Sheets/DFRobot%20PDFs/FIT0492-A_Web.pdf)
- [Team 103 – GripRx Project](https://egr304-2026-f-103.github.io/)
