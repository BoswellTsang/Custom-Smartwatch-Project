# Custom Smartwatch — Electronics and PCB Development

**Status:** In progress (November 2026) · **Project:** Independent hardware design  
**Focus:** KiCad · low-power electronics · BLE/RF · power management · sensors · mixed-signal layout

> Designing a custom smartwatch at the integrated-circuit and PCB level. The intended platform combines a Nordic nRF54L15 MCU, 250 mAh LiPo battery, charger/fuel gauge, 3.0 V and 1.8 V power rails, graphical display, IMU, ambient light sensor and a separate optical heart-rate PCB.

<!-- Add an image of the real schematic or PCB here once available. -->

## Project status

This is **not a completed smartwatch**. Major components have been selected, custom schematic symbols and supporting circuits are in development, and the separate heart-rate AFE board has reached preliminary fine-pitch routing. Fabrication, firmware bring-up and measured performance are still future work.

| Subsystem | Selected hardware / design |
| --- | --- |
| Microcontroller | Nordic nRF54L15, QFN48, Bluetooth Low Energy |
| Battery | MIKROE-4471 / MLP502030, protected 250 mAh, 3.7 V LiPo |
| Charger | TI BQ25185DLHR with power-path management |
| Main regulator | TI TPS63900DSKR buck-boost; target 3.0 V |
| Secondary regulator | TI TPS7A2018PDBVR LDO; target 1.8 V |
| Fuel gauge | MAX17048G+T10 |
| Battery temperature monitor | 10 kΩ NTC |
| IMU | Bosch BMI270, 3-axis accelerometer + gyroscope |
| Ambient light | TI OPT3004, I²C |
| RF antenna | Johanson 2450AT18A0100001E, 2.45 GHz chip antenna |
| Display | RONBO RB0128Y2447A-GF70; FPC interface being checked |
| Optical sensing | MAX86141ENP+T AFE on a separate proposed PCB |
| Board plan | Main smartwatch board + optical sensor daughterboard |

## Functional architecture (prototype)

<img width="671" height="663" alt="image" src="https://github.com/user-attachments/assets/5808e488-54ee-486b-9b73-bff73f1690c1" />

## Work completed so far

### Power architecture and schematic
- Selected the BQ25185, TPS63900, TPS7A20, MAX17048 and protected LiPo battery.
- Defined target **3.0 V and 1.8 V** supplies and investigated shutdown/enable control.
- Researched **2.2 µH** buck-boost inductor, **10 µF** input and **22 µF** output capacitors and supporting resistor options from datasheets.
- Evaluated 0402/0603 passives, voltage ratings, tolerances and assembly feasibility.
- Created and verified custom KiCad symbols for several ICs and sensors.

### MCU, RF and digital peripherals
- Investigated nRF54L15 QFN48 pin mapping, GPIO, SPI/I²C and power requirements.
- Selected a 2.45 GHz chip antenna and drafted a matching network; RF layout and measurement remain future work.
- Investigated **BMI270** interface options (I²C, 3-/4-wire SPI) and **OPT3004** I²C pull-ups (10 kΩ versus 2.2 kΩ).
- Examined FPC connector selection, display supply pins and LED backlight components including a **10 µH** inductor and **1 µF** capacitors.

### Optical sensing PCB
- Selected a **MAX86141**, a 20-ball **0.4 mm-pitch** WLP optical AFE.
- Began routing its supply, ground and sensitive photodiode input nets.
- Investigated a **4-layer** layout, PD_GND shielding and fine-pitch signal escapes.
- Identified unresolved AFE interrupt routing and LED-supply compatibility.

## Roadmap

- [x] Establish preliminary system architecture and select major ICs
- [x] Start custom schematic symbols and power circuits
- [x] Investigate antenna network, display and sensor interfaces
- [x] Start optical AFE board routing
- [x] Finish schematic review, pin mapping and ERC
- [ ] Complete main PCB and optical AFE PCB layout / DRC
- [ ] Fabricate and assemble the first prototypes
- [ ] Bring up power, MCU, sensors, display and BLE
- [ ] Record active/sleep current and battery runtime
- [ ] Validate optical measurement and RF performance

## Engineering documentation

- [Architecture and power domains](docs/architecture.md)
- [Component selection and design decisions](docs/design-decisions.md)
- [Bring-up and validation plan](docs/testing.md)
- [Progress log](docs/progress-log.md)
- [Hardware source file guide](hardware/README.md)
- [Firmware development status](firmware/README.md)

Native KiCad, fabrication, firmware and actual project images will be added as they become available. No unmeasured performance is asserted.
