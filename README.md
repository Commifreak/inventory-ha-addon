# Inventory – Home Assistant add-on

Home Assistant add-on repository for the [Inventory](https://github.com/Commifreak/inventory)
agent: monitors disk health, Home Assistant / add-on updates and Raspberry Pi power of
your Home Assistant host and reports it to your Inventory server.

[![Add repository to my Home Assistant](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FCommifreak%2Finventory-ha-addon)

See [inventory-agent/DOCS.md](inventory-agent/DOCS.md) for installation and details.

The add-on image (`ghcr.io/commifreak/inventory-ha-agent`) is built from the main
repository for every release; this repository only holds the add-on definition. Its
version is updated automatically by the release workflow of the main repository.

License: MIT
