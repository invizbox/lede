include $(TOPDIR)/rules.mk

PKG_NAME:=brcmfmac-module-ap6356s
PKG_VERSION:=0
PKG_FLAGS:=nonshared

include $(INCLUDE_DIR)/package.mk

BRCMFMAC4356_SDIO_URL:=@GITHUB/khadas/fenix/022fdc3a1333d2d16f84c2e59e4507c92a668a3d/archives/hwpacks/wlan-firmware/brcm/
BRCMFMAC4356_SDIO_FILE:=brcmfmac4356-sdio-ap6356s

define Download/brcmfmac4356_sdio_txt
  FILE:=$(BRCMFMAC4356_SDIO_FILE).txt
  URL:=$(BRCMFMAC4356_SDIO_URL)
  URL_FILE:=brcmfmac4356-sdio.txt
  HASH:=205af14e8e98acc858d729e3a8161c035fee2c186146a42d58bb0137b9c3c360
endef
$(eval $(call Download,brcmfmac4356_sdio_txt))

define Download/brcmfmac4356_sdio_bin
  FILE:=$(BRCMFMAC4356_SDIO_FILE).bin
  URL:=$(BRCMFMAC4356_SDIO_URL)
  URL_FILE:=brcmfmac4356-sdio.bin
  HASH:=42e603aacc1c25b9f797cab44a192a647f9a5527871954d2eb910f508edbd8c7
endef
$(eval $(call Download,brcmfmac4356_sdio_bin))

define Package/brcmfmac-module-ap6356s
  SECTION:=firmware
  CATEGORY:=Firmware
  URL:=https://github.com/khadas/fenix/blob/master/archives/hwpacks/wlan-firmware/brcm/
  DEPENDS:=@TARGET_sunxi
  PKGARCH:=all
  TITLE:=AP6356S module Wi-Fi firmware
endef

define Package/brcmfmac-module-ap6356s/description
  Firmware for the Wi-Fi part of AP6356S Wi-Fi/BT combo module.
endef

define Build/Prepare
	rm -rf $(PKG_BUILD_DIR)
	mkdir -p $(PKG_BUILD_DIR)
	cp $(DL_DIR)/$(BRCMFMAC4356_SDIO_FILE).txt $(PKG_BUILD_DIR)/brcmfmac4356-sdio.txt
	cp $(DL_DIR)/$(BRCMFMAC4356_SDIO_FILE).bin $(PKG_BUILD_DIR)/brcmfmac4356-sdio.bin
endef

define Build/Compile
	true
endef

define Package/brcmfmac-module-ap6356s/install
	$(INSTALL_DIR) $(1)/lib/firmware/brcm/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/brcmfmac4356-sdio.txt $(1)/lib/firmware/brcm/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/brcmfmac4356-sdio.bin $(1)/lib/firmware/brcm/
endef

$(eval $(call BuildPackage,brcmfmac-module-ap6356s))
