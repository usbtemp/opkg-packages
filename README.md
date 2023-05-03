# opkg-package for utmp-cli

To add the package to OpenWrt Build System append
```
src-git usbtemp https://github.com/usbtemp/opkg-packages.git
```
to `feeds.conf`, or execute
```
echo "src-git usbtemp https://github.com/usbtemp/opkg-packages.git" >>feeds.conf
```
in buildroot (source) directory.

Then update feeds by running
```
./scripts/feeds update
./scripts/feeds install -a -p usbtemp
```

Finally, enable package `utmp-cli` (under Utilities) in `make menuconfig` (sufficient only as a module) and compile package as
```
make package/feeds/usbtemp/utmp-cli/compile
```
Openwrt package (ipk) is created in `bin/packages/__target_arch__/usbtemp/` directory.

Digitemp package is available in official OpenWrt package repository.