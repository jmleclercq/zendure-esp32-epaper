# Troubleshooting

## The board does not connect to Wi-Fi (`Auth Expired`)

Many ESP32-C3 boards (e.g. SuperMini) fail to associate at full TX power.
The firmware already sets:

```yaml
wifi:
  output_power: 8.5dB
  power_save_mode: none
```

If it still fails, check the credentials in `esphome/secrets.yaml` and the
signal strength shown in the logs (below about -80 dB the link is unreliable).

## The display shows `--` instead of values

The values come from Home Assistant through the ESPHome API.

1. Make sure the device was added in *Settings > Devices & services* (ESPHome)
   with the key from `secrets.yaml`.
2. Check the entity names in the `substitutions` block against
   *Developer tools > States*.
3. Press the **Refresh display** button in Home Assistant.

## The display looks speckled right after boot

The first refresh at boot can be interrupted by the driver. The next refresh
(about 30 seconds later) draws a clean image. The firmware performs a full
refresh on every update (`full_update_every: 1`) to avoid ghosting.

## `-0 W` or wrong sign for the battery

Set `battery_power_sign` to `"1"` or `"-1"` in the `substitutions` block until
the sign is positive while charging. For the Zendure integration used by the
author, `bat_in_out` is negative while charging, hence `"-1"`.

## Solar coverage looks wrong

It is the SolarFlow output divided by the home consumption, and the home
consumption is the grid import plus the SolarFlow output. If your grid sensor
is not the import power (W), adapt `grid_entity` and `grid_power_sign`.
