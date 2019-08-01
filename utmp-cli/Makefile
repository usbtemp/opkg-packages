include $(TOPDIR)/rules.mk

PKG_NAME:=utmp-cli
PKG_VERSION:=2019-08-01
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/usbtemp/utmp-cli.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=02b1d9542467937207c24efb96fbaee36a5b44d3
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	CATEGORY:=Utilities
	TITLE:=Read temperature from USB thermometer
	DEPENDS:=+kmod-usb-serial +kmod-usb-serial-pl2303
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/utmp-cli $(1)/usr/bin/utmp-cli
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
