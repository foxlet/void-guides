sudo xbps-install -S git
git clone https://github.com/void-linux/void-packages.git
cd void-packages
./xbps-src binary-bootstrap
echo XBPS_ALLOW_RESTRICTED=yes >> etc/conf
./xbps-src pkg discord
sudo xbps-install --repository=$PWD/hostdir/binpkgs/nonfree discord
