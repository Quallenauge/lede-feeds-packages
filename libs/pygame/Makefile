# This is free software, licensed under the GNU General Public License
# v3. See /LICENSE for more information.
include $(TOPDIR)/rules.mk

PKG_NAME:=pygame
PKG_VERSION:=1.9.2
PKG_RELEASE:=1
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://bitbucket.org/pygame/pygame/downloads/

PKG_BUILD_DEPENDS:=python3 freetype

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/pygame
	SUBMENU:=Python
	SECTION:=lang
	CATEGORY:=Languages
	TITLE:=pygame
	URL:=http://pygame.org
#	DEPENDS:=+python3-light +libsdl +libpng +libjpeg +libsdl-image +libsdl-mixer +libsdl-ttf
	DEPENDS:=+python3 +libsdl +libpng +libjpeg
endef

define Package/pygame/description
Pygame is a set of Python modules designed for writing video games.
Pygame adds functionality on top of the excellent SDL library.
This allows you to create fully featured games and multimedia programs in the python language.
endef

define Build/Compile
	pwd
	$(if $(Build/Compile/Py3Mod),,@echo Python3 packaging code not found.; false)
	$(call Build/Compile/Py3Mod,, \
		install --prefix="$(PKG_INSTALL_DIR)/usr", \
		NO_SCRAP=1 \
		NO_MIXER=1 \
		NO_PORTMIDI=1 \
		NO_PORTTIME=1 \
	)
endef

define Build/Compile2
	$(call Build/Compile/Py3Mod,,\
		install \
		--prefix="$(PKG_INSTALL_DIR)/usr" \
		, \
		LOCALBASE="$(STAGING_DIR)/usr" \
		NO_SCRAP=1 \
		NO_MIXER=1 \
		NO_PORTMIDI=1 \
		NO_PORTTIME=1 \
		auto
	)
endef

define Package/pygame/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call BuildPackage,pygame))
