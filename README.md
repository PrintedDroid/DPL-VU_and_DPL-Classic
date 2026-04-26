# DPL Classic & DPL-VU

**Firmware and user manuals for the Printed-Droid DPL Classic and DPL-VU boards.**
Body lights for R-series Astromech droids (R2-D2 & co.)

---

## Quick start

1. Download `DPL Firmware_Nano-v1.1.hex`
2. Connect your DPL board to your PC via USB
3. Flash the firmware using **XLoader** (Windows) — see Section 4 in the manual
   - Device: **Nano (ATmega328)**
   - Baud rate: **115200** (or **57600** for older Nanos)
4. Bridge the `Left Door` and `Right Door` headers (or attach door switches) — otherwise DPL and CBI stay dark
5. Open a serial terminal at **115200 baud**, line ending **CR**
6. Send `/DP/BR/12` → DPL lights up

For full setup, hardware wiring, all commands, animations and troubleshooting, see the user manual:

| Manual | Language |
|--------|----------|
| `DPL_Manual_EN.pdf` | English |
| `DPL_Handbuch_DE.pdf` | German |

---

## Boards covered

| Board | VU LEDs on board | External VU possible |
|-------|:----------------:|:--------------------:|
| **DPL Classic** | no | yes (separate VU Extension at pin D3) |
| **DPL-VU** | yes (28 WS2812B) | — |

Both boards run the **same firmware** (`DPL Firmware_Nano-v1.1.hex`).

## Looking for full RGB?

Printed-Droid also offers the **RGB-DPL** — a fully WS2811/WS2812-based variant with full RGB color depth on every panel (DPL / CBI / LDPL / CSL). Different controller (Pro Mini or ESP32-S3), different firmware with profile system, color schemes and personality modes.

Repository: https://github.com/PrintedDroid/RGB-DPL-Firmware

---

## Hardware

The DPL board is the **central control unit**. The on-board MAX7219 drives the DPL's own front-side LEDs; external modules connect to the breakouts:

| External module | Connector | Command token |
|-----------------|-----------|:-------------:|
| **CBI Plus** (analog Charge Bay Indicator, MAX7219) | 5-pin header `−/+/L/C/D` | `/CB/...` |
| **D-CBI** (digital Charge Bay Indicator, WS2812B) | 3-pin header `D6 D-CBI` | `/DC/...` |
| **LDPL** (Large DataPanel Logics, WS2812B) | 3-pin header `D7 LDPL` | `/LD/...` |
| **UAL** (Utility Arm Lights, WS2812B) | signal-only pin `D8` | `/UA/...` |
| **VU Extension** (DPL Classic only) | 3-pin header `D3 VU` | `/VU/...` |

### Inputs

| Function | Pin |
|----------|-----|
| Left Door switch | D2 |
| Right Door switch | D4 |
| Voltage monitor (ADC) | A0 |

### Voltage monitor

Default voltage divider (factory-populated as SMD): **R1 = 100 kΩ**, R2 = 10 kΩ. THT pads next to the SMDs allow swapping in custom values for higher voltage ranges.

Default thresholds: red `11.5 V`, yellow `12.0 V`, green `12.5 V`, charge `13.0 V`.

Configurable at runtime:
- `/CB/VM/<0|1>` — enable/disable monitor
- `/DP/VL/<RED YELLOW GREEN CHARGE>` — set thresholds in volts
- `/DP/RR/<R1 R2>` — match software scaling to swapped resistors

---

## Serial commands (overview)

The full list and per-command details are in the manual. Format: `/<MODULE>/<PARAM>/<VALUE>[/...]` at **115200 baud**, line ending **CR**.

```text
Modules:    DP (DPL)   CB (CBI Plus)   DC (D-CBI)   LD (LDPL)   UA (UAL)   VU (VU)
            TB BL BG RL WL  (DPL sub-areas)

Parameters: BR  brightness  (0-15 for MAX7219, 0-255 for WS2812B)
            AN  animation number
            AS  animation speed (ms)
            CO  base color  (R G B, 0-255 each)
            VM  voltage monitor on/off
            VL  voltage thresholds (R Y G C in V)
            RR  voltage divider resistors (R1 R2 in ohms)

System:     /RESTART     soft reboot
            /FACTORY     reset EEPROM to defaults

Examples:   /DP/BR/15                       DPL brightness 15
            /LD/CO/0/0/255                  LDPL base color blue
            /DC/AN/6                        D-CBI rainbow
            /DP/VL/11.5/12.0/12.5/13.0      voltage thresholds
```

---

## Project structure

```text
DPL-VU_and_DPL-Classic/
  README.md                   (this file)
  DPL Firmware_Nano-v1.1.hex  current firmware (both boards)
  DPL_Manual_EN.pdf           full user manual (English)
  DPL_Handbuch_DE.pdf         full user manual (German)
```

---

## Acknowledgements

The firmware is based on the excellent **AstroCAN BodyLights** codebase by **RealNobser** from the R2 Builders community. Huge thanks to RealNobser for the great work that makes these boards possible.

---

## Support

- **Product pages:** https://www.printed-droid.com
- **Facebook group:** https://www.facebook.com/groups/printeddroid/
- **Issues / documentation feedback:** open an issue in this repository

---

## License

- **Firmware:** based on AstroCAN BodyLights by RealNobser — all rights with the original author
- **Manuals & this documentation:** © Printed-Droid — all rights reserved. No commercial reuse, duplication or modification without explicit consent.
