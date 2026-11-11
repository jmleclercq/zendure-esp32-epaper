# Contributing

Thanks for your interest! Issues and pull requests are welcome.

## Reporting a problem

Open an issue and include:
- your hardware (board, display model) and ESPHome version;
- the relevant ESPHome logs (`esphome logs esphome/zendure-epaper.yaml`);
- what you expected and what the display shows.

**Never paste** `secrets.yaml`, API keys, Wi-Fi passwords or Home Assistant
tokens. Redact them from logs before posting.

## Proposing a change

1. Fork the repository and create a branch.
2. Keep your changes focused and consistent with the existing style.
3. Make sure the firmware compiles:
   ```bash
   cd esphome
   cp secrets.example.yaml secrets.yaml
   esphome compile zendure-epaper.yaml
   ```
4. Update the README, `docs/` and `CHANGELOG.md` if behavior changes.
5. Open a pull request describing what and why.

Entity names in `zendure-epaper.yaml` default to a SolarFlow 2400 Pro with the
Zendure-HA integration. Adjust them through the `substitutions` block rather
than hard-coding new ones.
