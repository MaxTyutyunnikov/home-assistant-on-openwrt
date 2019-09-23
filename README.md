# Script to install Home Assistant on OpenWRT
Home Assistant is an open source home automation platform. It is able to track and control thousands of smart devices and offer a platform for automating control. Details on https://github.com/home-assistant/home-assistant.  
Home Assistant supports only Windows, Linux, Mac and Raspberry offically. While this project is to install the Home Assistant on OpenWRT OS. So that you can run a Home Assistant on a router without having to run a 24-hours PC or Raspberry.   

**Note that OpenWRT is not an officially supported platform by Home Assistant and so not all integrations (e.g. Zigbee binaries) will work in this system.** 

## Hardware Requirements

A complete installation of Home Assistant will take nearly 350 MB Flash and 130 MB RAM. More components require more storage.  
Recommend device is GL-S1300. It has a 8 GB emmc, 512 MB RAM and a Quad-core CPU. It is enough for running Home Assistant and its routing function is also completely unaffected.  

## Software Requirements

Firmware version 3.023 for GL-S1300 or above.

## Install using our scripts

We recommend strongly that using our `gl-homeassistant.ipk` to install the Home Assistant. It provides an one-click installation script and has add Home Assistant into the system boot program.  

You can install "gl-homeassistant" easily through the web. Just search "gl-homeassistant" in the "plug-ins" and click "install".
Or you can manually install it in the SSH terminal typing this:

```bash
opkg update
opkg install gl-homeassistant
```

After finished installing gl-homeassistant. You can using command in the SSH terminal to start the installation of Home Assistant.

```bash
hass-install
```
Wait for the installation finished. Usually it takes 20~30 minutes.

## Install Manually

If you didn't install gl-homeassistant. There is no command named "hass-install". You have to clone this project and excute it manually.

### Clone this project

Open the OpenWRT interface through SSH. Using putty or xshell or some other tools.  
And then get into the root path and clone this project.

```bash
cd /root/
git clone https://github.com/gl-inet/home-assistant-on-openwrt.git
```

Note that maybe you'd install the git, use command like this:

```bash
opkg install git git-http
```

### Start installation

Get into the project folder and start the installation. Make sure your device has connected to the Internet.

```bash
cd home-assistant-on-openwrt
./install.sh 
```

It will take 20~30 minutes. After finished, it will print "HomeAssistant installation finished. Use command "hass -c /data/.homeassistant" to start the HA."

## Start Home Assistant for The First Time

After installation finished, use command `hass -c /data/.homeassistant` to start.  

Note that firstly start will download and install some Python modules. Make sure the network is connected while first starting. It will take about 20 minutes. If it stuck or print some error messages, don't worry, interupt it and retry `hass -c /data/.homeassistant` usually works.  

It has fully started when print messages like:

```bash
Starting Home Assistant
Timer:starting
```

## Enjoy Home Assistant on The Router

Connect to the S1300 through LAN ports or Wifi using your PC or phone. Visit the address `192.168.8.1:8123` , that's the web page for Home Assistant.  

Now you can link your smart devices together with Home Assistant.  

Questions and discussion about HA on https://community.home-assistant.io/
