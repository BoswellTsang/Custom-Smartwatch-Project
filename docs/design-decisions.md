# Component selection and design decisions

| Design area | Decision / research | 
| --- | --- | 
| MCU | nRF54L15 QFN48 selected for low-power BLE |
| Battery | MIKROE-4471, 3.7 V / 250 mAh protected LiPo | 
| Charger | BQ25185DLHR with power-path management |
| DC-DC | TPS63900DSKR buck-boost targeting 3.0 V; 2.2 µH, 10 µF input, 22 µF output discussed |
| LDO | TPS7A2018PDBVR for 1.8 V |
| Fuel gauge | MAX17048G+T10 | 
| Temperature | NTCLE413E2103F106A, 10 kΩ NTC | 
| RF | Johanson 2450AT18A0100001E antenna with preliminary matching network |
| IMU | BMI270; SPI vs I²C bus selection reviewed | 
| Ambient light | OPT3004; 10 kΩ vs 2.2 kΩ I²C pull-ups researched |
| Display | RONBO round display; 24-pin 0.5 mm FPC requirement considered |
| Backlight | Investigated 10 µH inductor and 1 µF capacitors | 
| Optical AFE | MAX86141ENP+T on separate board | 

## Key hardware challenges

### Multiple power domains
The 3.0 V and 1.8 V supply targets are not automatically suitable for every peripheral. Each IC's operating voltage and peak current requirements must be checked. In particular, the optical AFE LED power input has a higher minimum than 3.0 V.

### Antenna matching and clearance
The 2.45 GHz ceramic antenna requires a correctly placed matching network and suitable ground/clearance layout; selecting nominal values is not a substitute for RF verification.

### Optical sensing analog layout
The MAX86141's 0.4 mm WLP pitch and sensitive photodiode nets constrain trace routing, via placement and the layer stackup. Investigated PD_GND shields, short photodiode traces, and separation from switching power circuits.

