
include $(TOPDIR)/rules.mk

PKG_NAME:=python3-setuptools-light
PKG_VERSION:=34.3.1
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/pypa/setuptools/archive/
#PKG_MD5SUM:=ea6ed9ab1a4abe978dade73a592a229c

PKG_BUILD_DIR:=$(BUILD_DIR)/setuptools-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3-light python3-six

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-setuptools-light
  SECTION:=language-python
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Python Setuptools Light
  URL:=https://pypi.python.org/pypi/setuptools/
endef

define Package/python3-setuptools-light/description
 Easily download, build, install, upgrade, and uninstall Python packages.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,, \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)" \
	)
endef

define Package/python3-setuptools-light/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python3-setuptools-light))
