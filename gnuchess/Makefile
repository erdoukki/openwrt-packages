# Copyright (C) 2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gnuchess
PKG_VERSION:=6.2.5
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://ftp.gnu.org/pub/gnu/chess
PKG_HASH:=9a99e963355706cab32099d140b698eda9de164ebce40a5420b1b9772dd04802

include $(INCLUDE_DIR)/package.mk

define Package/gnuchess
  TITLE:=Chess GNU from FSF
  SECTION:=games
  CATEGORY:=Games
  URL:=http://www.gnu.org/software/chess/chess.html
  DEPENDS:=+libncurses +libpthread +libreadline +libstdcpp
endef
PKG_BUILD_DIR:=$(BUILD_DIR)/gnuchess-$(PKG_VERSION)

define Package/gnuchess/description
  GNU Chess lets most modern computers play a full game of chess. It has a plain terminal interface but supports visual interfaces such as xboard and eboard
endef
 
define Build/Configure
      $(call Build/Configure/Default)

endef 
define Package/gnuchess/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/gnuchess $(1)/usr/bin/
	mkdir -p $(1)/usr/share/gnuchess
	$(INSTALL_DATA) ./files/gnuchess.ini $(1)/usr/share/gnuchess/
endef 

$(eval $(call BuildPackage,gnuchess))
