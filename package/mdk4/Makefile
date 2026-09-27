include $(TOPDIR)/rules.mk

PKG_NAME:=mdk4
PKG_VERSION:=4.2-dev
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/mdk4-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/aircrack-ng/mdk4.git
PKG_SOURCE_VERSION:=36ca143a2e6c0b75b5ec60143b0c5eddd3d2970c
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_MAINTAINER:=OpenWrt MDK4 package

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/mdk4
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Wireless
  TITLE:=MDK4 wireless testing tool
  URL:=https://github.com/aircrack-ng/mdk4
  DEPENDS:=+libpthread +libnl +libpcap
endef

define Package/mdk4/description
 MDK4 wireless testing and auditing tool.
 Developer version 4.2-dev.
endef

MAKE_FLAGS += \
	$(TARGET_CONFIGURE_OPTS)

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/src \
		$(TARGET_CONFIGURE_OPTS)
endef

define Package/mdk4/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mdk4 $(1)/usr/sbin/mdk4
endef

$(eval $(call BuildPackage,mdk4))
