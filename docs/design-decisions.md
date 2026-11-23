# Component selection and design decisions

| Design area | Decision / research | Status |
| --- | --- | --- |
| MCU | nRF54L15 QFN48 selected for low-power BLE | Selected |
| Battery | MIKROE-4471, 3.7 V / 250 mAh protected LiPo | Selected |
| Charger | BQ25185DLHR with power-path management | Selected |
| DC-DC | TPS63900DSKR buck-boost targeting 3.0 V; 2.2 µH, 10 µF input, 22 µF output discussed | Schematic design |
| LDO | TPS7A2018PDBVR for 1.8 V | Schematic design |
| Fuel gauge | MAX17048G+T10 | Symbol and circuitry development |
| Temperature | NTCLE413E2103F106A, 10 kΩ NTC | Selected |
| RF | Johanson 2450AT18A0100001E antenna with preliminary matching network | Not RF-tested |
| IMU | BMI270; SPI vs I²C bus selection reviewed | Pending bus finalization |
| Ambient light | OPT3004; 10 kΩ vs 2.2 kΩ I²C pull-ups researched | Pending bus timing validation |
| Display | RONBO round display; 24-pin 0.5 mm FPC requirement considered | Mating connector not verified |
| Backlight | Investigated 10 µH inductor and 1 µF capacitors | Schematic design |
| Optical AFE | MAX86141ENP+T on separate board | Partial fine-pitch routing |

## Key hardware challenges

### Multiple power domains
The 3.0 V and 1.8 V supply targets are not automatically suitable for every peripheral. Each IC's operating voltage and peak current requirements must be checked. In particular, the optical AFE LED power input has a higher minimum than 3.0 V.

### Antenna matching and clearance
The 2.45 GHz ceramic antenna requires a correctly placed matching network and suitable ground/clearance layout; selecting nominal values is not a substitute for RF verification.

### Optical sensing analog layout
The MAX86141's 0.4 mm WLP pitch and sensitive photodiode nets constrain trace routing, via placement and the layer stackup. Investigated PD_GND shields, short photodiode traces, and separation from switching power circuits.

### FPC connector compatibility
Pin count and pitch are insufficient to guarantee mechanical compatibility. Final display mating part and pad orientation require verification.
