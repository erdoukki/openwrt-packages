#
# Copyright (C) 2006-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=whois
PKG_VERSION:=5.2.18
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)/$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)_$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=http://ftp.debian.org/debian/pool/main/w/whois
PKG_HASH:=c35d0d26aff37107c244a8ad54fd42e497ec0b90f76309e9beb7078b827c97d5
PKG_CAT:=xzcat

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/whois
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libidn
  TITLE:=WHOIS commandline utility
  URL:=http://ftp.debian.org/debian/pool/main/w/whois
  MAINTAINER:=hashashin <gentoo.power@gmail.com>
endef

define Package/whois/description
  Utility to display information from WHOIS servers
endef

define Package/whois/conffiles
/etc/whois.conf
endef

define Package/whois/postinst
#!/bin/sh
grep -q '^whois[[:space:]]*43/tcp[[:space:]]*nicname' $${IPKG_INSTROOT}/etc/services 2>/dev/null
if [ $$? -ne 0 ]; then
	echo "whois           43/tcp          nicname" >> $${IPKG_INSTROOT}/etc/services
fi
endef

MAKE_FLAGS += \
	prefix=$(PKG_BUILD_DIR)

define Package/whois/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/whois $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/whois.conf $(1)/etc/whois.conf
endef

$(eval $(call BuildPackage,whois))

