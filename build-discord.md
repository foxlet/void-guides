Build Discord on Void Linux
===========================

Installing the Discord Desktop app is fairly straightforward. It is included in the XBPS source code repos, but not as a binary due to licensing restrictions. Users are free, however, to build and install it locally.

```
sudo xbps-install -S git
git clone https://github.com/void-linux/void-packages.git
cd void-packages
./xbps-src binary-bootstrap
echo XBPS_ALLOW_RESTRICTED=yes >> etc/conf
./xbps-src pkg discord
sudo xbps-install --repository=$PWD/hostdir/binpkgs/nonfree discord
```
