PHONY := u-boot u-boot-distclean kernel

PWD := $(shell pwd)
UBOOT_SRC_DIR = $(PWD)/u-boot/u-boot-2017.04
KERNEL_SRC_DIR = $(PWD)/kernel/linux-4.9
CROSS_COMPILE = arm-linux-gnueabihf-

uboot:
	make -C $(UBOOT_SRC_DIR) ARCH=arm CROSS_COMPILE=$(CROSS_COMPILE) zynq_ax7010_defconfig
	make -C $(UBOOT_SRC_DIR) ARCH=arm CROSS_COMPILE=$(CROSS_COMPILE)
	cp $(UBOOT_SRC_DIR)/u-boot $(PWD)/u-boot.elf

uboot-distclean:
	make -C $(UBOOT_SRC_DIR) ARCH=arm CROSS_COMPILE=$(CROSS_COMPILE) distclean
	rm $(PWD)/u-boot.elf -rf

kernel-config:
	make -C $(KERNEL_SRC_DIR) ARCH=arm CROSS_COMPILE=$(CROSS_COMPILE) xilinx_zynq_defconfig
	
kernel:
	make -C $(KERNEL_SRC_DIR) ARCH=arm CROSS_COMPILE=$(CROSS_COMPILE) uImage LOADADDR=0x8000
	
kernel-distclean:
	make -C $(KERNEL_SRC_DIR) ARCH=arm CROSS_COMPILE=$(CROSS_COMPILE) distclean

kernel-menuconfig:
	make -C $(KERNEL_SRC_DIR) ARCH=arm CROSS_COMPILE=$(CROSS_COMPILE) menuconfig
	
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
	@echo  '  kernel           - Build for kernel'
	@echo  ''
	
.PHONY: $(PHONY)
