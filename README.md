To add packages to OpenWrt Build System append
```
src-git usbtemp https://github.com/usbtemp/opkg-packages.git
```
to `feeds.conf` (`feeds.conf.default`), or execute
```
echo "src-git usbtemp https://github.com/usbtemp/opkg-packages.git" >> feeds.conf
```
in buildroot (source) directory. Update feeds by running
```
./scripts/feeds update
./scripts/feeds install -a
```
Enable package `utmp-cli` (under Utilities) in `make menuconfig` (sufficient only as a module) and compile package as
```
make package/feeds/usbtemp/utmp-cli/compile
```
Digitemp package is also available in official OpenWrt package repository.