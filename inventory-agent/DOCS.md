# Inventory Agent

Reports this Home Assistant host to an [Inventory](https://github.com/Commifreak/inventory)
server. The agent only reads data – it never changes anything on the host.

## What is reported

- **Disks:** SMART health, wear and temperature of SSDs/HDDs; SD card and eMMC
  data. Kernel errors of SD cards and disks.
- **Raspberry Pi power:** undervoltage and throttling – the most common cause of
  corrupted SD cards.
- **Updates:** available updates of Home Assistant OS, Core, Supervisor and all
  add-ons (alert when they stay pending too long).
- **Software:** Home Assistant versions and installed add-ons, with a change log.
- **System:** hardware, memory, network interfaces, data disk usage.

## Installation

1. Inventory server: **Settings → Install agents** → section *Home Assistant OS*.
2. Add this add-on repository to Home Assistant (button on that page or
   *Settings → Add-ons → Add-on store → ⋮ → Repositories*).
3. Install **Inventory Agent**, open *Configuration* and enter the server URL and
   the enrollment token shown on the install page.
4. For SMART of SSDs and hard disks (e.g. a USB SSD on a Raspberry Pi): turn off
   **Protection mode** on the add-on's *Info* tab. Home Assistant only grants the
   hardware access below to unprotected add-ons. Without it the agent still
   reports everything else and lists the disks without SMART values.
5. Enable *Start on boot* and *Watchdog*, then start the add-on.

The device appears in the Inventory device list within a minute. The enrollment
token is only used for the first start; the agent keeps its own credential in the
add-on data and survives restarts and Home Assistant OS updates.

## Permissions

- **Full hardware access** – required to read SMART data of disks. Home Assistant
  applies it only with *Protection mode* turned off and lowers the add-on's
  security rating because of it.
- **SYS_RAWIO capability** – SMART of SATA and USB disks (e.g. an SSD on a
  Raspberry Pi) uses ATA pass-through commands, which the kernel only allows
  with this capability. The agent only reads.
- **Host network** – real network interfaces and host name.
- **Journal** – kernel messages for undervoltage and disk errors.
- **Supervisor API** (read-only role) – versions and available updates.

## Updates

New agent versions are published as add-on updates. Enable *Auto update* in the
add-on to install them automatically.

## Troubleshooting

The add-on log shows the agent's messages. The Inventory server shows the latest
warnings and errors of the agent on the device's *Agent* tab.
