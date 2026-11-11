# Home Assistant setup

## Prerequisites

- Home Assistant with the Zendure integration (e.g. *Zendure-HA*, via HACS)
  connected to the SolarFlow 2400 Pro.
- **ESPHome** integration enabled (the device is discovered automatically
  after the first flash; the API key is the one from `secrets.yaml`).

## Entities to identify

In *Developer tools > States*, find your entities and copy them into the
`substitutions` block of `esphome/zendure-epaper.yaml`:

| Substitution                    | Content                            | Unit |
|---------------------------------|------------------------------------|------|
| `solar_entity`                  | Total solar power                  | W    |
| `mppt1_entity` … `mppt4_entity` | Power of each MPPT                 | W    |
| `home_entity`                   | Home consumption                   | W    |
| `battery_soc_entity`            | Battery level                      | %    |
| `battery_power_entity`          | Battery power                      | W    |
| `grid_entity`                   | Grid power (import/export)         | W    |

The default names are **examples**: they depend on the integration version and
on the name given to the device.

## Signs

- `battery_power_sign`: set to `"-1"` if your entity is negative when charging.
- `grid_power_sign`: set to `"-1"` if your entity is negative when importing.

## Self-consumption rate

Computed in ESPHome:

```
self-consumption = (production − grid export) / production × 100
```

It shows `--` when production is below 10 W.
