PHONY := u-boot u-boot-distclean

PWD := $(shell pwd)
UBOOT_SRC_DIR = $(PWD)/u-boot/u-boot-2017.04
CROSS_COMPILE = arm-linux-gnueabihf-

uboot:
	make -C $(UBOOT_SRC_DIR) ARCH=arm CROSS_COMPILE=$(CROSS_COMPILE) zynq_ax7010_defconfig
	make -C $(UBOOT_SRC_DIR) ARCH=arm CROSS_COMPILE=$(CROSS_COMPILE)
	cp $(UBOOT_SRC_DIR)/u-boot $(PWD)/u-boot.elf

uboot-distclean:
	make -C $(UBOOT_SRC_DIR) ARCH=arm CROSS_COMPILE=$(CROSS_COMPILE) distclean
	rm $(PWD)/u-boot.elf -rf

BOOT:
	bootgen -image boot.bif -o i BOOT.bin
BOOT-clean:
	rm BOOT.bin -rf
	
help:
	@echo  ''
	@echo  '  ------------ XILINX ------------'
	@echo  '  uboot            - Build for u-boot'
	@echo  '  uboot-distclean  - Distclean for u-boot'
	@echo  '  BOOT             - BOOT image'
	@echo  '  BOOT-clean       - BOOT image clean'
	@echo  ''
	
.PHONY: $(PHONY)
