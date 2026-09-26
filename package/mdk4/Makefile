include $(TOPDIR)/rules.mk

PKG_NAME:=mdk4
PKG_VERSION:=4.2
PKG_RELEASE:=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/aircrack-ng/mdk4.git
PKG_SOURCE_VERSION:=4.2
PKG_MIRROR_HASH:=skip

PKG_LICENSE:=GPL-3.0-or-later
PKG_MAINTAINER:=Local OpenWrt Build

PKG_BUILD_DEPENDS:=libpcap libnl-tiny

include $(INCLUDE_DIR)/package.mk

define Package/mdk4
  SECTION:=net
  CATEGORY:=Network
  TITLE:=MDK4 wireless testing tool
  DEPENDS:=+libpcap +libnl-tiny
endef

define Package/mdk4/description
 MDK4 wireless testing and auditing tool.
 Built specifically for the target OpenWrt SDK.
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CC)" \
		AR="$(TARGET_AR)" \
		RANLIB="$(TARGET_RANLIB)" \
		CFLAGS="$(TARGET_CFLAGS) -fcommon -D LINKTYPE_ETHERNET=1 -D LINKTYPE_IEEE802_11=105 -D LINKTYPE_PRISM_HEADER=119 -D LINKTYPE_RADIOTAP_HDR=127 -D LINKTYPE_PPI_HDR=192 -D TCPDUMP_MAGIC=0xa1b2c3d4" \
		CPPFLAGS="$(TARGET_CPPFLAGS) -D LINKTYPE_ETHERNET=1 -D LINKTYPE_IEEE802_11=105 -D LINKTYPE_PRISM_HEADER=119 -D LINKTYPE_RADIOTAP_HDR=127 -D LINKTYPE_PPI_HDR=192 -D TCPDUMP_MAGIC=0xa1b2c3d4" \
		LDFLAGS="$(TARGET_LDFLAGS)"
endef

define Package/mdk4/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mdk4 $(1)/usr/sbin/mdk4
endef

$(eval $(call BuildPackage,mdk4))
