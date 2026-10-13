# fakeTec_pcb - 2.4GHz Edition

A low-cost, high-power 2.4GHz nRF52 device with the form factor of the Heltec v2 & v3 devices, fully compatible with [Meshtastic®](https://meshtastic.org/). 

This repository is a hardware fork derived from **[lupusworax's variant](https://github.com/gargomoma/fakeTec_pcb/issues/16)**, which was originally based on the excellent base design by **[gargomoma](https://github.com/gargomoma)**.

> ⚠️ **Legal Disclaimer:**  
> **🇬🇧:** It is the sole responsibility of the end user to ensure that the assembly, configuration, and operation of these PCBs comply with applicable local telecommunications laws and regulations.

## 🚀 The 2.4GHz Difference
While the original versions focus on sub-GHz LoRa modules (like the HT-RA62 or RA-01SH), this version swaps the RF section out for an **Ebyte E28-2G4M27S / SX** module. This brings **2.4GHz LoRa capabilities** and a powerful +27dBm output to the compact Heltec footprint. 

*Note: The E28 module overhangs the PCB slightly, so existing 3D-printed FakeTec/Heltec cases may require minor modifications.*

## 📸 Hardware Preview

<details>
<summary><b>Click to view PCB render/photos</b></summary>
<br>
<img width="545" alt="fakeTec 2.4GHz Edition" src="https://github.com/user-attachments/assets/c57fbee2-593e-4f86-9308-69756b5a0a54" />
</details>

## ✨ Features
- **2.4GHz LoRa Mesh:** Built around the powerful SX1280-based Ebyte E28-2G4M27SX module.
- **Heltec v3 Form Factor:** Fits seamlessly into existing community 3D-printed cases meant for the original FakeTec or Heltec v3 (with slight case modifications for the module overhang).
- **nRF52840 MCU:** Powered by the affordable ProMicro / SuperMini nRF52840 board.
- **I2C Expansion:** Dedicated side ports ready to accept a standard SSD1306 OLED screen.
- **Battery Monitoring:** Integrated battery voltage sensing via 1206 SMD resistors.
- **Mounting:** Standard 2mm mounting holes.

## 📜 Changelog

### [v2.1] - *Pending test*
- **Silkscreen Improvements:** Redesigned to match the original fakeTec V4 with complete pin markings and a handy resistor value guide. The power selector now clearly indicates whether the ProMicro or external buck-boost is active.
- **Thicker Traces:** Increased trace thickness from the power selector to the E28 input for better current handling.

### [v2.0] - *Pending test*
- **Buck-Boost Converter Integration:** Added support for a buck-boost converter to allow the E28 to operate at its full +27dBm power (the built-in ProMicro 3.3V source only allows up to ~24dBm).
- **Power Source Selector:** Added a solder bridge selector to easily choose between running the E28 via the built-in ProMicro regulator or the external buck-boost converter.

### [v1.0] - *Initial 2.4GHz Release*
- **RF Module Migration:** Replaced sub-GHz LoRa module footprint with **Ebyte E28-2G4M27S / SX** (+27dBm 2.4GHz LoRa).
- **PCB Layout Updates:** Re-routed SPI/RF traces and pad layouts to accommodate the E28 footprint and pinout.
- **Firmware Variant:** Included a ready-to-use Meshtastic firmware variant tailored for this specific pin mapping.
- **Documentation & BOM:** Updated bill of materials, parts sources, and credits to reflect 2.4GHz requirements.

## 🛒 Bill of Materials (BOM)

| Part | Source / Example | Approx. Cost | Note |
| :--- | :--- | :--- | :--- |
| **ProMicro nRF52840** (SuperMini) | [AliExpress](https://es.aliexpress.com/item/1005009116054547.html) | ~€5.00 | Double-check bootloader compatibility before soldering. |
| **Ebyte E28-2G4M27S / SX** | [AliExpress](https://es.aliexpress.com/item/1005010288386483.html) | ~€7-9.00 | 2.4GHz LoRa module (+27dBm high power). |
| **2x 1MΩ Resistors** | [AliExpress](https://es.aliexpress.com/item/1005002991902748.html) | <€0.50 | Battery voltage divider. SMD 1206 size. |
| **OLED SSD1306 I2C** *(Optional)* | [AliExpress](https://es.aliexpress.com/item/1005005970901119.html) | ~€1.50 | Add insulating tape beneath to prevent MCU shorts. |
| **2x Push Buttons** | [AliExpress](https://es.aliexpress.com/item/4001125532910.html) | <€0.50 | Search for "3x4x2.0 2 Pin Buttons". |
| **Mini Buck-Boost** *(Optional)* | [AliExpress](https://es.aliexpress.com/item/1005011637436564.html) | ~€3.00 | Required to run the E28 at full power. *(v2.0+ only)* |
| **2.4GHz Antenna & Pigtail** | [AliExpress](https://es.aliexpress.com/item/1005004598468979.html) | ~€9.00 | Ensure you use a dedicated **2.4GHz** antenna (not sub-GHz). |
| **Custom PCB** | Custom Gerber | Variable | Order via your favorite fabrication house (JLCPCB, PCBWay, etc.). |

*(Note: Links are non-affiliated and provided only as examples)*

## 🛠️ Mounting & Assembly Instructions

> ⚠️ **CRITICAL WARNING:** NEVER power on or transmit with the board without a 2.4GHz antenna connected to the E28 module! Operating without an antenna will permanently damage the RF power amplifier.

To ensure a clean and hassle-free build, assemble the board in order of component height (lowest profile components first):

### 1️⃣ Step 1: Ebyte E28 Module Soldering
Due to the fine castellation pads on the **E28-2G4M27S/SX**, alignment and technique are key:
- **Method A (Hot Plate - Recommended):** Apply solder paste to the pads, align the module carefully, and reflow on a hot plate.
- **Method B (Drag Soldering):** Tack down two opposite corner pads to anchor the module. Apply generous liquid/gel flux, and use drag soldering with a knife-edge (KU) tip. Clean excess flux with isopropyl alcohol (IPA).
- **Method C (Pin-by-Pin):** Carefully solder each pad one by one with a fine tip. Preheating the board (80-90ºC) and using high-quality flux is highly recommended. Have solder wick ready to clear any bridges.

### 2️⃣ Step 2: Power and Microcontroller
- **Mini Buck-Boost Converter (v2.0+ only):** If using external power for maximum transmission (+27dBm), solder the buck-boost module into position now.
- **ProMicro / SuperMini nRF52840:** Solder the MCU board directly to the PCB, or use low-profile female pin headers if you want it to be removable.

### 3️⃣ Step 3: SMD Components & Small Hardware
- **Battery Divider Resistors:** Solder the two SMD 1206 resistors (1MΩ / 1MΩ, or 680KΩ / 1MΩ) in their designated locations.
- **Push Buttons:** Solder the two SMD tactile buttons (User & Reset).
- **Power Selector Jumper (v2.0+ only):** Bridge the solder selector to choose your E28 power source: the ProMicro's onboard regulator OR the external buck-boost module.

### 4️⃣ Step 4: Screen & Finishing Touches
- **SSD1306 OLED Display (Optional):** If mounting a display directly above the MCU, **you must place a layer of insulating Kapton or electrical tape** underneath the screen module to prevent its pins from shorting against the nRF52 board.
- **Antenna Connection:** Snap on your IPEX pigtail and secure your **2.4GHz antenna** before plugging in USB or battery power.

## 💻 Firmware & Flashing

Because this board uses a 2.4GHz SX1280 radio instead of the traditional sub-GHz SX1262, you must compile or flash a Meshtastic firmware variant matching this specific pinout. 

This repository includes a ready-to-use variant. 

> ⚠️ **Developers:** If compiling your own build, ensure your `variant.h` maps the SPI, BUSY, DIO, RESET, and TX_EN pins accurately to the Ebyte E28 / ProMicro layout.

## 🤝 Credits & Thanks
- **[gargomoma](https://github.com/gargomoma)** for creating the original open-source `fakeTec_pcb` layout and concept.
- **[lupusworax](https://github.com/gargomoma/fakeTec_pcb/issues/16)** for the intermediate design improvements that this branch directly builds upon.
- Designed and modified for 2.4GHz by **[EmilioAl](https://github.com/EmilioAL-Git)** & contributors.

---
**Disclaimer:** *No warranty is provided. You build and operate this hardware entirely at your own risk. Always ensure compliance with local radio frequency regulations regarding 2.4GHz transmission power limits.*
