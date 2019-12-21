## Installing hass.io on Raspberry Pi 4b

Using [64-bit Ubuntu Server](https://ubuntu.com/download/raspberry-pi  ) as the Raspbian images are only 32-bit.  
Using the [manual instalation](https://www.home-assistant.io/hassio/installation/#alternative-install-on-a-generic-linux-host)
instead of the hassio image to make it easier to install other services on the RPi while still having access to the hassio addons.

### Update the OS  
`sudo apt update && sudo apt upgrade -y`

### Install docker via convenience script
Source: https://github.com/docker/docker-install

> **NOTE**: I had to hack this script to use the disco repo instead of a (currently) non-existent eoan repo.

```
curl -fsSL https://get.docker.com -o get-docker.sh
chmod u+x get-docker.sh
sudo ./get-docker.sh
```

### Install home assistant
Source: https://www.home-assistant.io/hassio/installation/#preparation

```
sudo apt install apparmor-utils apt-transport-https avahi-daemon ca-certificates curl dbus jq network-manager socat -y
sudo systemctl disable ModemManager
curl -sL "https://raw.githubusercontent.com/home-assistant/hassio-installer/master/hassio_install.sh" -o hassio-install.sh
chmod u+x hassio-install.sh
sudo ./hassio-install.sh -m raspberrypi4-64
```
