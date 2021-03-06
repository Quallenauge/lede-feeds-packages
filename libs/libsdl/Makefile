#
# Copyright (C) 2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=SDL
PKG_VERSION:=1.2.14
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://www.libsdl.org/release/
PKG_MD5SUM:=e52086d1b508fa0b76c52ee30b55bec4

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libsdl
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Simple DirectMedia Layer
  URL:=http://www.libsdl.org
  DEPENDS:=+zlib +libpthread
endef

define Package/libsdl/description
 SDL is a library that allows programs portable low level access to a video
 framebuffer, audio output, mouse, and keyboard.
endef

CONFIGURE_ARGS+= \
	--enable-libc \
	--enable-video \
	--enable-events \
	--disable-joystick \
	--disable-cdrom \
	--enable-threads \
	--enable-timers \
	--enable-file \
	--enable-loadso \
	--enable-cpuinfo \
	--enable-assembly \
	--disable-oss \
	--disable-alsatest \
	--disable-alsa-shared \
	--disable-esd \
	--disable-esdtest \
	--enable-esd-shared \
	--disable-pulseaudio \
	--disable-pulseaudio-shared \
	--disable-arts \
	--disable-arts-shared \
	--disable-nas \
	--disable-nas-shared \
	--disable-diskaudio \
	--disable-dummyaudio \
	--disable-mintaudio \
	--disable-nasm \
	--disable-altivec \
	--disable-ipod \
	--disable-nanox \
	--disable-video-x11 \
	--disable-x11-shared \
	--disable-dga \
	--disable-video-dga \
	--disable-video-x11-dgamouse \
	--disable-video-x11-vm \
	--disable-video-x11-xv \
	--disable-video-x11-xinerama \
	--disable-video-x11-xme \
	--disable-video-x11-xrandr \
	--disable-video-photon \
	--disable-video-carbon \
	--disable-video-cocoa \
	--enable-video-fbcon \
	--disable-video-directfb \
	--disable-video-ps2gs \
	--disable-video-ps3 \
	--disable-video-ggi \
	--disable-video-svga \
	--disable-video-vgl \
	--disable-video-wscons \
	--disable-video-aalib \
	--disable-video-caca \
	--disable-video-qtopia \
	--disable-video-picogui \
	--disable-video-xbios \
	--disable-video-gem \
	--disable-video-dummy \
	--disable-video-opengl \
	--disable-osmesa-shared \
	--disable-screensaver \
	--enable-input-events \
	--disable-input-tslib \
	--enable-pth \
	--enable-pthreads \
	--enable-pthread-sem \
	--disable-stdio-redirect \
	--disable-directx \
	--enable-sdl-dlopen \
	--disable-atari-ldg \
	--disable-clock_gettime \
	--without-x \
	--disable-rpath \
	--disable-audio \
	--disable-alsa

#CONFIGURE_VARS+= \
#		ac_cv_path_DIRECTFBCONFIG=no \

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include $(1)/usr/lib/pkgconfig
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/SDL* \
		$(1)/usr/include/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libSDL*.{a,so*} \
		$(1)/usr/lib/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig


	$(INSTALL_DIR) $(1)/usr/share/aclocal
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/aclocal/* \
		$(1)/usr/share/aclocal/

	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/sdl-config \
		$(1)/usr/bin/

	$(SED) 's,^\(exec_prefix\|prefix\)=.*,\1=\"$(STAGING_DIR)/usr/\",g' \
		$(1)/usr/bin/sdl-config

	$(INSTALL_DIR) $(1)/host/bin
	ln -sf ../../usr/bin/sdl-config $(1)/host/bin/
endef

define Package/libsdl/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libSDL*.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libsdl))
