# Solar 18650 USB Battery Charger

A compact hardware project that charges a single 18650 Li-ion cell using solar energy, stores it safely, and outputs regulated 5V via USB. Includes real-time voltage, current, and battery percentage display for monitoring.

## Features
- Charges 18650 cell from solar panel (~6V input)
- USB 5V output via boost converter (MT3608)
- Battery management with TP4056 (with protection)
- Live monitoring: voltage, current, charge %
- Designed for portable, off-grid applications

## Components
| Component | Description | Link |
|-----------|-------------|------|
| TP4056 | Li-ion charging + protection | - |
| MT3608 | Boost converter (3.7V → 5V) | - |
| 18650 Battery | Rechargeable Lithium-ion cell | - |
| Solar Panel | 5.5–6V, 1–2W recommended | - |
| INA219 | Current/voltage sensor (I2C) | - |
| MSP420 | OLED display | - |
| Microcontroller | ATmega32U4 Pro Micro | - |

## Wiring Diagram


## Power Flow
1. Solar panel feeds TP4056 charger
2. TP4056 charges and protects 18650 cell
3. MT3608 boosts cell output to 5V USB
4. INA219 + microcontroller read voltage/current
5. Display shows real-time data

## Firmware
Firmware is in `/code`. Uses:
- Adafruit INA219 library
- Adafruit SSD1306 library
- Arduino core for ATmega32U4

Upload via Arduino IDE or PlatformIO.

## Safety Notes
- Use a TP4056 with protection circuit (not the bare one!)
- Do not exceed panel voltage/current ratings
- Keep battery within 3.0V–4.2V range

## Future Plans
- Auto shutoff if battery drops too low
- Enclosure design (weatherproof)

## License
MIT

## Author
Caleb Thomas — 2025

