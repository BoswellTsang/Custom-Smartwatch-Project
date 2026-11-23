# Hardware bring-up and test plan

**No fabricated or measured smartwatch results are currently documented.** These are future steps, not completed tests.

| Stage | Proposed validation |
| --- | --- |
| Pre-power | Inspect assembly, continuity, orientation, shorts and schematic/PCB revisions |
| Charger | Verify charging input, battery path and NTC temperature response |
| Regulators | Measure 3.0 V and 1.8 V startup, ripple and load transient response |
| MCU | Verify boot, debugging and clocks |
| Sensors | Verify I²C/SPI transactions and expected device identities |
| Display | Verify control interface, display output and backlight current |
| RF | Validate BLE link and antenna performance; consider RF matching measurements |
| Optical AFE | Verify safe LED supply, SPI, photodiode signals and measurement behavior |
| Power | Measure sleep/active current and estimate/validate battery life |

For each test, record instrument, operating conditions, expected/actual values, revision and outcome.
