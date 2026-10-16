
---
title: Component Selection
---

# Component Selection – GripRx Motor Board

**Course:** EGR 304 – Embedded Systems Design  
**Team:** 103 – GripRx  
**Project:** Motor Board

## Overview

The purpose of this assignment is to evaluate and compare major electronic components for the GripRx Motor Board. The board uses a PIC18F57Q43 microcontroller to control a DC gear motor through an H-bridge motor driver.

The selection process considers electrical compatibility, performance, cost, power requirements, and ease of integration.

The major components evaluated are:

1. DC Gear Motor
2. H-Bridge Motor Driver
3. 5V Voltage Regulator
4. 9V Power Supply

## 1. DC Gear Motor Selection

*Table 1: DC Gear Motor Comparison*

| Solution | Pros | Cons |
|---|---|---|
| ![DFRobot FIT0492-A](motor1.jpg)<br> **Option 1: DFRobot FIT0492-A** <br> **Price:** $11.90 each <br> **Voltage:** 12V <br> **Speed:** 50 RPM no-load <br> **Rated torque:** 9 kg-cm <br> **Rated current:** 0.68A <br> **Stall current:** 2.19A <br> [Product Link](https://www.dfrobot.com/product-1471.html) | - Lowest price among the compared motors <br> - High rated torque for a geared motor <br> - Low rotational speed suitable for controlled gripping <br> - Metal gearbox for mechanical durability | - Requires a 12V supply for rated performance <br> - Stall current exceeds the 1A current-limit target in the current block diagram <br> - Relatively heavy at 210g <br> - No integrated position encoder |
| ![Pololu 50:1 37D](motor2.jpg)<br> **Option 2: Pololu 50:1 37D** <br> **Price:** $38.95 each <br> **Voltage:** 12V <br> **Speed:** 200 RPM no-load <br> **Stall torque:** 21 kg-cm (extrapolated) <br> **Stall current:** 5.5A <br> [Product Link](https://www.pololu.com/product/4743) | - Durable metal gearbox <br> - Higher speed for faster movement <br> - Optional encoder-equipped version <br> - Detailed manufacturer specifications | - More expensive than Option 1 <br> - High stall current requires careful driver and power-supply selection <br> - Higher speed may require additional control for precise gripping <br> - Extrapolated stall torque is not a recommended continuous operating torque |
| ![Pololu 150:1 Micro](motor3.webp)<br> **Option 3: Pololu 150:1 Micro** <br> **Listed price:** $26.45 each <br> **Voltage:** 12V <br> **Speed:** 200 RPM no-load <br> **Stall torque:** approximately 2.9 kg-cm <br> **Stall current:** 0.8A <br> [Product Link](https://www.robotshop.com/products/12v-pololu-1501-micro-metal-gearmotor) | - Compact and lightweight design <br> - Lower stall current than the other two motors <br> - Metal gearbox <br> - Easier to accommodate in a small mechanism | - Much lower stall torque than the other options <br> - May not provide enough force for the gripping mechanism <br> - Higher no-load speed than Option 1 <br> - More expensive than Option 1 |

**Preliminary Choice:** Option 1 – DFRobot FIT0492-A Metal DC Gear Motor.

**Rationale:** The DFRobot FIT0492-A is the preferred preliminary choice because it provides a useful combination of low output speed, substantial rated torque, and low cost. Its rated torque of 9 kg-cm and rated current of 0.68A make it a promising candidate for the GripRx gripping mechanism. The 50 RPM no-load speed may also help provide controlled opening and closing movement. Compared with the Pololu alternatives, it offers an attractive balance between torque and cost.
However, the motor is rated for 12V, while the current block diagram specifies a 9V power supply. The power supply selection should therefore be reconsidered. Additionally, the motor has a stall current of 2.19A, which exceeds the currently proposed 1A motor-driver current limit. The team must evaluate the motor driver's current-limit setting and confirm that the motor can produce sufficient gripping force without overheating or stalling.
The final motor selection will be confirmed after the mechanical design is completed and the required gripping torque is calculated or measured.

**Sources:**
- [DFRobot FIT0492-A Manufacturer Specifications](https://www.dfrobot.com/product-1471.html)
- [Pololu 50:1 Metal Gearmotor Specifications](https://www.pololu.com/product/4743)
- [Pololu 150:1 Micro Metal Gearmotor Listing](https://www.robotshop.com/products/12v-pololu-1501-micro-metal-gearmotor)

## 2. H-Bridge Motor Driver Selection

*Table 2: H-Bridge Motor Driver Comparison*

The GripRx Motor Board requires an H-bridge driver to control the direction and speed of a brushed DC gear motor. The driver must support PWM control, operate with the motor supply voltage, and provide adequate current handling and protection against motor startup and stall conditions.

| Solution | Pros | Cons |
|---|---|---|
| <img src="driver1.jpeg" width="150"><br> **Option 1: Texas Instruments DRV8871DDAR** <br> **Approximate price:** $2.90 each <br> **Supply voltage:** 6.5–45V <br> **Peak output current:** 3.6A <br> **Package:** 8-pin HSOP <br> [Product Link](https://www.ti.com/product/DRV8871) | - Supports bidirectional brushed DC motor control <br> - Supports PWM speed control <br> - Adjustable current regulation using an external resistor <br> - Integrated overcurrent and thermal protection <br> - Relatively simple two-input interface | - Current limit must be configured correctly <br> - Thermal design limits continuous current <br> - Does not provide the same current feedback capabilities as Option 3 <br> - Current block diagram may need changes to the current-limit setting |
| <img src="driver2.jpeg" width="150"><br> **Option 2: Texas Instruments DRV8876PWPR** <br> **Approximate price:** $1.95 each <br> **Supply voltage:** 4.5–37V <br> **Peak output current:** 3.5A <br> **Package:** 16-pin HTSSOP <br> [Product Link](https://www.ti.com/product/DRV8876) | - Lowest estimated unit price <br> - Integrated current sensing and regulation <br> - Supports PWM motor control <br> - Compatible with 3.3V and 5V logic <br> - Integrated fault protection | - More pins and control configurations <br> - Requires careful PCB layout and thermal design <br> - Additional configuration may increase circuit complexity <br> - Not a direct pin-compatible replacement for the DRV8871 |
| <img src="driver3.jpeg" width="150"><br> **Option 3: Texas Instruments DRV8251ADDAR** <br> **Approximate price:** $2.40 each <br> **Minimum supply voltage:** 4.5V <br> **Absolute maximum supply voltage:** 50V <br> **Peak output current:** 4.1A <br> **Package:** 8-pin HSOP <br> [Product Link](https://www.ti.com/product/DRV8251A) | - Highest specified peak current among the options <br> - Integrated current sensing and regulation <br> - Current feedback may support stall detection <br> - Supports common microcontroller logic levels <br> - Integrated thermal and overcurrent protection <br> - Compact package | - Requires configuration of current regulation <br> - Thermal performance must be verified <br> - Motor current must remain within safe operating limits <br> - Requires verification of the control interface |

**Preliminary Choice:** Option 3 – Texas Instruments DRV8251ADDAR.

**Rationale:** The DRV8251A is the preferred preliminary motor driver because it provides integrated current sensing, adjustable current regulation, and a peak output current rating of 4.1A. Its operating voltage range accommodates the proposed motor supply.

Current regulation is particularly useful for the GripRx project because the motor may experience increased mechanical resistance while gripping an object. The integrated current sensing feature may also help detect motor loading or stall conditions.

The DRV8871 remains a viable alternative and is already included in the team's preliminary block diagram. However, the DRV8251A offers additional current feedback functionality that may be beneficial during development.

The final selection depends on the required gripping torque, expected motor current, thermal performance, and implementation of the motor control signals. The proposed 9V supply must also be reconsidered because the selected motor is rated for 12V. The block diagram and PCB design must be updated if the team changes from the DRV8871 to the DRV8251A.

**Sources:**
- [Texas Instruments DRV8871 Product Information](https://www.ti.com/product/DRV8871)
- [Texas Instruments DRV8876 Product Information](https://www.ti.com/product/DRV8876)
- [Texas Instruments DRV8251A Product Information](https://www.ti.com/product/DRV8251A)

## 3. Voltage Regulator Selection

*Table 3: Voltage Regulator Comparison*

| Solution | Pros | Cons |
|---|---|---|
| Option 1: To be researched | Pending | Pending |
| Option 2: To be researched | Pending | Pending |
| Option 3: To be researched | Pending | Pending |

**Choice:** Pending component comparison.

**Rationale:** To be completed.

## 4. Power Supply Selection

*Table 4: Power Supply Comparison*

| Solution | Pros | Cons |
|---|---|---|
| Option 1: To be researched | Pending | Pending |
| Option 2: To be researched | Pending | Pending |
| Option 3: To be researched | Pending | Pending |

**Choice:** Pending component comparison.

**Rationale:** To be completed.

## Final Component Selection Summary

This section will summarize the selected components after completing the comparisons.
