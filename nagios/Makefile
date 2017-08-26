#
# Copyright (C) 2008-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=nagios
PKG_VERSION:=4.2.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/nagios
PKG_HASH:=83ee7eb00b77b829c98473ebeff810949114d0a89f4330fc25eeaf794bd5265c

include $(INCLUDE_DIR)/package.mk

define Package/nagios
  SECTION:=admin
  CATEGORY:=Administration
  DEPENDS:=+libpthread +perl +libltdl
  TITLE:=service and network monitoring program
  URL:=http://www.nagios.org/
endef

define Package/nagios/description
	service and network monitoring program
endef

EXTRA_CFLAGS += $(TARGET_CPPFLAGS)

CONFIGURE_VARS += \
	ac_cv_lib_gd_gdImagePng_1=no \
	ac_cv_lib_gd_gdImagePng_2=no \
	ac_cv_lib_gd_gdImagePng_3=no \
	ac_cv_lib_gd_gdImagePng_4=no

CONFIGURE_ARGS += \
	--with-nagios-user="root" \
	--with-nagios-group="root" \
	--sysconfdir="/etc/nagios" \
	--without-gd-lib \
	--without-gd-inc \
	CFLAGS="$(TARGET_CFLAGS) $(EXTRA_CFLAGS)"

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		DESTDIR="$(PKG_INSTALL_DIR)" \
		INSTALL_OPTS="" \
		STRIP=: \
		all install install-config
endef

define Package/nagios/install
	$(INSTALL_DIR)	$(1)/etc/nagios
	$(CP)	$(PKG_INSTALL_DIR)/etc/nagios/* $(1)/etc/nagios/
	$(INSTALL_DIR)	$(1)/usr/bin
	$(INSTALL_BIN)	$(PKG_INSTALL_DIR)/usr/bin/{nagios,nagiostats} $(1)/usr/bin/
	$(INSTALL_DIR)	$(1)/usr/sbin
	$(INSTALL_BIN)	$(PKG_INSTALL_DIR)/usr/sbin/* $(1)/usr/sbin/
	$(INSTALL_DIR)	$(1)/usr/share
	$(CP)	$(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
endef

define Package/nagios/conffiles
/etc/nagios/cgi.cfg
/etc/nagios/nagios.cfg
/etc/nagios/resource.cfg
/etc/nagios/objects/commands.cfg
/etc/nagios/objects/localhost.cfg
/etc/nagios/objects/switch.cfg
/etc/nagios/objects/timeperiods.cfg
/etc/nagios/objects/contacts.cfg
/etc/nagios/objects/printer.cfg
/etc/nagios/objects/templates.cfg
/etc/nagios/objects/windows.cfg
endef

$(eval $(call BuildPackage,nagios))
