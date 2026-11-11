# Home Assistant setup

## Prerequisites

- Home Assistant with the Zendure integration (e.g. *Zendure-HA*, via HACS)
  connected to the SolarFlow 2400 Pro.
- **ESPHome** integration enabled (the device is discovered automatically
  after the first flash; the API key is the one from `secrets.yaml`).

## Entities to identify

In *Developer tools > States*, find your entities and copy them into the
`substitutions` block of `esphome/zendure-epaper.yaml`:

| Substitution                    | Content                                         | Unit |
|---------------------------------|-------------------------------------------------|------|
| `solar_entity`                  | Total solar power                               | W    |
| `mppt1_entity` … `mppt4_entity` | Power of each MPPT                              | W    |
| `sf_output_entity`              | Power the SolarFlow delivers to the house       | W    |
| `battery_soc_entity`            | Battery level                                   | %    |
| `battery_power_entity`          | Battery power                                   | W    |
| `grid_entity`                   | Grid power from your meter (import)             | W    |

The default names are **examples**: they depend on the integration version and
on the name given to the device.

## Signs

- `battery_power_sign`: set to `"-1"` if your entity is negative when charging.
- `grid_power_sign`: set to `"-1"` if your entity is negative when importing.

## Computed values

Both are computed in ESPHome and also exposed to Home Assistant:

```
home consumption = grid import + SolarFlow output to the house
solar coverage   = SolarFlow output / home consumption × 100
```

The grid import comes from `grid_entity`. Only positive values (import) are
counted; use `grid_power_sign` if your meter reports import as negative.
A sensor in VA works too, it is used as watts.
"Solar coverage" includes energy the SolarFlow delivers from its battery.
It shows `--` when the home consumption is unknown.
