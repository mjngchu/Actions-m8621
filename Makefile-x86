# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2006-2011 OpenWrt.org

include $(TOPDIR)/rules.mk

ARCH:=i386
BOARD:=x86
BOARDNAME:=x86
FEATURES:=squashfs ext4 vdi vmdk vhdx pcmcia targz fpu boot-part rootfs-part
SUBTARGETS:=generic legacy geode 64

KERNEL_PATCHVER:=5.10

KERNELNAME:=bzImage

include $(INCLUDE_DIR)/target.mk

DEFAULT_PACKAGES += partx-utils mkf2fs e2fsprogs kmod-button-hotplug \
		    kmod-8139cp kmod-8139too kmod-alx kmod-amazon-ena kmod-amd-xgbe \
		    kmod-bnx2 kmod-bnx2x kmod-button-hotplug kmod-drm-amdgpu kmod-drm-i915 \
		    kmod-e1000 kmod-e1000e kmod-forcedeth kmod-fs-vfat kmod-i40e kmod-iavf \
		    kmod-igb kmod-igbvf kmod-igc kmod-ipt-nat kmod-ipt-nat6 kmod-ixgbe \
		    kmod-lib-zstd kmod-mlx4-core kmod-mlx5-core kmod-mmc kmod-pcnet32 \
		    kmod-phy-broadcom kmod-r8125 kmod-r8168 kmod-sdhci kmod-tcp-bbr \
		    kmod-tg3 kmod-tulip kmod-usb-hid kmod-vmxnet3 kmod-iwlwifi kmod-mt76 \
		    wlwifi-firmware-iwl6000g2 iwlwifi-firmware-ax210

$(eval $(call BuildTarget))

$(eval $(call $(if $(CONFIG_ISO_IMAGES),SetupHostCommand,Ignore),mkisofs, \
	Please install mkisofs. , \
	mkisofs -v 2>&1 , \
	genisoimage -v 2>&1 | grep genisoimage, \
	xorrisofs -v 2>&1 | grep xorriso \
))
