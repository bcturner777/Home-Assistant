# Set up Home Assistant on the Raspberry Pi

This is for the Phase 1 pilot at home on a Raspberry Pi 4 or 5. The same steps apply later on a Home Assistant Green, except that the Green comes with Home Assistant already installed, so you start at step 3.

## What you need

- Raspberry Pi 4 or 5 with its official USB-C power supply
- A microSD card of 32 GB or more. **Flashing erases everything on it.**
- An Ethernet cable to your Meraki switch or router
- Your Mac, for flashing the card and finishing setup

## 1. Flash Home Assistant OS onto the SD card

1. On your Mac, install **Raspberry Pi Imager** from https://www.raspberrypi.com/software/.
2. Open Imager and choose:
   - **Device:** your Pi model (4 or 5)
   - **Operating system:** *Other specific-purpose OS › Home assistants and home automation › Home Assistant*, then the build that matches your Pi
   - **Storage:** the microSD card
3. Click **Next** and write the card. If Imager offers OS customization settings, skip them, because Home Assistant OS ignores them.

## 2. Boot the Pi

1. Put the card in the Pi and connect it to the network with Ethernet. WiFi is not recommended for the hub.
2. Plug in the power. The first boot takes several minutes while Home Assistant downloads its latest version.

## 3. Finish setup in the browser

1. On your Mac, open **http://homeassistant.local:8123**.
   - If that page doesn't load, find the Pi's IP address in the Meraki dashboard (Network-wide › Clients, look for "homeassistant") and open `http://<that-ip>:8123`.
2. Create your owner account. Use a strong password and store it in your password manager.
3. Set your home location, time zone and units.
4. Home Assistant will suggest devices it found on your network. You can skip these for now.

## 4. Recommended first settings

- **Give the Pi a fixed IP address.** In Meraki, add a DHCP reservation for the Pi so its address never changes.
- **Turn on automatic backups** under Settings › System › Backups. Back up daily and keep the recent copies.
- **Install the File editor or Studio Code Server add-on** under Settings › Add-ons. These let you edit the config files from this repo.
- **Set up Home Assistant Cloud** under Settings › Home Assistant Cloud. You need it for remote access and for Aladdin Connect.

## 5. Next

Connect your devices: [integrations.md](integrations.md).
