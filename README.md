## Raspberry Pi TightVNC Server Autostart Script

An easy script to ensure the TightVNC Server autostarts when the Raspberry Pi boots up.

Tested on a few Raspberry Pi Model B+s (Wheezy) and a Raspberry Pi 2 (Jessie) too.

### Why?
It ensures I have reliable headless access to my Raspberry Pis, even after reboots.

### Is it useful?
Yes, as it allows me to easily and reliably access my Raspberry Pis, regardless of where they are located.

### Installation
Ensure the Raspberry Pi system is up to date:
```
sudo apt-get update
sudo apt-get upgrade
```
Install the TightVNC server software:
```
sudo apt-get install tightvncserver
```
Run TightVNC and set a password:
```
/usr/bin/tightvncserver
```
Test your Raspberry Pi access with a VNC client:
```
VNC://Raspberry.Pi.IP.Address:1
```
Put the TightVNC Server autostart script here:
```
/etc/init.d/tightvncserver
```
Sort the script ownership and permissions:
```
sudo chown root:root /etc/init.d/tightvncserver
sudo chmod 755 /etc/init.d/tightvncserver
```
Add the script to the default runlevels:
```
sudo update-rc.d tightvncserver defaults
```
Reboot to make sure it's all works:
```
sudo shutdown -r now
```
### Missing and ToDo
Nothing... unless something is spotted.

### Credits
Most of the Internet for help & inspiration.

### License
Public domain - do what you like.
---

I used crontab instead, which worked fine for me.

 sudo crontab -e
Select editor for yourself i used nano editor which i felt easy myself.

 @reboot su - pi -c '/usr/bin/tightvncserver :1'
or if you use VNC server instead of tightvncserver.

 @reboot su - pi -c '/usr/bin/vncserver :1'
Explanation of the command: "su" is a user to select, "pi" is a name of user; you may have other users, "c" defines as command followed by in single quotations.

TIPS:

My suggestions is that before you reboot your pi please run the rebootcode

su - pi -c '/usr/bin/vncserver :1'
So this will verify us if there is a display available for that particular user, if not it will ask you to submit password for your display. Just give some password and remember that will be your VNC viewer password. And then reboot your pi. Open your vncviewer/tightvncviewer from your computer type "IP-RASPBERRYpi:1" then password. If everything goes well you can now access your pi in GUI with VNCVIEWER. Cheers..
