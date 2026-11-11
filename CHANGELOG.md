# Changelog

All notable changes to this project are documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [0.1.0] - 2026-11-11

### Added
- ESPHome firmware for an ESP32-C3 driving a Waveshare 1.54" e-Paper V2 (200 × 200).
- Dashboard: solar production, home consumption, four MPPT inputs, battery
  level and power, and solar coverage of the home consumption.
- Home consumption computed from grid import plus SolarFlow output.
- Home Assistant integration through the ESPHome native API, with a
  "Refresh display" button and the computed sensors exposed to HA.
- Wiring, Home Assistant and troubleshooting documentation.
- CI that compiles the firmware on every push.

[0.1.0]: https://github.com/jmleclercq/zendure-esp32-epaper/releases/tag/v0.1.0
