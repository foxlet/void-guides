Build Kodi PVR 17.6 (HDHomeRun) on Void Linux
=============================================

The Kodi PVR plugins are not included in Void Linux yet, but they are easy enough to build and install for the current stable version (17.6 Krypton).

# pvr.hdhomerun

## Build from Git

```
sudo xbps-install -Suyv base-devel
git clone --single-branch -b Krypton https://github.com/xbmc/xbmc.git
git clone --single-branch -b Krypton https://github.com/kodi-pvr/pvr.hdhomerun.git
cd pvr.hdhomerun && mkdir build && cd build
cmake -DADDONS_TO_BUILD=pvr.hdhomerun -DADDON_SRC_PREFIX=../.. -DCMAKE_BUILD_TYPE=Debug -DCMAKE_INSTALL_PREFIX=../../xbmc/addons -DPACKAGE_ZIP=1 ../../xbmc/project/cmake/addons
make
cp -r  ~/src/xbmc/addons/pvr.hdhomerun/ ~/.kodi/addons/
```

## Build from Archive (tar)

```
sudo xbps-install -Suyv base-devel
wget https://github.com/xbmc/xbmc/archive/17.6-Krypton.tar.gz && tar -xvf 17.6-Krypton.tar.gz
wget https://github.com/kodi-pvr/pvr.hdhomerun/archive/2.4.7-Krypton.tar.gz && tar -xvf 2.4.7-Krypton.tar.gz
cd pvr.hdhomerun-2.4.7-Krypton && mkdir build && cd build
cmake -DADDONS_TO_BUILD=pvr.hdhomerun -DADDON_SRC_PREFIX=../.. -DCMAKE_BUILD_TYPE=Debug -DCMAKE_INSTALL_PREFIX=../../xbmc-17.6-Krypton/addons -DPACKAGE_ZIP=1 ../../xbmc-17.6-Krypton/project/cmake/addons
make
cp -r  ~/src/xbmc-17.6-Krypton/addons/pvr.hdhomerun/ ~/.kodi/addons/
```
