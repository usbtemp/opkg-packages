include $(TOPDIR)/rules.mk

PKG_NAME:=utmp-cli
PKG_VERSION:=1.064
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/usbtemp/utmp-cli.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=92b74d384b61089a10295adf13700c3cb176431a
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
