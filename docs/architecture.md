# System architecture and interfaces

## Proposed power tree
- **Battery:** 1S protected 3.7 V nominal / 250 mAh LiPo.
- **Charging and power path:** BQ25185.
- **Main system rail:** TPS63900 buck-boost, nominal target 3.0 V.
- **Secondary rail:** TPS7A2018 LDO, 1.8 V.
- **Battery telemetry:** MAX17048; 10 kΩ NTC temperature monitoring for charger.
- **Optical AFE:** MAX86141 on separate board; the LED-driver supply voltage must be reviewed independently of the 3.0 V rail.

## Digital links
- Nordic nRF54L15 MCU with BLE.
- BMI270 inertial sensor, SPI or I²C selection pending.
- OPT3004 ambient light sensor using I²C.
- Display linked through an FPC connector; finalized wiring pending.
- MAX86141 optical AFE, SPI communication to main MCU planned.
- Chip antenna and manufacturer-matched RF network at 2.45 GHz.

## Board separation
One main PCB for MCU, RF, charge/power, sensors and display connector. A separate optical sensor board is planned for the MAX86141 and optical emitters/detectors.

This is a conceptual representation, not a validated schematic or production design.
