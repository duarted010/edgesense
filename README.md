# EdgeSense

An end-to-end IoT system built in 30 days: sensors on an **ESP32** process data at the edge with **MicroPython**, publish telemetry over **MQTT**, a **FastAPI** backend stores and serves it, and a **Raspberry Pi** gateway bridges local buses (serial / I2C / SPI).

> Learning-in-public project. Every day = one commit + one log entry in [`docs/daily-log`](docs/daily-log).

## Architecture

```
 [sensors / actuators]
          │  GPIO · ADC · PWM · I2C
          ▼
 ┌──────────────────┐   MQTT / WebSockets   ┌──────────────────┐     SQL / NoSQL
 │  ESP32 (edge)    │ ────────────────────▶ │  FastAPI backend │ ─────────────▶ [DB]
 │  MicroPython     │ ◀──── commands ────── │  + MQTT broker   │
 └──────────────────┘                       └──────────────────┘
          ▲  serial / I2C / SPI                      ▲
          └──────────── Raspberry Pi gateway ────────┘
```

## Roadmap

| Phase | Focus | Days | Status |
|-------|-------|------|--------|
| **B — Edge** | MicroPython on ESP32: GPIO, interrupts, PWM, ADC, sensors, timers, edge logic, storage, Wi-Fi, low power | 1–10 | 🟡 In progress |
| **A — IoT + Backend** | MQTT, telemetry, commands, FastAPI, databases, WebSockets | 11–20 | ⚪ Planned |
| **C — Gateway** | Raspberry Pi gateway with serial / I2C / SPI | 21–30 | ⚪ Planned |

## Repository structure

```
edgesense/
├── firmware/      # Phase B — MicroPython code that runs on the ESP32
├── backend/       # Phase A — FastAPI service + MQTT client
├── gateway/       # Phase C — Raspberry Pi gateway
├── hardware/      # Schematics & wiring (KiCad / Fritzing), BOM
└── docs/
    └── daily-log/ # One markdown entry per day
```

## Hardware

- ESP32 dev board
- Breadboard, jumper wires, LEDs, resistors, push buttons
- Assorted sensors & actuators (DHT, potentiometer, …)
- Raspberry Pi (Phase C)

## Getting started (firmware)

1. Install tools: [Thonny](https://thonny.org/) or `pip install esptool mpremote`
2. Flash MicroPython onto the ESP32 — see the [official guide](https://docs.micropython.org/en/latest/esp32/tutorial/intro.html)
3. Open the REPL: `mpremote connect auto repl`
4. Copy and run the code: `mpremote cp firmware/*.py : && mpremote reset`

## Daily log

| Day | Topic | Log |
|-----|-------|-----|
| 1 | Setup + MicroPython blink | [day-01](docs/daily-log/day-01.md) |

## Author

Daniel Duarte — [@duarted010](https://github.com/duarted010)
