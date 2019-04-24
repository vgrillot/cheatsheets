HOW TO LINUX, rpi edition !
===================================

https://www.raspberrypi.org/documentation/


Raspbian setup
==============
Default user: pi:rasbperry

Enable SSH:
Touch a file "ssh" on boot partition
https://www.raspberrypi.org/documentation/remote-access/ssh/


Update all packages
``sudo apt-get update``

Install PIP
``sudo apt-get install python3-pip``

Install GIT
``sudo apt-get install git``





Kivy setup
==========
_I'm using Kivy distribution for mission-pinball framework._

Default user : sysop:posys

http://kivypie.mitako.eu/kivy-faq.html


Install
-------
Update firmware:
``sudo rpi-update``

Extend SD card:
``sudo pipaos-config --expand-rootfs``

Kivy 1.0 wifi bug:
------------------
Need to edit file manually to set wifi:
https://groups.google.com/forum/#!topic/kivypie/K23t5fr6oyE
``sudo vi /boot/interfaces``


Update wifi settings:
``sudo pipaos-setwifi 42 passphrase``

Fixed ip addr for wifi:
``sudo vi /etc/network/interfaces``
````
#iface wlan0 inet dhcp
iface wlan0 inet static
  wpa-ssid: 42
  wpa-psk: TheAnswer
address 192.168.0.127
netmask 255.255.255.0
network 192.160.0.0
gateway 192.168.0.255
````

Show config:
``sudo ifconfig wlan0``

Restart wifi:
``sudo ifdown wlan0 && sudo ifup wlan0``


Display ip at start:
``hostname -I | figlet``

install figlet:
``sudo apt-get install figlet``



System
======
Startup script
--------------
https://www.baldengineer.com/raspberry-pi-startup-script-tutorial.html




Sound:
======

MPF sound issue:
----------------
https://groups.google.com/forum/#!topic/mpf-users/oPSGKiTUwJc
http://www.framboise314.fr/ca-va-faire-du-bruit-chez-les-framboise314-comment-configurer-le-son-sur-le-raspberry-pi/

Analog sound:
-------------
https://mike632t.wordpress.com/2013/09/09/enable-analogue-audio-output-raspberry-pi/

Alsa driver:
------------
https://raspberrypi.stackexchange.com/questions/44/why-is-my-audio-sound-output-not-working


PulseAudio:
-----------
https://raspberrypi.stackexchange.com/questions/639/how-to-get-pulseaudio-running

I have got it working on my Raspberry Pi using the ALSA sink, with procedure as follows:

To install the necessary files:

````
sudo apt-get install pulseaudio pulseaudio-module-zeroconf alsa-utils avahi-daemon
````

To enable ALSA:
````
sudo modprobe snd-bcm2835                      # load module for single boot
echo "snd-bcm2835" | sudo tee -a /etc/modules  # load module for persistance
````

To set up networking:
``sudo nano /etc/pulse/default.pa`` and uncomment the lines:
````
load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1;192.168.0.0/16
load-module module-zeroconf-publish
````
To start the pulseaudio server, use ``pulseaudio -D``
You should be able to test that it works by playing a wav file with paplay (sudo apt-get install pulseaudio-utils), and also over the network by selecting the sink in your system's sound control panel.

You might be also be able to set up in system-wide mode with ``sudo pulseaudio --system`` 



