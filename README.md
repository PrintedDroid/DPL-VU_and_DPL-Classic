# DPL Classic & DPL-VU

**Firmware and user manuals for the Printed-Droid DPL Classic and DPL-VU boards.**
Body lights for R-series Astromech droids (R2-D2 & co.)

---

## What's in this repository

| File | Description |
|------|-------------|
| `DPL Firmware_Nano-v1.1.hex` | Current firmware for **both** DPL Classic and DPL-VU |
| `DPL_Manual_EN.pdf` | Full user manual (English) |
| `DPL_Handbuch_DE.pdf` | Full user manual (German) |

## Quick start

1. Download `DPL Firmware_Nano-v1.1.hex`
2. Connect your DPL board to your PC via USB
3. Flash the firmware using **XLoader** (Windows) — see Section 4 in the manual
   - Device: **Nano (ATmega328)**
   - Baud rate: **115200** (or **57600** for older Nanos)
4. Bridge the `Left Door` and `Right Door` headers (or attach door switches) — otherwise DPL and CBI stay dark
5. Open a serial terminal at **115200 baud**, line ending **CR**
6. Send `/DP/BR/12` → DPL lights up

For all commands, animations, hardware connections and troubleshooting, see the manual PDF.

## Boards covered

| Board | VU LEDs on board | External VU possible |
|-------|:----------------:|:--------------------:|
| **DPL Classic** | no | yes (separate VU Extension at pin D3) |
| **DPL-VU** | yes (28 WS2812B) | — |

Both boards run the **same firmware**.

## Acknowledgements

The firmware is based on the excellent **AstroCAN BodyLights** codebase by **RealNobser** from the R2 Builders community. Huge thanks to RealNobser for the great work that makes these boards possible.

## Support

- Product pages: https://www.printed-droid.com
- Facebook group: https://www.facebook.com/groups/printeddroid/
- Issues with the documentation: open an issue in this repository

## License

- **Firmware:** based on AstroCAN BodyLights by RealNobser — all rights with the original author
- **Manuals:** © Printed-Droid — all rights reserved. No commercial reuse, duplication or modification without explicit consent.
