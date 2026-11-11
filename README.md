# zendure-esp32-epaper

ESP32-powered e-paper dashboard displaying real-time solar production, home energy consumption, battery status, and self-consumption data from Zendure SolarFlow via Home Assistant and ESPHome.

## Hardware

| Item            | Choice                                          |
|-----------------|-------------------------------------------------|
| Microcontroller | ESP32-C3                                        |
| Display         | Waveshare e-Paper 1.54" V2, 200 × 200 px        |
| Firmware        | ESPHome                                         |
| Data source     | Zendure SolarFlow 2400 Pro via Home Assistant   |
| Power           | USB (battery possible later)                    |

## Display

```
┌────────────────────────┐
│ SolarFlow         14:32│
├───────────┬────────────┤
│PRODUCTION │   HOME     │
│   1850    │    620     │
│     W     │     W      │
├───────────┴────────────┤
│  M1  │  M2  │ M3 │ M4  │
│ 480  │ 470  │ 460│ 440 │
├────────────────────────┤
│ BATTERY                │
│ 85%             +1230 W│
│ [██████████████░░░]    │
├────────────────────────┤
│ SELF-CONSUMPTION   72% │
│ [███████████░░░░░]     │
└────────────────────────┘
```

## Quick start

```bash
pip install esphome
cd esphome
cp secrets.example.yaml secrets.yaml   # then edit it
# adapt the entities in the "substitutions" block of zendure-epaper.yaml
esphome run zendure-epaper.yaml
```

## Documentation

- [Wiring](docs/wiring.md)
- [Home Assistant setup](docs/home-assistant.md)

## Layout

```
esphome/
  zendure-epaper.yaml      main configuration
  secrets.example.yaml     secrets template
docs/                      wiring and HA integration
.github/workflows/         automatic compilation (CI)
```

## Ideas for later

- Battery power supply + `deep_sleep`
- Alternative layout (24 h production graph)
- 3D-printed enclosure

## License

[MIT](LICENSE)
