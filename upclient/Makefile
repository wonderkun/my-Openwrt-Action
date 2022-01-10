include $(TOPDIR)/rules.mk
# PAK NAME 必须和包所在文件夹一样.
PKG_NAME:=upclient

# 下面三个参数随便填写.
PKG_VERSION:=20220105
PKG_RELEASE:=1
PKG_MAINTAINER:=Y.A.K.E

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)
include $(INCLUDE_DIR)/package.mk

# 下面是显示在menuconfig中的菜单路径
# SUBMENU后面跟着的是我自己diy的一个菜单选项,
# 这个菜单里面全是自己的包,比较好找.

define Package/$(PKG_NAME)
	SECTION:=utils
	CATEGORY:=Utilities
	SUBMENU:=00.Y.A.K.E_BIN
	PKGARCH:=all
	DEFAULT:=y
	TITLE:=upclient bin
endef

# 包介绍说明,不要用中文.
define Package/$(PKG_NAME)/description
    upclient bin client ~~ update proxy
endef

define Package/$(PKG_NAME)/preinst
endef

# 安装后执行的脚本
# 这里大概作用就是安装后给./usr/bin/v2ray添加执行权限.

define Package/$(PKG_NAME)/postinst
#!/bin/sh
if [ -z "$${IPKG_INSTROOT}" ]; then
	chmod 755 "$${IPKG_INSTROOT}/usr/bin/upclient" >/dev/null 2>&1
	chmod 755 "$${IPKG_INSTROOT}/etc/init.d/upclient" >/dev/null 2>&1
	ln -sf  "../init.d/upclient" "$${IPKG_INSTROOT}/etc/rc.d/S99upclient"
	ln -sf  "../init.d/upclient" "$${IPKG_INSTROOT}/etc/rc.d/K99upclient"
fi
exit 0
endef

define Build/Prepare
endef

define Build/Configure
endef

define Build/Compile
endef

# 安装作业
# 这里一般就是复制文件
# 如果有更多文件直接参考修改,非常简单.

# 两条命令一组
# 第一条是指定复制到的目录
# 第二条是拷贝文件.

define Package/$(PKG_NAME)/install
	$(CP) ./files/* $(1)/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))