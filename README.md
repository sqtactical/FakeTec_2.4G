# fakeTec_pcb - 2.4GHz Edition

A low-cost, high-power 2.4GHz nRF52 device with the form-factor of the Heltec v2 & v3 devices, compatible with [Meshtastic](https://meshtastic.org/)®. 

This repository is a hardware fork derived from **[lupusworax's variant](https://github.com/gargomoma/fakeTec_pcb/issues/16)**, which was originally based on the excellent base design by **[gargomoma](https://github.com/gargomoma)**.

> ⚠️ **Legal Disclaimer:**  
> **🇬🇧:** It is the sole responsibility of the end user to ensure that the assembly, configuration, and operation of these PCBs comply with applicable local telecommunications laws and regulations.

## 🚀 What's Different?
While the original versions focus on sub-GHz LoRa modules (like the HT-RA62 or RA-01SH), this version swaps the RF section out for an **Ebyte E28-2G4M27S/ SX** module. This brings **2.4GHz LoRa capabilities** and a powerful +27dBm power output to the compact Heltec footprint. However, the E28 overhangs outside a bit, so your current faketec cases may need redesigning.

# Pictures

<details><summary>Click to open</summary>

<img width="545" height="708" alt="image" src="https://github.com/user-attachments/assets/c57fbee2-593e-4f86-9308-69756b5a0a54" />

</details>

## Features
- **2.4GHz LoRa Mesh:** Built around the powerful SX1280-based Ebyte E28-2G4M27SX module.
- **Heltec v3 Form Factor:** Fits seamlessly into existing community 3D-printed cases meant for the original FakeTec or Heltec v3 (with slight case modifications for the module overhang).
- **nRF52840 MCU:** Powered by the affordable ProMicro / SuperMini nRF52840 board.
- **I2C Expansion:** Dedicated side ports ready to accept a standard SSD1306 OLED screen.
- **Battery Monitoring:** Integrated battery voltage sensing (1206 SMD resistors).
- **Mounting:** Standard 2mm mounting holes.

## 📜 Changelog
### [v2.1] - Pending test
- **Improved the silkscreen:** Improved the silkscreen, to look more like the original faketec V4 (with all the pin markings), and also added in a small reminder to see which resistor value goes where. Improved the selector so you now know if you're feeding it with the ProMicro or the buck-boost
- **Increased trace thickness:** Increased the trace thickness from the selector to the input of the E28 (just in case).


### [v2] - Pending test
- **Added in Buck-Boost converter:** Added in a buck-boost converter to allow the E28 to operate at full power (the built in ProMicro 3.3V source onlly allows up to 24dBm).
- - **Added in Buck-Boost or Pro Micro selector:** Added in a selector so you can choose between running the E28 with the built in ProMicro regulator or an external buck-boost converter

### [v1] - Initial 2.4GHz Release
- **RF Module Migration:** Replaced sub-GHz LoRa module footprint with **Ebyte E28-2G4M27S / SX** (+27dBm 2.4GHz LoRa).
- **PCB Layout Updates:** Re-routed SPI/RF traces and pad layout to accommodate the E28 footprint and pinout.
- **Firmware Variant:** Included ready-to-use Meshtastic firmware variant tailored for this pin mapping.
- **Documentation & BOM:** Updated bill of materials, parts sources, and credits to reflect 2.4GHz requirements.

## Bill of Materials (BOM)

| Part | Source / Example | Approx. Cost | Note |
| :--- | :--- | :--- | :--- |
| **ProMicro nRF52840** (SuperMini) | [AliExpress](https://es.aliexpress.com/item/1005009116054547.html) | ~5€ | Double-check bootloader compatibility before soldering. |
| **Ebyte E28-2G4M27S/SX** | [AliExpress](https://es.aliexpress.com/item/1005010288386483.html) | ~7-9€ | 2.4GHz LoRa module (+27dBm high power). |
| **2x 1M Ohm Resistors** | [AliExpress](https://es.aliexpress.com/item/1005002991902748.html) | <0.50€ | Used for the battery voltage divider. SMD 1206 size. |
| **OLED SSD1306 I2C** (Optional) | [AliExpress](https://es.aliexpress.com/item/1005005970901119.html) | ~1.50€ | Add insulating tape beneath to prevent shorts against the MCU. |
| **2x Push Buttons** | [AliExpress](https://es.aliexpress.com/item/4001125532910.html) | <0.50€ | Search for "3\*4\*2.0 2 Pin Buttons". |
| **Mini buck-boost (Optional)** | [AliExpress](https://es.aliexpress.com/item/1005011637436564.html) | ~3€ | Mini buck-boost to run the E28 at full power. Only for V2.0 and beyond |
| **2.4GHz Antenna & Pigtail (SX only)** | [AliExpress](https://es.aliexpress.com/item/1005004598468979.html) | ~9€ | Ensure you use a dedicated **2.4GHz** antenna, not a sub-GHz one! |
| **Custom PCB** | Custom Gerber | Variable | Order via your favorite fabrication house (JLCPCB, PCBWay, etc.). |

*(Links are non-affiliated and only serve as examples)*

## 🛠️ Mounting & Assembly Instructions

> ⚠️ **Important Safety Warning:** NEVER power on or transmit with the board without a 2.4GHz antenna connected to the E28 module! Doing so can permanently damage the RF power amplifier.

To ensure a clean and hassle-free build, it is recommended to assemble the board in order of component height (lowest profile components first):

### 1️⃣ **Step 1: Ebyte E28 Module Soldering**
Due to the fine castellation pads on the **E28-2G4M27S/SX**, alignment and technique are key:
* **Recommended Method A (Hot Plate):** Apply solder paste to the pads, align the module carefully, and reflow on a hot plate.
* **Recommended Method B (Drag Soldering):** Tack down two corner pads to anchor the module in place. Apply a generous amount of liquid/gel flux, and use **drag soldering** with a **KU tip (knife edge)** and a small amount of solder across the castellated pads. Clean any excess flux with isopropyl alcohol (IPA).
* **Method C:** Patiently and very carefully solder each pad one by one with a fine tip. Reccomended using flux and preheating on a hot bed if possible (80-90ºC). Be really careful since it's really easy to bridge two pads together. Have some soldering wick ready just in case.

### 2️⃣ **Step 2: Power and Microcontroller**
* **Mini Buck-Boost Converter (Optional, V2.0+):** If using the external buck-boost for maximum transmission power (+27dBm), solder it into position now.
* **ProMicro / SuperMini nRF52840:** Solder the MCU board directly to the PCB or use low-profile female pin headers if you prefer it to be removable.

### 3️⃣ **Step 2: SMD Components & Small Hardware**
* **Battery Divider Resistors:** Solder the two SMD 1206 1MΩ (or 680K and 1M) resistors in their designated locations on the PCB.
* **Push Buttons:** Solder the two SMD tactile buttons (User/Reset).
* **Power Selector Jumper (v2.0+):** Configure the solder selector bridge to choose whether you will feed the E28 radio from the ProMicro's onboard regulator or from the external buck-boost module.

### 4️⃣ **Step 4: Screen & Finishing Touches**
* **SSD1306 OLED Display (Optional):** If mounting a display directly above the MCU, **always place a layer of insulating Kapton/electrical tape** underneath the screen module to avoid shorting out component pins on the nRF52 board.
* **Antenna Connection (For E28-2G4M27SX or S without built in anntena):** Snap on your IPEX pigtail and secure your **2.4GHz antenna** before testing.

---

## Firmware & Flashing

Because this board uses a 2.4GHz SX1280 radio instead of the traditional sub-GHz SX1262, you will need to compile or flash a Meshtastic firmware variant matching the pinout. This repository already includes a variant for it.

> ⚠️ **Reminder:** Make sure your `variant.h` configuration maps the SPI busy/dio/reset and TX EN pins accurately to how the Ebyte E28 module is wired to your ProMicro layout!

## Credits & Thanks
- **[gargomoma](https://github.com/gargomoma)** for creating the original open-source `fakeTec_pcb` layout and concept.
- **[lupusworax](https://github.com/gargomoma/fakeTec_pcb/issues/16)** for the intermediate design improvements that this branch directly builds upon.
- Designed and modified for 2.4GHz by [EmilioAl](https://github.com/EmilioAL-Git) & yours truly.

### Disclaimer
No warranty is provided. You build and operate this hardware at your own risk. Always ensure compliance with local radio frequency regulations regarding 2.4GHz transmission power limits.
