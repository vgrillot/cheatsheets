HOW TO LINUX, general edition
=============================


System
======
Startup script
--------------
https://www.baldengineer.com/raspberry-pi-startup-script-tutorial.html
https://www.raspberrypi.org/documentation/linux/usage/systemd.md



Admin
=====

switch to admin:
````
sudo -i
sudo su -
````

edit or grants:
http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo


visudo


Users:
======
``/etc/passwd``

create a user:
``sudo adduser pinball``

allow sudo:
``sudo adduser pinball sudo``





Tmp:
====

increase tmp size:
edit ``/etc/fstab``


Upgrade:
========

pip
---

``sudo pip3 install --upgrade pip``

python
------
install python 3.6:
https://tutorials.technology/tutorials/67-Installing-python-36-on-raspberrypi.html
