## Overview

This Bill of Materials (BOM) documents the electronic components selected for the GripRx Motor Board, developed as part of Team 103 in EGR 304 Embedded Systems Design.

The Motor Board uses a PIC18F57Q43 Curiosity Nano microcontroller, a DRV8871 motor driver, and an L7805 voltage regulator to control a DC gear motor. The design includes limit switches, power filtering capacitors, connectors, status LEDs, and test points.

Components are sourced from DigiKey, Newark, existing inventory, and class-provided materials.

## Bill of Materials

The following table identifies the components used in the Motor Board design, including their reference designators, quantities, manufacturer part numbers, and suppliers. N/A suppliers mean the components can be found in class.

| Component | Reference | Qty | Manufacturer Part Number | Supplier | Supplier Part Number |
|:---|:---|---:|:---|:---|:---|
| PIC18F57Q43 Curiosity Nano | U1 | 1 | DM164150 | Already Owned | N/A |
| 5V Voltage Regulator | U2 | 1 | L7805ABV-DG | Newark | 51AC9206 |
| Motor Driver | U3 | 1 | DRV8871DDAR | DigiKey | 296-43024-1-ND |
| DC Gear Motor | J4 | 1 | FIT0492-A | Newark | 33AK3163 |
| 150uF Capacitor | C1 | 1 | EEUFR1E151B | Newark | 62W8036 |
| 0.33uF Capacitor | C2 | 1 | MPMLR50V334KX7RTB5 | Newark | 68AH8543 |
| 0.1uF Capacitors | C3, C5, C6, C9-C12 | 7 | MPMLR50V104KX7RTB2-5 | Newark | 68AH8539 |
| 10uF Capacitor | C4 | 1 | MCGPR25V106M5X11 | Newark | 38K4677 |
| 47uF Capacitor | C7 | 1 | ECA1EHG470 | Newark | 17T5002 |
| 100uF Capacitor | C8 | 1 | EEUFR1E101 | Newark | 58T1749 |
| Schottky Diode | D1 | 1 | 1N5822 | Newark | 33AK8198 |
| Green LED | D2 | 1 | Class Provided | Class | N/A |
| Red LED | D3 | 1 | Class Provided | Class | N/A |
| 1k Ohm Resistors | R1, R3, R8 | 3 | CFR-25JR-52-1K | Class | N/A |
| 10k Ohm Resistors | R2, R5-R7 | 4 | MFR-25FBF52-10K | Class | N/A |
| 64.9k Ohm Resistor | R4 | 1 | MFR-25FBF52-64K9 | DigiKey | 64.9KXBK-ND |
| Limit Switches | SW1, SW2 | 2 | D2F-01L | Newark | 36K7261 |
| Debug Push Button | SW3 | 1 | B3F-1000 | Newark | 36K7138 |
| DC Power Jack | J1 | 1 | PJ-102AH | Newark | 59AM2884 |
| 8-Pin Header | J2 | 1 | 5-102618-2 | Class | N/A |
| 10-Pin GPIO Header | J3 | 1 | MTLW-110-06-T-S-060 | Newark | 40AC2655 |
| 2-Pin Jumper Headers | JP1-JP3 | 3 | M20-9990246 | DigiKey | 952-2262-ND |
| JP1/JP2 Jumper Caps | JP1, JP2 | 2 | M7583-05 | DigiKey | 952-2882-ND |
| JP3 Motor Power Jumper Cap | JP3 | 1 | QPC02SXGN-RC | DigiKey | S9337-ND |
| PCB Test Points | TP1-TP9 | 9 | 5000 | Newark | 07J9695 |

## Component Purchasing

Components requiring purchase are ordered through DigiKey and Newark using the EGR 304 purchase request forms.

Class-provided and already-owned components are included in the BOM for completeness but are excluded from purchase requests.

## Datasheets

Manufacturer datasheets for the selected components are provided in the project repository.
