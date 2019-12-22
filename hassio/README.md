## Installing hass.io on Raspberry Pi 4b

Using [64-bit Ubuntu Server](https://ubuntu.com/download/raspberry-pi  ) as the Raspbian images are only 32-bit.  
Using the [manual instalation](https://www.home-assistant.io/hassio/installation/#alternative-install-on-a-generic-linux-host)
instead of the hassio image to make it easier to install other services on the RPi while still having access to the hassio addons.

### Update the OS  
`sudo apt update && sudo apt upgrade -y`

### Install docker via convenience script
Source: https://docs.docker.com/install/linux/docker-ce/ubuntu/

#### Install packages to allow apt to use a repository over HTTPS:  
`sudo apt install apt-transport-https ca-certificates curl gnupg-agent -y`

#### Add Docker’s official GPG key:  
`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

#### Add the stable Docker repository:
> **NOTE**: As of writing Docker is not available for Ubuntu Eoan. Use the previous release by changing `$(lsb_release -cs)` to `disco` in the command below.

`sudo sh -c "echo \"deb [arch=arm64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable\" > /etc/apt/sources.list.d/docker.list"`

#### Update the apt package index:  
`sudo apt update`

#### Install docker-ce:  
`sudo apt install docker-ce -y`

#### Check docker works:  
`sudo docker run hello-world`

#### Add the user to the docker group:
> **NOTE**: This requires logging out and back in again to take effect.

`sudo usermod -aG docker $USER`

### Install home assistant
Source: https://www.home-assistant.io/hassio/installation/#preparation

```
sudo apt install apparmor-utils avahi-daemon dbus jq network-manager socat -y
sudo systemctl disable ModemManager
curl -sL "https://raw.githubusercontent.com/home-assistant/hassio-installer/master/hassio_install.sh" | sudo bash -s -- -m raspberrypi4-64
```
