# Home Assistant: Home & Rental Property Automation

A monitoring and control platform for the home and, later, for short-term rental properties. Covers heating and cooling, WiFi, internet health, the doorbell camera and the garage door, with lighting, door access, irrigation and TVs to come.

## How it's built

- **Home Assistant** runs onsite at each property as the hub that talks to every device.
  - Phase 1 (pilot at home): a Raspberry Pi 4/5 running Home Assistant OS.
  - Rentals: Home Assistant Green, one per property.
- **Remote access** goes through Home Assistant Cloud (Nabu Casa). No ports are opened to the internet.
- **This repo** holds the Home Assistant configuration, custom integrations (such as Meraki), helper scripts and, later, the multi-property `fleet` dashboard.

| System | Integration |
|---|---|
| Heating/cooling (Nest) | Home Assistant Google Nest integration |
| Doorbell (Nest) | Home Assistant Google Nest integration |
| Garage (Aladdin Connect) | Home Assistant Aladdin Connect integration (needs Home Assistant Cloud) |
| WiFi/network (Cisco Meraki) | Custom integration on the Meraki Dashboard API (Phase 2) |
| Internet (TDS) | Ping + Speedtest integrations, plus Meraki uplink health (Phase 2) |

## Repo layout

```
homeassistant/          Home Assistant config (secrets.yaml is never committed)
  configuration.yaml
  packages/             one file per feature: climate, garage, network, ...
  dashboards/           dashboard definitions
  custom_components/    our own integrations (Meraki lands here)
scripts/                helper Python scripts
fleet/                  Phase 3: multi-property dashboard
docs/                   setup guides, roadmap, integration notes
```

## Start here

1. [Set up Home Assistant on the Raspberry Pi](docs/setup-raspberry-pi.md)
2. [Connect your devices](docs/integrations.md)
3. [Roadmap](docs/roadmap.md)
