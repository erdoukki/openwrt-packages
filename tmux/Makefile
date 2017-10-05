#
# Copyright (C) 2009-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=tmux
PKG_VERSION:=2.6
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/tmux/tmux/releases/download/$(PKG_VERSION)
PKG_HASH:=b17cd170a94d7b58c0698752e1f4f263ab6dc47425230df7e53a6435cc7cd7e8
PKG_MAINTAINER:=hashashin <gentoo.power@gmail.com>

PKG_LICENSE:=ISC
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/tmux
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Terminal
  TITLE:=Terminal multiplexer
  DEPENDS:=+libncurses +libevent2 +libpthread +librt
  URL:=http://tmux.sourceforge.net/
endef

define Package/tmux/description
  tmux is a modern, BSD-licensed alternative to GNU screen.
endef

MAKE_FLAGS += \
	PREFIX="/usr" \
	PLATFORM="linux"

define Package/tmux/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/tmux $(1)/usr/bin/
endef

$(eval $(call BuildPackage,tmux))
