# Wiring

ESP32-C3 ↔ Waveshare e-Paper 1.54" V2 (SSD1681, 200 × 200).

| Display (Waveshare) | ESP32-C3 | Note             |
|---------------------|----------|------------------|
| VCC                 | 3V3      | 3.3 V only       |
| GND                 | GND      |                  |
| DIN                 | GPIO6    | MOSI             |
| CLK                 | GPIO4    | SCK              |
| CS                  | GPIO7    |                  |
| DC                  | GPIO10   |                  |
| RST                 | GPIO3    |                  |
| BUSY                | GPIO5    |                  |

GPIO2, 8 and 9 (strapping pins) are deliberately avoided.
If your ESP32-C3 board exposes different pins, change them in
`esphome/zendure-epaper.yaml` (`spi:` and `display:` blocks).

## Power

- **Phase 1**: 5 V USB on the ESP32-C3 board.
- **Phase 2 (optional)**: 3.7 V Li-ion battery through the board connector
  (if it has a charger) or a TP4056 module. To run on battery, add
  `deep_sleep` in ESPHome: the e-paper keeps its image without power, so just
  wake the ESP every 5 to 15 minutes, let Home Assistant push the values,
  refresh the display, then go back to sleep.
