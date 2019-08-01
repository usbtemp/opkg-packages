include $(TOPDIR)/rules.mk

PKG_NAME:=digitemp
PKG_VERSION:=3.7.2
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/bcl/digitemp.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=a162e63aad35358aab325388f3d5e88121606419
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_LICENSE:=GPL-2.0+

include $(INCLUDE_DIR)/package.mk

define Package/digitemp/Default
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=DigiTemp is a simple to use program for reading values from 1-wire devices.
  URL:=http://www.digitemp.com
endef

define Package/digitemp/Default/description
	DigiTemp is a simple to use program for reading values from 1-wire devices.
	Its main use is for reading temperature sensors, but it also reads counters,
	and understands the 1-wire hubs with devices on different branches of the network.
endef

define Package/digitemp
$(call Package/digitemp/Default)
  TITLE += (serial version)
endef

define Package/digitemp/description
$(call Package/digitemp/Default/description)
	This package is built without USB support.
endef

define Package/digitemp-usb
$(call Package/digitemp/Default)
  TITLE += (USB version)
  DEPENDS += +libusb-compat
endef

define Package/digitemp-usb/description
$(call Package/digitemp/Default/description)
	This package is built with USB support.
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		$(TARGET_CONFIGURE_OPTS) \
		CFLAGS="$(TARGET_CFLAGS) -DLINUX $(TARGET_CPPFLAGS) \
			-I./src -I./userial" \
		LIBS="$(TARGET_LDFLAGS)" \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		ds9097 ds9097u
	$(MAKE) -C $(PKG_BUILD_DIR) \
		$(TARGET_CONFIGURE_OPTS) \
		CFLAGS="$(TARGET_CFLAGS) -DLINUX $(TARGET_CPPFLAGS) \
			-I./src -I./userial -DOWUSB" \
		LIBS="$(TARGET_LDFLAGS) -lusb -lm -DOWUSB" \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		clean ds2490
endef

define Package/digitemp/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(CP) $(PKG_BUILD_DIR)/digitemp_{DS9097,DS9097U} $(1)/usr/bin/
endef

define Package/digitemp-usb/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(CP) $(PKG_BUILD_DIR)/digitemp_DS2490 $(1)/usr/bin/
endef

$(eval $(call BuildPackage,digitemp))
$(eval $(call BuildPackage,digitemp-usb))
