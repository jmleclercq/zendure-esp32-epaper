# zendure-esp32-epaper

Tableau de bord e-paper piloté par ESP32 : production solaire, consommation de la maison, batterie et autoconsommation en temps réel, à partir d'un Zendure SolarFlow via Home Assistant et ESPHome.

*ESP32-powered e-paper dashboard displaying real-time solar production, home energy consumption, battery status, and self-consumption data from Zendure SolarFlow via Home Assistant and ESPHome.*

## Matériel

| Élément          | Choix                                          |
|------------------|------------------------------------------------|
| Microcontrôleur  | ESP32-C3                                       |
| Écran            | Waveshare e-Paper 1,54" V2, 200 × 200 px       |
| Firmware         | ESPHome                                        |
| Source de données| Zendure SolarFlow 2400 Pro via Home Assistant  |
| Alimentation     | USB (batterie possible ultérieurement)         |

## Affichage

```
┌────────────────────────┐
│ SolarFlow         14:32│
├───────────┬────────────┤
│PRODUCTION │  MAISON    │
│   1850    │    620     │
│     W     │     W      │
├───────────┴────────────┤
│  M1  │  M2  │ M3 │ M4 │
│ 480  │ 470  │ 460│ 440│
├────────────────────────┤
│ BATTERIE                │
│ 85%             +1230 W│
│ [██████████████░░░]    │
├────────────────────────┤
│ AUTOCONSOMMATION   72% │
│ [███████████░░░░░]     │
└────────────────────────┘
```

## Démarrage rapide

```bash
pip install esphome
cd esphome
cp secrets.example.yaml secrets.yaml   # puis éditer
# adapter les entités dans le bloc "substitutions" de zendure-epaper.yaml
esphome run zendure-epaper.yaml
```

## Documentation

- [Câblage](docs/wiring.md)
- [Configuration Home Assistant](docs/home-assistant.md)

## Structure

```
esphome/
  zendure-epaper.yaml      configuration principale
  secrets.example.yaml     modèle de secrets
docs/                      câblage et intégration HA
.github/workflows/         compilation automatique (CI)
```

## Pistes d'évolution

- Alimentation par batterie + `deep_sleep`
- Mise en page alternative (graphique de production sur 24 h)
- Boîtier imprimé en 3D

## Licence

[MIT](LICENSE)
