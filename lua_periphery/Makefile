include $(TOPDIR)/rules.mk

PKG_NAME:=lua-periphery
PKG_VERSION:=1.1.1
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/lua-periphery
PKG_MAINTAINER:=Sebastian Muszytowski

include $(INCLUDE_DIR)/package.mk

define Package/lua-periphery
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=lua periphery library
  DEPENDS:= +lua
endef

TARGET_CFLAGS += \
	-I$(STAGING_DIR)/usr/include \
	-D_GNU_SOURCE

MAKE_FLAGS += \
	FPIC="$(FPIC)" \
	CFLAGS="$(TARGET_CFLAGS)" \
	LDFLAGS="$(TARGET_LDFLAGS)"

define Package/lua-periphery/description
	lua periphery.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/libcperiphery.so $(1)/usr/lib/libcperiphery.so
	$(INSTALL_DIR) $(1)/usr/lib/lua
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/periphery.so $(1)/usr/lib/lua/periphery.so
	$(INSTALL_DIR) $(1)/usr/lib/lua/lua_periphery_test
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tests/* $(1)/usr/lib/lua/lua_periphery_test/
endef

define Package/lua-periphery/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/libcperiphery.so $(1)/usr/lib/libcperiphery.so
	$(INSTALL_DIR) $(1)/usr/lib/lua
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/periphery.so $(1)/usr/lib/lua/periphery.so
	$(INSTALL_DIR) $(1)/usr/lib/lua/lua_periphery_test
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tests/* $(1)/usr/lib/lua/lua_periphery_test/
endef

$(eval $(call BuildPackage,lua-periphery))
