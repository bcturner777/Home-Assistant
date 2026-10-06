# Connecting your devices

Do these in order. Each one is added in Home Assistant under **Settings › Devices & services › Add integration**.

## 1. Internet monitoring (Ping + Speedtest)

TDS has no public API, so we watch the connection from inside the house.

- **Ping:** add the *Ping (ICMP)* integration twice, once for `1.1.1.1` and once for `8.8.8.8`. If both go offline, the internet is down.
- **Speedtest.net:** add *Speedtest.net*. It measures download speed, upload speed and latency on a schedule, which builds a history you can use in conversations with TDS.

## 2. Aladdin Connect (garage)

- Requires **Home Assistant Cloud** to be active.
- Add *Aladdin Connect* and sign in with your Genie/Aladdin account.
- You get open/close control, the door state, and backup battery level (that sensor is disabled by default).
- Limitations: cloud only, and it only works with doors your account owns, not shared ones.

## 3. Google Nest (thermostat + doorbell)

This one has the most steps, but you only do it once.

1. Use a **personal** Google account. Google Workspace accounts are not supported.
2. Pay the one-time **US$5 Device Access fee** at https://console.nest.google.com/device-access.
3. Follow the Home Assistant guide, which walks you through creating a Google Cloud project, an OAuth client and a Pub/Sub topic: https://www.home-assistant.io/integrations/nest/
4. **Thermostat:** current temperature, humidity, mode, setpoints and fan.
5. **Doorbell:** ring, motion and person events; live view; clips on doorbell models. Some newer doorbells set up in the Google Home app have limits on snapshots and ring events, so we'll confirm what yours supports.

## 4. Cisco Meraki (Phase 2)

The built-in Meraki integration only does presence detection. For device health, client counts, guest WiFi on/off and internet uplink loss/latency, we'll build a custom integration on the Meraki Dashboard API in `homeassistant/custom_components/`.

To prepare, create a Dashboard API key in Meraki (Organization › Settings › Dashboard API access, then My profile › API access). **Do not paste the key into this repo or into chat.** It goes in `secrets.yaml` on the Pi.

## Sources

- https://www.home-assistant.io/integrations/aladdin_connect
- https://www.home-assistant.io/integrations/nest/
- https://developers.home.google.com/device-access
- https://www.home-assistant.io/integrations/meraki/
