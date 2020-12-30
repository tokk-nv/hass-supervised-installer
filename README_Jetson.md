# Setting up Home Assistant Supervised on Jetson 

> This doc shows an experimental method to install Home Assistance on Jetson Nano Developoer Kit

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
sudo bash ./installer.sh --machine raspberrypi4
```

### Install process

> [info] Do you want to proceed with overwriting the /etc/network/interfaces file? [N/y]

`N`

If it goes well, you should see this output at the end.

```
[info] Home Assistant supervised is now installed
[info] First setup will take some time, when it's ready you can reach it here:
[info] http://192.168.xxx.xxx:8123
[info]
```

### Post-install verification

```bash
$ sudo docker ps
CONTAINER ID        IMAGE                                                COMMAND                  CREATED             STATUS              PORTS                  NAMES
30fe8f7fb3ca        homeassistant/raspberrypi4-homeassistant:2020.12.1   "/init"                  19 hours ago        Up 19 hours                                homeassistant
815ea93a758b        homeassistant/aarch64-hassio-multicast:3             "/init"                  19 hours ago        Up 19 hours                                hassio_multicast
3da3ea1e1c32        homeassistant/aarch64-hassio-observer:2020.10.1      "/init"                  19 hours ago        Up 19 hours         0.0.0.0:4357->80/tcp   hassio_observer
451dd522fdce        homeassistant/aarch64-hassio-cli:2020.11.1           "/init /bin/bash -c …"   19 hours ago        Up 19 hours                                hassio_cli
f89df71acc61        homeassistant/aarch64-hassio-audio:17                "/init"                  19 hours ago        Up 19 hours                                hassio_audio
ad995bfc2c14        homeassistant/aarch64-hassio-dns:2020.11.0           "/init"                  19 hours ago        Up 19 hours                                hassio_dns
98e046b95352        homeassistant/aarch64-hassio-supervisor              "/init"                  19 hours ago        Up 19 hours                                hassio_supervisor

```


##

## Troubleshooting

If somethings going wrong, use `journalctl -f` to get your system logs. If you are not familiar with Linux and how you can fix issues, we recommend to use our Home Assistant OS.

