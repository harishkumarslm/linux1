# SPDX-License-Identifier: GPL-2.0
#
# Makefile for the linux kernel.
#

# CPU-specific support
obj-$(CONFIG_SOC_AT91RM9200)	+= at91rm9200.o
obj-$(CONFIG_SOC_AT91SAM9)	+= at91sam9.o
obj-$(CONFIG_SOC_SAM9X60)	+= sam9x60.o
obj-$(CONFIG_SOC_SAM9X7)	+= sam9x7.o
obj-$(CONFIG_SOC_SAMA5)		+= sama5.o sam_secure.o
obj-$(CONFIG_SOC_SAMA7)		+= sama7.o
obj-$(CONFIG_SOC_SAMV7)		+= samv7.o
obj-$(CONFIG_AT91_VDEC_G1)	+= memalloc.o vdec_g1.o

# Power Management
obj-$(CONFIG_ATMEL_PM)		+= pm.o pm_suspend.o

ifeq ($(CONFIG_PM_DEBUG),y)
CFLAGS_pm.o += -DDEBUG
endif

$(obj)/pm_data-offsets.h: $(obj)/pm_data-offsets.s FORCE
	$(call filechk,offsets,__PM_DATA_OFFSETS_H__)

$(obj)/pm_suspend.o: $(obj)/pm_data-offsets.h

targets += pm_data-offsets.s
clean-files += pm_data-offsets.h
