# Firmware Architecture

## Overview
This project implements a keypad-driven LED controller for Raspberry Pi Pico W using an Arduino-style event loop.

## Source Layout
- `src/main.cpp`: Main firmware logic (keypad read + LED control state changes).
- `include/`: Reserved for future headers.
- `docs/wiring.md`: Hardware wiring and pin mapping.
- `README.md`: Build/run instructions and behavior summary.

## Module Behavior

### 1) Static configuration
- `keys[4][4]`: Key layout matrix.
- `ledPins[12]`: GPIO mapping for 12 LEDs.
- `rowPins[4]`, `colPins[4]`: Keypad line mappings.

### 2) Initialization (`setup`)
- Configures all LED pins as outputs.
- Forces initial LED state to OFF.

### 3) Runtime loop (`loop`)
- Polls one key event using `keypad.getKey()`.
- If a valid key is detected:
  - Numeric keys `1..8`: turn ON corresponding blue LED.
  - `9`: turn ON all blue LEDs (indices `0..7`).
  - `0`: turn OFF all blue LEDs (indices `0..7`).
  - `A..D`: turn ON corresponding red LED.
  - `*`: turn ON all red LEDs (indices `8..11`).
  - `#`: turn OFF all red LEDs (indices `8..11`).
- Waits 10 ms between loop iterations.

## Design Notes
- The implementation is intentionally simple and non-blocking except for a short fixed delay.
- No Wi-Fi logic is present in the provided source.
