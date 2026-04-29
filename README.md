# Raspberry Pi Pico W - Keypad to LED Controller

This repository contains a Raspberry Pi Pico W project where a 4x4 keypad controls 12 LEDs.
The firmware logic is preserved from the provided source and documented for easier maintenance and reuse.

## Features
- 4x4 keypad input scanning via `Keypad.h`.
- Individual LED activation using keys `1..8` and `A..D`.
- Group control:
  - `9` / `0`: ON/OFF all blue LEDs.
  - `*` / `#`: ON/OFF all red LEDs.
- GPIO mapping aligned with the provided Wokwi wiring.

## Repository Structure

```text
.
├── CMakeLists.txt
├── README.md
├── include/
├── src/
│   └── main.cpp
└── docs/
    ├── architecture.md
    └── wiring.md
```

## Quick Start (Wokwi)
1. Open Wokwi and create a Raspberry Pi Pico (or Pico W) project.
2. Paste the provided `diagram.json` into `diagram.json` in Wokwi.
3. Use `src/main.cpp` logic in your Wokwi sketch source.
4. Start simulation and press keypad buttons.

## Run on Real Hardware

### Option A: Arduino-Pico workflow (recommended for this exact code)
Because the source uses Arduino APIs (`pinMode`, `digitalWrite`, `delay`) and `Keypad.h`:
1. Install Arduino IDE.
2. Install **Raspberry Pi Pico/RP2040** board package.
3. Install **Keypad** library from Library Manager.
4. Select **Raspberry Pi Pico W** board.
5. Build and upload `src/main.cpp` content.

### Option B: Pico SDK workflow
If using Pico SDK, you must adapt Arduino-specific APIs/libraries first.
This repository keeps original logic unchanged and focuses on documentation/organization.

## GPIO Summary
See full mapping in [`docs/wiring.md`](docs/wiring.md).

## Wi-Fi Note
No Wi-Fi APIs or credentials are used in the provided firmware.
If Wi-Fi is added later, store credentials in a separate non-versioned config file and never commit secrets.
