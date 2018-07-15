Build Wine on Void Linux
========================

Since the latest version of Wine available on the Void Linux repo is 32-bit only, here's some instructions for compiling the latest version of Wine on Void Linux. This assumes 3 folders exist, **wine** with the Wine source code, **wine64** for the compiled 64-bit Wine installation, and **wine32** for WoW64 support.

## Compile 64-bit-only Wine

Compiling 64-bit Wine is the easiest, but it will only run 64-bit Windows applications. Most likely this will not be very useful since most applications still have 32-bit components. However, it is required for a WoW (32 and 64-bit) Wine installation.

Install 64-bit compiler and development tools
```
sudo xbps-install -Su base-devel
```

Install Wine 64-bit dependencies
```
sudo xbps-install libX11-devel freetype-devel libjpeg-turbo-devel gnutls-devel dbus-devel libopenal-devel gstreamer-devel libxml2-devel libxslt-devel tiff-devel libldap-devel libXrender-devel libXrandr-devel libXfixes-devel libpulseaudio libOSMesa fontconfig-devel libmpg123 lcms2-devel libXinerama-devel libXcomposite-devel libXcursor-devel libXi-devel libsane glu-devel libgphoto2-devel opencl-headers pulseaudio-devel libpcap-devel
```

Compile Wine 64-bit
```
mkdir wine64
cd wine64
../wine/configure --enable-win64
make -j10
```

64-bit Wine is ready to use. You can optionally install it with `make install`, but you will want to add WoW64 support first.

## Compile WoW64 (32-bit support) for 64-bit Wine

You'll need to follow the Wine 64-bit instructions first.
After compiling 64-bit Wine...

Install 32-bit compiler
```
sudo xbps-install gcc-multilib
```

Install Wine 32-bit dependencies
```
sudo xbps-install libX11-devel-32bit freetype-devel-32bit libjpeg-turbo-devel-32bit gnutls-devel-32bit dbus-devel-32bit libopenal-devel-32bit gstreamer-devel-32bit libxml2-devel-32bit libxslt-devel-32bit tiff-devel-32bit libldap-devel-32bit libXrender-devel-32bit libXrandr-devel-32bit libXfixes-devel-32bit libpulseaudio-32bit libOSMesa-32bit fontconfig-devel-32bit libmpg123-32bit lcms2-devel-32bit libXinerama-devel-32bit libXcomposite-devel-32bit libXcursor-devel-32bit libXi-devel-32bit libsane-32bit glu-devel-32bit libgphoto2-devel-32bit opencl-headers pulseaudio-devel-32bit libpcap-devel-32bit libcups-32bit
```

Compile 32-bit Wine support libraries
```
mkdir wine32
cd wine32
PKG_CONFIG_PATH=/usr/lib32/pkgconfig ../wine/configure --with-wine64=../wine64
make -j10
```

WoW64 will be automatically added to the 64-bit Wine installation. To use wine, use the 64-bit installation.

To install wine, first install wine32 `cd wine32 && sudo make install`, then wine64 `cd wine64 && sudo make install`
