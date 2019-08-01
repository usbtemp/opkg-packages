To add packages append
```
src-git usbtemp https://github.com/usbtemp/opkg-packages.git
```
to `feeds.conf` (`feeds.conf.default`), or execute
```
echo "src-git usbtemp https://github.com/usbtemp/opkg-packages.git" >> feeds.conf
```
in buildroot (source) directory and update feeds by running
```
./scripts/feeds update
./scripts/feeds install -a
```
Then enable packages in `make menuconfig` (sufficient only as a module) and compile package as
```
make package/feeds/usbtemp/utmp-cli/compile
```
Digitemp package is also available in official OpenWRT package repository.
