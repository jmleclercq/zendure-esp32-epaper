# Configuration Home Assistant

## Prérequis

- Home Assistant avec l'intégration Zendure (par ex. *Zendure-HA*, via HACS)
  connectée au SolarFlow 2400 Pro.
- Intégration **ESPHome** activée (l'appareil est découvert automatiquement
  après le premier flash ; la clé API est celle de `secrets.yaml`).

## Entités à identifier

Dans *Outils de développement > États*, repérez les entités et reportez-les
dans le bloc `substitutions` de `esphome/zendure-epaper.yaml` :

| Substitution          | Contenu                               | Unité |
|-----------------------|---------------------------------------|-------|
| `solar_entity`        | Puissance solaire totale              | W     |
| `mppt1_entity` … `mppt4_entity` | Puissance de chaque MPPT    | W     |
| `home_entity`         | Consommation de la maison             | W     |
| `battery_soc_entity`  | Niveau de la batterie                 | %     |
| `battery_power_entity`| Puissance de la batterie              | W     |
| `grid_entity`         | Puissance réseau (soutirage/injection)| W     |

Les noms par défaut sont des **exemples** : ils dépendent de la version de
l'intégration et du nom donné à l'appareil.

## Signes

- `battery_power_sign` : mettre `"-1"` si votre entité est négative en charge.
- `grid_power_sign` : mettre `"-1"` si votre entité est négative en soutirage.

## Taux d'autoconsommation

Calculé dans l'ESPHome :

```
autoconsommation = (production − injection réseau) / production × 100
```

Il est affiché `--` quand la production est inférieure à 10 W.
