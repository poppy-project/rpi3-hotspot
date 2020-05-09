# rpi3-hotspot

Turns a Raspberry Pi 3/4 into a configurable access point.

## How this works

An access point is created if `/boot/hotspot.txt` file is present. If there is no such file, no access point will be set up and the `/etc/wpa_supplicant/wpa_supplicant.conf` will be used.

Defaults are `ssid=Rpi Access Point (%hostname%)` and `passphrase=rpi_ap_pass` but can be changed by tweaking the `/boot/hotspot.txt` file. One or both parameters can be modified.  
See `boot/hotspot.txt.example` for a documented example.

The Raspberry Pi IP address will be `10.99.99.1`.

```
# /boot/hotspot.txt
ssid=Rodrigo The Robot
passphrase=your_secret_passphrase
```

## Installation

1. Clone this repo or download the archive.
2. `cd` into the directory
3. Uninstall previously installed version
4. `sudo ./install.sh`
5. Profit.

## Uninstalling previous version

```bash
sudo systemctl stop rpi-access-point
sudo systemctl disable rpi-access-point
sudo rm /etc/systemd/system/rpi-access-point.service /usr/bin/rpi-access-point
sudo systemctl daemon-reload
```
