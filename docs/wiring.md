# Câblage

ESP32-C3 ↔ Waveshare e-Paper 1,54" V2 (SSD1681, 200 × 200).

| Écran (Waveshare) | ESP32-C3 | Remarque                |
|-------------------|----------|-------------------------|
| VCC               | 3V3      | 3,3 V uniquement        |
| GND               | GND      |                         |
| DIN               | GPIO6    | MOSI                    |
| CLK               | GPIO4    | SCK                     |
| CS                | GPIO7    |                         |
| DC                | GPIO10   |                         |
| RST               | GPIO3    |                         |
| BUSY              | GPIO5    |                         |

Les GPIO2, 8 et 9 (broches de strapping) sont volontairement évitées.
Si votre carte ESP32-C3 expose d'autres broches, modifiez les pins dans
`esphome/zendure-epaper.yaml` (blocs `spi:` et `display:`).

## Alimentation

- **Phase 1** : USB 5 V sur la carte ESP32-C3.
- **Phase 2 (option)** : batterie Li-ion 3,7 V via le connecteur de la carte
  (si elle intègre un chargeur) ou un module TP4056. Pour tenir sur batterie,
  ajouter `deep_sleep` dans ESPHome : l'e-paper conserve l'image sans énergie,
  il suffit de réveiller l'ESP toutes les 5 à 15 minutes, de laisser Home
  Assistant pousser les valeurs, de rafraîchir l'écran puis de se rendormir.
