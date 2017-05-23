# Home Automation

A few years ago I started a project to automate my house and have finally settled in a solution which works well. If you're just getting started with home automation I recommend you try out something like [SmartThings](https://www.smartthings.com/) or [Wink](https://www.wink.com/) as they provides the complete package. If you're willing to dig a bit deeper and roll up your sleeves, read on.


## Principles 

Before I get started I want to call out a few concepts I used to shape my setup:

1. **Keep communication local to the network.** While SmartThings and similar hubs are easy to set up they typically do so by routing their traffic through the open internet to their servers. This can cause a lag in responsiveness, but more importantly, it means they are getting your data and can understand your home usage patterns. No thanks.

2. **Devices should look and behave like a normal device.** More of a personal preference, but I want my light switches and other devices to look and behave like normal light switches. I shouldn't be required to use my phone to turn something on and vistors shouldn't notice that anything is out of the ordinary.


## Setup 

![Network Diagram](https://jeffharrell.github.io/home-assistant-config/HomeNetworkDiagram.svg)

`1` – My home network is controlled by the open source application [Home Assistant](https://home-assistant.io/). Other options were explored like SmartThings, HABmin, and Domoticz, but this is the one which worked for me. It has a vibrant open source community, frequent updates, is highly customizable, and a good looking design for it's apps.

`2` – Home Assistant is running in a Docker container on a [Synology NAS DS716+II](https://www.amazon.com/Synology-DS716-II-Storage-DiskStation/dp/B01EMPW5Z6/). The NAS is not externally accessible from the internet and if you wish to connect to the NAS remotely you need to VPN into the local network. Internal to the local network all traffic is served over SSL.

`3`, `6` – The majority of my home network communicates over [Z-Wave](https://en.wikipedia.org/wiki/Z-Wave) through a [Aoetec Z-Stick](https://www.amazon.com/Aeotec-Aeon-Labs-ZW090-Stick/dp/B00X0AWA6E/) plugged into the Synology NAS. Z-Wave devices are low power devices which help me stick to the principle of communication on my local network. Plus, they tend to look and feel like normal devices so that helps.

- **Light Switches:** All light switches are wired up with [GE Smart Dimmer Z-Wave Switches](https://www.amazon.com/gp/product/B006LQFHN2/). The dimmer switches are a little more flexible than normal switches and can be customized through the Z-Wave parameters to either not dim or dim slower/faster.

- **Garage Door Sensors:** The door sensors are using [Ecolink Z-Wave Sensors](https://www.amazon.com/Ecolink-Intelligent-Technology-Operated-DWZWAVE2-ECO/dp/B00HPIYJWU/) which are your basic contact sensor.

- **Doorbell:** This was a fun one. I learned about dry contact sensors and ended up using a [Aoetec Dry Contact Sensor](https://www.amazon.com/gp/product/B0155HSUUY/) and magnetic switch connected to my existing doorbell to trigger a Z-Wave event when it was rung.


`4`, `5` – The remainder of the devices communicate over some form of HTTP/TCP. 

- **Media Center:** [Logitech Harmony Hub](https://www.amazon.com/Logitech-Harmony-Companion-Control-Entertainment/dp/B00N3RFC4G/)

- **Thermostat:** [Ecobee 3 Smart Thermostat](https://www.amazon.com/Ecobee3-Thermostat-Sensor-Generation-Amazon/dp/B00ZIRV39M/)

- **Voice Input:** [Amazon Echo Dot](https://www.amazon.com/All-New-Echo-Dot-2nd-Generation/dp/B01DFKC2SO/)
