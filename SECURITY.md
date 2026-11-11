# Security policy

This project is a hobby firmware for a local display. It has no server
component, but it handles Wi-Fi and Home Assistant credentials.

## Reporting a vulnerability

Please report security issues privately through GitHub's
[private vulnerability reporting](https://github.com/jmleclercq/zendure-esp32-epaper/security/advisories/new)
instead of opening a public issue.

## Good practice

- Keep `esphome/secrets.yaml` out of version control (it is git-ignored).
- Generate a unique API encryption key per device: `openssl rand -base64 32`.
- Use a dedicated Home Assistant token only when needed, and revoke it afterwards.
