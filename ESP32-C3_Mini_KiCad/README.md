# ESP32-C3 Mini Evaluation Board in KiCad 10

A custom PCB design for the **ESP32-C3 Mini** microcontroller created in KiCad 10

## Project Overview

This project is a clean, minimal development board created by following the [
KiCad 9 ESP32-C3 Mini PCB Design | Full Schematic Walkthrough] from https://www.youtube.com/watch?v=-iZbwzr0dS8

It uses a hierarchical schematic structure to separate the system block diagram from the detailed power, microcontroller, and I/O circuitry.

## Hardware Specifications
 **Microcontroller:** `ESP32-C3-WROOM-02` (integrates Wi-Fi, flash memory, RF components, and an internal 40 MHz system crystal)
* **USB-C Input & Protection:** 
  * 16-pin USB 2.0 Type-C receptacle configured as a 5V power sink using `5.1 kΩ` pull-down resistors on `CC1` and `CC2`
  * Native USB 2.0 differential data lines (`IO18` / `IO19`) protected by a `USBLC6` low-capacitance ESD protection array
  * `VBUS` 5V line protected by a unidirectional PES-series ESD diode and a Pi-filter stage (`4.7 µF` capacitors with a `0 Ω` placeholder resistor)
* **Voltage Regulation:** `AP2112` 3.3V LDO linear regulator (600 mA output) with `4.7 µF` input/output decoupling capacitors
* **External RTC Clock:** `32.768 kHz` (`ABS07` series) low-speed crystal with load capacitors and a feedback resistor connected to `IO0` and `IO1` for real-time clock and low-power operation
* **Boot & Reset Controls:**
  * Manual **Reset** push-button on the `EN` pin with a `10 kΩ` pull-up resistor and RC debounce filter (`100 Ω` + `100 nF`)
  * Manual **Boot** push-button on strapping pin `IO9` (`10 kΩ` pull-up) to enter firmware download mode
  * Dedicated `10 kΩ` pull-up resistors on strapping pins `IO2` and `IO8` for reliable SPI flash booting
* **Expansion Headers:** Dual 8-pin (`2.54 mm` pitch) headers exposing `3.3V`, `GND`, `UART`, `JTAG`, and general-purpose GPIOs in physical module pin order

## Repository Contents
* **`ESP32-C3-Mini.kicad_pro`** – Main KiCad 9 project file
* **`ESP32-C3-Mini.kicad_sch`** – Root schematic sheet
* **`BlockDiagram.kicad_sch`** – High-level system block diagram
* **`ESP32C3Mini.kicad_sch`** – Detailed hierarchical schematic sub-sheet
* **`ESP32-C3-Mini.kicad_pcb`** – PCB layout file
* **`ESP32-C3-Mini.png`** – Board schematic/layout preview

## Acknowledgements
* Design based on the tutorial by **PCB Learning Collective**: [KiCad 9 ESP32-C3 Mini PCB Design | Full Schematic Walkthrough] (https://www.youtube.com/watch?v=-iZbwzr0dS8)

## License
This project is licensed under the terms of the [LICENSE](../LICENSE) file in the root directory.

