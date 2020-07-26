# Dell Latitude D420 - debian/testing + WiFi (b43)

debian/testing + Ubuntu BCM43xx drivers

https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx

## Wi-Fi

Determine driver (BCM4311; 14e4:4311):

```bash
lcpci -nn -d 14e4:
```

Use b43 drivers (not STA). Download on host; see
https://packages.debian.org/bullseye/b43-fwcutter

```bash
wget http://http.us.debian.org/debian/pool/contrib/b/b43-fwcutter/b43-fwcutter_019-6_i386.deb
wget http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
```

Copy to removeable media and install on target:

```bash
sudo dpkg -i b43-fwcutter_019-6_i386.deb
tar xfvj broadcom-wl-5.100.138.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o
sudo reboot
```

## /etc/apt/sources.list

Edit to contain:

```
deb http://deb.debian.org/debian testing main contrib non-free
deb http://security.debian.org/debian-security testing-security main contrib
```

Update:

```bash
sudo apt update
sudo apt dist-upgrade
```
