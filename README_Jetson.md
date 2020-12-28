# This shows an experimental method to install Home Assistance on Jetson Nano Developoer Kit

## Prerequisite 

* Install Intel 8265NGW Wi-Fi/BT card on the M.2 slot, as HASS requires Bluetooth connection to some devices.
* Install JetPack 4.4.1 image on 64GB microSD card
    * Auto-login


## Install Home Assistant Supervised

This document shows the installation of Home Assistant Supervised on Jetson Nano.

There are other alternative installation methods;
* Recommended
    * Home Assistant OS
    * Home Assistant Container
* Alternative installs
    * Home Assisstant Core
    * **Home Assistant Supervised** <--
    * vent (as your user)

https://www.home-assistant.io/docs/installation/

## Before install

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -y jq curl
```

## Installation process

### Running installer.sh

```bash
cd
git clone https://github.com/tokk-nv/hass-supervised-installer
cd hass-supervised-installer
sudo bash ./installer.sh --machine jetson
```

### Install process

> [info] Do you want to proceed with overwriting the /etc/network/interfaces file? [N/y]

`N`

If it goes well, you should see this output at the end.

```
[info] Home Assistant supervised is now installed
[info] First setup will take some time, when it's ready you can reach it here:
[info] http://192.168.1.134:8123
[info]
```

### Post-install verification

```bash
$ sudo docker ps
[sudo] password for jetson:
CONTAINER ID        IMAGE                                     COMMAND             CREATED             STATUS              PORTS               NAMES
20f01b5257e0        homeassistant/aarch64-hassio-supervisor   "/init"             23 minutes ago      Up 23 minutes                           hassio_supervisor

```


##

## Troubleshooting

If somethings going wrong, use `journalctl -f` to get your system logs. If you are not familiar with Linux and how you can fix issues, we recommend to use our Home Assistant OS.
