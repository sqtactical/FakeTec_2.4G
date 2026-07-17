# fakeTec_pcb - 2.4GHz Edition

A low-cost, high-power 2.4GHz nRF52 device with the form-factor of the Heltec v2 & v3 devices, compatible with [Meshtastic](https://meshtastic.org/)®. 

This repository is a hardware fork derived from **[lupusworax's variant](https://github.com/gargomoma/fakeTec_pcb/issues/16)**, which was originally based on the excellent base design by **[gargomoma](https://github.com/gargomoma/fakeTec_pcb)**.

## 🚀 What's Different?
While the original versions focus on sub-GHz LoRa modules (like the HT-RA62 or RA-01SH), this version swaps the RF section out for an **Ebyte E28-2G4M27S/ SX** module. This brings **2.4GHz LoRa capabilities** and a powerful +27dBm power output to the compact Heltec footprint. However, the E28 overhangs outside a bit, so your current faketec cases may need redesigning

# Pictures


<details><summary>Click to open</summary>

| Front | Back |
| :------------ | :---------------------------- |
| <img width="300" height="600" alt="image" src="https://github.com/user-attachments/assets/8d96614d-f144-4313-88c5-60e54c289da3" />
 | <img width="300" height="600" alt="image" src="https://github.com/user-attachments/assets/44d46e6d-5e4b-4656-8b00-460d66f5e28d" />
 |

</details>

## Features
- **2.4GHz LoRa Mesh:** Built around the powerful SX1280-based Ebyte E28-2G4M27SX module.
- **Heltec v3 Form Factor:** Fits seamlessly into existing community 3D-printed cases meant for the original FakeTec or Heltec v3.
- **nRF52840 MCU:** Powered by the affordable ProMicro / SuperMini nRF52840 board.
- **I2C Expansion:** Dedicated side ports ready to accept a standard SSD1306 OLED screen.
- **Battery Monitoring:** Integrated battery voltage sensing (supports both SMD and through-hole resistors).
- **Mounting:** Standard 2mm mounting holes.

## Bill of Materials (BOM)

| Part | Source / Example | Approx. Cost | Note |
| :--- | :--- | :--- | :--- |
| **ProMicro nRF52840** (SuperMini) | [AliExpress]([https://www.aliexpress.com/](https://es.aliexpress.com/item/1005009116054547.html)) | ~5€ | Double-check bootloader compatibility before soldering. |
| **Ebyte E28-2G4M27S/SX** | [AliExpress]([https://www.aliexpress.com/](https://es.aliexpress.com/item/1005010288386483.html)) | ~7-9€ | 2.4GHz LoRa module (+27dBm high power). |
| **2x 1M Ohm Resistors** | [AliExpress]([https://www.aliexpress.com/](https://es.aliexpress.com/item/1005002991902748.html)) | <0.50€ | Used for the battery voltage divider. SMD 1206 size. |
| **OLED SSD1306 I2C** (Optional) | [AliExpress]([https://www.aliexpress.com/](https://es.aliexpress.com/item/1005005970901119.html)) | ~1.50€ | Add insulating tape beneath to prevent shorts against the MCU. |
| **2x Push Buttons** | [AliExpress]([https://www.aliexpress.com/](https://es.aliexpress.com/item/4001125532910.html)) | <0.50€ | Search for "3\*4\*2.0 2 Pin Buttons". |
| **2.4GHz Antenna & Pigtail (SX only)** | [AliExpress]([https://www.aliexpress.com/](https://es.aliexpress.com/item/1005004598468979.html)) | ~9€ | Ensure you use a dedicated **2.4GHz** antenna, not a sub-GHz one! |
| **Custom PCB** | Custom Gerber | Variable | Order via your favorite fabrication house (JLCPCB, PCBWay, etc.). |

(Links are non affiliated and only serve as an example)

## Firmware & Flashing

Because this board uses a 2.4GHz SX1280 radio instead of the traditional sub-GHz SX1262, you will need to compile or flash a Meshtastic firmware variant matching the pinout. This repository already includes a variant for it.

> ⚠️ **Reminder:** Make sure your `variant.h` configuration maps the SPI busy/dio/reset and TX EN pins accurately to how the Ebyte E28 module is wired to your ProMicro layout!

## Credits & Thanks
- **[gargomoma](https://github.com/gargomoma)** for creating the original open-source `fakeTec_pcb` layout and concept.
- **[lupusworax](https://github.com/gargomoma/fakeTec_pcb/issues/16)** for the intermediate design improvements that this branch directly builds upon.
- Designed and modified for 2.4GHz by [EmilioAl](https://github.com/EmilioAL-Git) & yours truly.


### Disclaimer
No warranty is provided. You build and operate this hardware at your own risk. Always ensure compliance with local radio frequency regulations regarding 2.4GHz transmission power limits.
