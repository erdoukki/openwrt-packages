#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lynx
PKG_VERSION:=2.8.9rel.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://invisible-mirror.net/archives/lynx/tarballs/
PKG_HASH:=899e3531cc9446e73dc5ebe63ea5f062

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/lynx
    TITLE:=lynx
    SECTION:=network
    CATEGORY:=Network
    DEPENDS:=+libncurses +zlib +libopenssl +libidn +libncursesw
    URL:=http://lynx.isc.org
endef

define Package/lynx/description
    text console browser
endef

CONFIGURE_ARGS += --with-zlib --with-ssl \
		  --with-screen=ncursesw \
		  --enable-widec \
		  --enable-locale-charset \
		  --disable-color-style \
		  --enable-charset-choice \
		  --enable-cjk \
		  --enable-japanese-utf8 \
		  --enable-nsl-fork \
		  --enable-ipv6

CONFIGURE_VARS += cf_cv_ncurses_header="ncursesw/curses.h" \
		  ac_cv_path_NCURSES_CONFIG=""

define Package/lynx/install
	$(INSTALL_DIR) $(1)/usr/bin $(1)/etc
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lynx $(1)/usr/bin/
	$(INSTALL_DATA) ./files/etc/lynx.cfg $(1)/etc/
	$(INSTALL_DATA) ./files/etc/lynx.lss $(1)/etc/
endef

$(eval $(call BuildPackage,lynx))
