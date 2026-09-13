include $(TOPDIR)/rules.mk

PKG_NAME:=sane-airscan
PKG_VERSION:=0.99.38
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/alexpevzner/sane-airscan/tar.gz/$(PKG_VERSION)?
PKG_HASH:=1e5b3b8373141caa37bf42fe74ae1950de3ff15c84966d8a415485d334ba5507

PKG_MAINTAINER:=Rosa Hase <github@smnx.addy.io>
PKG_LICENSE:=GPL-3.0-only
PKG_LICENSE_FILES:=LICENSE

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/meson.mk

define Package/sane-airscan
  TITLE:=Scanner Access Now Easy - universal driver for eSCL (Apple AirScan) and WSD
  URL:=https://github.com/alexpevzner/sane-airscan
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libsane +libjpeg +libpng +libtiff +libxml2 +libgnutls +libavahi-client
endef

define Package/sane-airscan/description
  Similar to how most modern network printers support "driverless" printing, using the universal vendor-neutral printing protocol, many modern network scanners and MFPs support "driverless" scanning.
  Driverless scanning comes in two flavors: Apple AirScan or AirPrint scanning (official protocol name is eSCL) and Microsoft WSD, or WS-Scan (term WSD means "Web Services for Devices)
endef

define Package/sane-airscan/conffiles
/etc/sane.d/airscan.conf
endef

define Package/sane-airscan/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/airscan-discover $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/lib/sane
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/sane/libsane-airscan.so.* $(1)/usr/lib/sane/
	$(INSTALL_DIR) $(1)/etc/sane.d/dll.d
	$(INSTALL_CONF) $(PKG_INSTALL_DIR)/etc/sane.d/airscan.conf $(1)/etc/sane.d/
endef

$(eval $(call BuildPackage,sane-airscan))
