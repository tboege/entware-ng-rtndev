#
# Copyright (C) 2011-2018 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# Abandoned in 2010

include $(TOPDIR)/rules.mk

PKG_NAME:=python-cheetah
PKG_VERSION:=2.4.4
PKG_RELEASE:=2

PKG_SOURCE:=Cheetah-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://pypi.python.org/packages/source/C/Cheetah
PKG_MD5SUM:=53917116e731afbc8c8a43c37e6ddba
PKG_BUILD_DEPENDS:=python
PKG_BUILD_DIR:=$(BUILD_DIR)/Cheetah-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-cheetah
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	DEPENDS:=+python-setuptools
	TITLE:=Python-powered template engine
	URL:=http://www.cheetahtemplate.org/
	MAINTAINER:=Entware team, http://entware.net
endef

define Package/python-cheetah/description
 Cheetah is an open source template engine and code generation tool, written in
 Python. It can be used standalone or combined with other tools and frameworks.
 Web development is its principle use, but Cheetah is very flexible and is also
 being used to generate C++ game code, Java, sql, form emails and even Python
 code.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install \
	    --prefix=/opt \
	    --root=$(PKG_INSTALL_DIR) \
	)
endef

define Package/python-cheetah/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/opt/bin/cheetah{,-analyze,-compile} \
		$(1)/opt/bin
	 $(SED) 's,/usr/bin/env python,/opt/bin/python,g' \
		$(1)/opt/bin/cheetah{,-analyze,-compile}
endef

$(eval $(call BuildPackage,python-cheetah))
