Set up iOS support in Void Linux
==================================

At a basic level, the `usbmuxd` daemon is needed to interact with iOS devices.

```
sudo xbps-install -S usbmuxd
sudo ln -s /etc/sv/usbmuxd /var/service/
```

For management utilities, idevicetools are also useful.

```
sudo xbps-install -S libimobiledevice
```
