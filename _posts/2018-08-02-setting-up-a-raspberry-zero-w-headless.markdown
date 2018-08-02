---
layout: post
title:  "Setting up a Raspberry Pi Zero W headless"
ref: raspberryheadless
date:   2018-08-02 18:48:44 +0100
categories: raspberry server
lang: en
---
You bought a raspberry Pi Zero W and forgot to buy any additional cables and adapters? Now you can't wait to start working with your freshly bought toy. I'm bringing good news, there is a way to get things working.

## What you need to have:
- Raspberry Pi Zero W
- 4 GB Micro SD Card (I recommend 16 GB)
- Micro USB Data Cable

## What you need to know:
- nothing

# Install an Operating System to the Raspberry PI Zero
1. Download the latest Version of [Rasbian Lite](https://www.raspberrypi.org/downloads/raspbian/) (if you want a UI choose a version with PIXEL)
2. Unzip Rasbian
3. Install [Rufus](https://rufus.akeo.ie/)
4. Write the Rasbian Image to the SD via Rufus
5. Eject the SD Card
6. Put the SD in the Raspberry PI Zero
7. Plug the Raspberry PI Zero
If the flickers for a few seconds and stays glowing after it, you have done everything until here. If not try another USB Cable or another Micro SD Card.

# Enable Wifi
1. Put the SD Card back in your Computer
2. Create a file named: {% highlight bash %}wpa_supplicant.conf{% endhighlight %}
3. Edit the File and change to 
{% highlight bash %}
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=GER

network={
  ssid="SSID"
  psk="PASSWORD"
  key_mgmt=WPA-PSK
  scan_ssid=1
}
{% endhighlight %}
4. Change SSID to the Name of your Network, PASSWORD to the password of your Network and country to your country code. 
Germany = GER
USA = US

# Set up a SSH Connection
1. Create a date file named ssh
2. Plug the SD again in your Raspberry PI Zero
3. Search your Router for the Raspberry PI Zero
4. Select "Fix IP"

## On Windows
5. Download the Ubuntu App
6. Start the Ubuntu Shell
7. type ssh pi@raspberrypi
8. The password is raspberry
9. Congratulations you have made it!

## On Linux/Mac
5. Start the Terminal
6. type ssh pi@raspberrypi
7. The password is raspberry
8. Congratulations you have made it!