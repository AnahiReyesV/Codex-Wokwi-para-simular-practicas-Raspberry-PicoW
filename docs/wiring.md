# Wiring and GPIO Mapping (Raspberry Pi Pico W)

## Hardware Components (from `diagram.json`)
- 1x Raspberry Pi Pico / Pico W (`wokwi-pi-pico`)
- 1x 4x4 membrane keypad (`wokwi-membrane-keypad`)
- 12x LEDs
  - 8x blue LEDs labeled `1..8`
  - 4x red LEDs labeled `A..D`
- 12x LED current-limiting resistors (`220Ω`, IDs `r1..r12`)
- 4x keypad pull-up resistors (`1kΩ`, IDs `rp1..rp4`)

## GPIO Mapping Table

### Keypad matrix wiring
| Keypad line | Pico W GPIO | Code array |
|---|---:|---|
| C1 | GP19 | `colPins[0]` |
| C2 | GP18 | `colPins[1]` |
| C3 | GP17 | `colPins[2]` |
| C4 | GP16 | `colPins[3]` |
| R1 | GP26 | `rowPins[0]` |
| R2 | GP22 | `rowPins[1]` |
| R3 | GP21 | `rowPins[2]` |
| R4 | GP20 | `rowPins[3]` |

### LED wiring
| LED label | Pico W GPIO | Code index |
|---|---:|---:|
| 1 | GP11 | `ledPins[0]` |
| 2 | GP10 | `ledPins[1]` |
| 3 | GP9  | `ledPins[2]` |
| 4 | GP8  | `ledPins[3]` |
| 5 | GP7  | `ledPins[4]` |
| 6 | GP6  | `ledPins[5]` |
| 7 | GP5  | `ledPins[6]` |
| 8 | GP4  | `ledPins[7]` |
| A | GP3  | `ledPins[8]` |
| B | GP2  | `ledPins[9]` |
| C | GP28 | `ledPins[10]` |
| D | GP27 | `ledPins[11]` |

## Power and Ground
- All LED cathodes are tied to Pico GND.
- Each LED anode is driven by a GPIO through a 220Ω resistor.
- Keypad row lines include external pull-ups to 3V3 via four 1kΩ resistors.

## Assumptions noted
- The supplied logic uses `Keypad.h` and Arduino-style `setup()/loop()`. Documentation keeps this behavior unchanged and maps it directly to Pico W GPIO naming.
