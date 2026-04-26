# DPL Classic & DPL-VU — Data Port Logics für Astromech-Droiden

**Printed-Droid Body-Lights-Platinen für R-Series Droiden (R2-D2 & Co.)**
Firmware DPL Firmware_Nano-v1.1 · Hardware-Plattform Arduino Nano (ATmega328) · Doku 2.0.0 · Stand 2026-04-26

---

## Danksagung

Die DPL-Firmware basiert auf der hervorragenden **AstroCAN BodyLights**-Codebasis von **RealNobser** aus der R2-Builders-Community. Ein großes Dankeschön an RealNobser für die Bereitstellung dieses leistungsstarken Codes — ohne sein Engagement wären die DPL Classic und DPL-VU Platinen so nicht möglich gewesen.

---

## Was diese Doku abdeckt

Diese Dokumentation richtet sich an User der Printed-Droid-Platinen **DPL Classic** und **DPL-VU**.
Beide Platinen laufen mit der **gleichen Firmware** (`DPL Firmware_Nano-v1.1`). Der Unterschied liegt nur in der Bestückung:

| Platine | Microcontroller | VU-LEDs auf Platine | Sound-reaktive Anzeige | Externe VU möglich |
|---------|----------------|:--------------------:|:----------------------:|:------------------:|
| **DPL Classic** | Arduino Nano on-board | nein (nicht bestückt) | nein (Default) | ja, separat erhältlich, an Pin D3 anlöten |
| **DPL-VU** | Arduino Nano on-board | ja (28 WS2812B in 2× 14er-Reihen) | nein (siehe Hinweis im Handbuch) | — |

Beide Platinen treiben:
- **DPL** (Data Port Lights) — direkt auf der Platine
- **CBI Plus** oder **D-CBI** (Charge Bay Indicator, separat erhältlich) — auf der Charge-Bay-Tür
- **LDPL** (Large DataPanel Logics, separat erhältlich)
- **UAL** (Utility Arm Lights, separat erhältlich)
- **Voltage Monitor** mit 4 Schwellwerten (rot/gelb/grün/laden) — Anzeige über CBI

---

## Schnelleinstieg

1. **Platine an 5V anschließen** (USB-Kabel vom PC reicht aus — auch mit beiden CBI-Varianten gleichzeitig)
2. **USB-Kabel an den on-board Arduino Nano stecken**
3. **Firmware flashen** mit XLoader (Anleitung im Handbuch, Abschnitt "Firmware flashen")
4. **Serielles Terminal öffnen** mit 115200 Baud, Zeilenende **CR** (nicht LF!)
5. **Befehl absenden:** `/DP/BR/12` → DPL-Helligkeit auf 12

Befehle, Animationen, Hardware-Anschlüsse, Pin-Belegung und Troubleshooting sind im Handbuch ausführlich beschrieben.

---

## Befehlsformat (Kurzfassung)

```
/MODUL/PARAMETER/WERT[/WERT2/WERT3...]
```

**Module (Tokens):** `DP` `CB` `DC` `LD` `UA` `VU` · plus DPL-Sub-Bereiche `TB` `BL` `BG` `RL` `WL`
**Parameter:** `BR` (Helligkeit) · `AN` (Animation) · `AS` (Animation-Speed ms) · `CO` (RGB-Farbe) · `VM` (Voltage Monitor an/aus) · `VL` (Voltage-Schwellen) · `RR` (Spannungsteiler-Widerstände)
**System-Befehle:** `/RESTART` (Soft-Reboot) · `/FACTORY` (EEPROM-Defaults wiederherstellen)

```
/DP/BR/15                       DPL Helligkeit 15 (Skala 0-15)
/LD/BR/100                      LDPL Helligkeit 100 (Skala 0-255)
/LD/CO/255/0/0                  LDPL Grundfarbe Rot
/CB/AN/3                        CBI Heart-Animation
/DC/AN/6                        D-CBI Rainbow
/DP/VL/11.5/12.0/12.5/13.0      Voltage-Schwellen rot/gelb/grün/laden
```

---

## Variant-Auswahl-Hilfe

**DPL Classic kaufen wenn:**
- Standard-Funktion ohne VU-Anzeige reicht
- VU-Effekte sind nicht gewünscht oder werden später optional nachgerüstet

**DPL-VU kaufen wenn:**
- Eine 28-LED VU-Anzeige im Data-Port von Anfang an gewünscht ist
- Aufmerksamkeitsstarke Effekte (BPM-Sync, Juggle, VU-Meter) erwünscht sind

**DPL Classic + externe VU-Platine** (nachträglich an D3 anlötbar): wenn man die VU später ergänzen möchte. Externe VU-Platine ist separat bei Printed-Droid erhältlich.

---

## Hardware-Quellen

- **Printed-Droid DPL Classic:** https://www.printed-droid.com/kb/dpl-classic-data-port-logics/
- **Printed-Droid DPL-VU:** https://www.printed-droid.com/kb/data-port-logics-vu-dpl-vu/
- **Original-Code (RealNobser):** AstroCAN BodyLights

---

## Support & Hilfe

- **Shop / Produktseiten:** https://www.printed-droid.com
- **Community / Facebook-Gruppe:** https://www.facebook.com/groups/printeddroid/
- **GitHub-Repo:** https://github.com/PrintedDroid/DPL-VU_and_DPL-Classic

---

## Lizenz & Credits

- **Firmware:** DPL Firmware_Nano-v1.1 (basiert auf **AstroCAN BodyLights** von **RealNobser**, R2-Builders-Community) — die Original-Codebasis enthält keine eigene Lizenz-Datei; alle Rechte beim Original-Autor RealNobser
- **Platinen-Design:** Printed-Droid (https://www.printed-droid.com)
- **Diese Doku:** © Printed-Droid — **alle Rechte vorbehalten**. Keine Genehmigung zur kommerziellen Weiterverwendung, Vervielfältigung oder Bearbeitung ohne ausdrückliche Zustimmung.
