# DPL Classic & DPL-VU — Data Port Logics for Astromech droids

**Printed-Droid Body-Lights boards for R-series droids (R2-D2 & co.)**
Firmware DPL Firmware_Nano-v1.1 · Platform Arduino Nano (ATmega328) · Doc 2.0.0 · 2026-04-26

---

## Acknowledgements

The DPL firmware is based on the excellent **AstroCAN BodyLights** codebase by **RealNobser** from the R2 Builders community. A huge thanks to RealNobser for providing this powerful code — without his work the DPL Classic and DPL-VU boards would not be possible in their current form.

---

## What this documentation covers

This documentation is for users of the Printed-Droid **DPL Classic** and **DPL-VU** boards.
Both boards run the **same firmware** (`DPL Firmware_Nano-v1.1`). The only difference is the assembly:

| Board | Microcontroller | VU LEDs on board | Sound-reactive display | External VU possible |
|-------|----------------|:----------------:|:----------------------:|:--------------------:|
| **DPL Classic** | Arduino Nano on board | no (not populated) | no (default) | yes, available separately, soldered to D3 |
| **DPL-VU** | Arduino Nano on board | yes (28 WS2812B in 2× 14-row layout) | no (see note in the manual) | — |

Both boards drive:
- **DPL** (Data Port Lights) — directly on the board
- **CBI Plus** or **D-CBI** (Charge Bay Indicator, available separately) — on the charge-bay door
- **LDPL** (Large DataPanel Logics, available separately)
- **UAL** (Utility Arm Lights, available separately)
- **Voltage Monitor** with 4 thresholds (red/yellow/green/charge) — display via CBI

---

## Quick start

1. **Connect the board to 5V** (a USB cable from your PC is enough — even with both CBI variants connected at the same time)
2. **Plug the USB cable into the on-board Arduino Nano**
3. **Flash the firmware** with XLoader (instructions in the manual, section "Flashing the firmware")
4. **Open a serial terminal** at 115200 baud, line ending **CR** (not LF!)
5. **Send a command:** `/DP/BR/12` → DPL brightness 12

Commands, animations, hardware connections, pin map and troubleshooting are covered in detail in the manual.

---

## Command format (short version)

```
/MODULE/PARAMETER/VALUE[/VALUE2/VALUE3...]
```

**Modules (tokens):** `DP` `CB` `DC` `LD` `UA` `VU` · plus DPL sub-areas `TB` `BL` `BG` `RL` `WL`
**Parameters:** `BR` (brightness) · `AN` (animation) · `AS` (animation speed ms) · `CO` (RGB color) · `VM` (voltage monitor on/off) · `VL` (voltage thresholds) · `RR` (voltage divider resistors)
**System commands:** `/RESTART` (soft reboot) · `/FACTORY` (restore EEPROM defaults)

```
/DP/BR/15                       DPL brightness 15 (scale 0-15)
/LD/BR/100                      LDPL brightness 100 (scale 0-255)
/LD/CO/255/0/0                  LDPL base color red
/CB/AN/3                        CBI heart animation
/DC/AN/6                        D-CBI rainbow
/DP/VL/11.5/12.0/12.5/13.0      Voltage thresholds red/yellow/green/charge
```

---

## Variant decision guide

**Choose DPL Classic if:**
- Standard function without VU display is enough
- VU effects are not desired or will optionally be retrofitted later

**Choose DPL-VU if:**
- A 28-LED VU display in the data port is desired from the start
- Eye-catching effects (BPM sync, juggle, VU meter) are wanted

**DPL Classic + external VU board** (can be soldered to D3 later): if you want to add VU later. The external VU board is sold separately by Printed-Droid.

---

## Hardware sources

- **Printed-Droid DPL Classic:** https://www.printed-droid.com/kb/dpl-classic-data-port-logics/
- **Printed-Droid DPL-VU:** https://www.printed-droid.com/kb/data-port-logics-vu-dpl-vu/
- **Original code (RealNobser):** AstroCAN BodyLights

---

## Support & help

- **Shop / product pages:** https://www.printed-droid.com
- **Community / Facebook group:** https://www.facebook.com/groups/printeddroid/
- **GitHub repo:** https://github.com/PrintedDroid/DPL-VU_and_DPL-Classic

---

## License & credits

- **Firmware:** DPL Firmware_Nano-v1.1 (based on **AstroCAN BodyLights** by **RealNobser**, R2 Builders community) — the original codebase does not include a license file; all rights with the original author RealNobser
- **Board design:** Printed-Droid (https://www.printed-droid.com)
- **This documentation:** © Printed-Droid — **all rights reserved**. No permission granted for commercial reuse, duplication or modification without explicit consent.
