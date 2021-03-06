#
# Copyright (C) 2006-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=aircrack-ng
PKG_VERSION:=1.2-rc4
PKG_RELEASE:=1
PKG_LICENSE:=GPLv2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/aircrack-ng/aircrack-ng.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=177ee2c040e93c03a1d8893c7de5bfe307435c6a
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

PKG_MAINTAINER:=Andreas Nilsen <adde88@gmail.com>

include $(INCLUDE_DIR)/package.mk

define Package/aircrack-ng
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpcap +libpthread +libopenssl +libnl +wireless-tools +ethtool +libstdcpp +libsqlite3
  TITLE:=WLAN tools for breaking 802.11 WEP/WPA keys
  URL:=http://www.aircrack-ng.org/
  MAINTAINER:=Rick Farina <zerochaos@gentoo.org>
  SUBMENU:=wireless
endef

define Package/aircrack-ng/description
  WLAN tools for breaking 802.11 WEP/WPA keys
endef

MAKE_FLAGS += prefix=/usr \
	libnl=true \
	sqlite=true \
	experimental=true \
	stackprotector=false \
	OSNAME=Linux 
	

CFLAGS="$(TARGET_CFLAGS) -Wall -Iinclude/ $(TARGET_CPPFLAGS) -D_REVISION=0" \

define Package/aircrack-ng/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/* $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,aircrack-ng))
