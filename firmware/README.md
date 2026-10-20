# firmware — Phase B (Edge)

MicroPython code that runs on the ESP32.

- `boot.py` — runs first on every reset (Wi-Fi, config)
- `main.py` — entry point, runs after `boot.py`
- `lib/` — reusable modules (drivers, helpers)

Wi-Fi credentials go in `secrets.py` (git-ignored, never committed).

Upload: `mpremote cp firmware/*.py : && mpremote reset`
