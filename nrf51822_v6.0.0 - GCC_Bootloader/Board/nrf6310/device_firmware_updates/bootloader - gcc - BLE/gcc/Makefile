TARGET_CHIP := NRF51822_QFAA_CA
BOARD := BOARD_NRF6310

#SOFTDEVICE_FLAGS=-DS310_STACK -DS130
SOFTDEVICE_FLAGS=-DS110
MEMORY_LIMITATIONS=-D__STACK_SIZE=1024 -D__HEAP_SIZE=1024

CFLAGS += -DBLE_STACK_SUPPORT_REQD -DBOOTLOADER_BANKED -DBLE_STACK_SUPPORT_REQD $(SOFTDEVICE_FLAGS) -DBOARD_NRF6310
#CFLAGS += -DBOOTLOADER_BANKED -DS310_STACK -DS130 -DBOARD_NRF6310
#CLFAGS += -DEPD_ENABLE_EXTRA_RAM
CFLAGS += -Os -flto -ffunction-sections -fdata-sections -fno-builtin

LDFLAGS = --specs=nano.specs -lc -lnosys -Wl,--gc-sections

ASMFLAGS = $(MEMORY_LIMITATIONS)

DEVICESERIES := nrf51

SDK_PATH = /opt/nrf51_sdk/v6/nrf51822/

OUTPUT_FILENAME=dobots

C_SOURCE_FILES += main.c
C_SOURCE_FILES += dfu_dual_bank.c
C_SOURCE_FILES += dfu_transport_ble.c
C_SOURCE_FILES += serial.c
C_SOURCE_FILES += bootloader.c
C_SOURCE_FILES += bootloader_util_gcc.c
C_SOURCE_FILES += $(SDK_PATH)Source/ble/ble_services/ble_dfu.c
C_SOURCE_FILES += $(SDK_PATH)Source/app_common/app_timer.c
C_SOURCE_FILES += $(SDK_PATH)Source/app_common/pstorage.c
C_SOURCE_FILES += $(SDK_PATH)Source/app_common/hci_mem_pool.c
C_SOURCE_FILES += $(SDK_PATH)Source/app_common/app_scheduler.c
C_SOURCE_FILES += $(SDK_PATH)Source/app_common/app_gpiote.c
C_SOURCE_FILES += $(SDK_PATH)Source/app_common/crc16.c
C_SOURCE_FILES += $(SDK_PATH)Source/ble/ble_conn_params.c
C_SOURCE_FILES += $(SDK_PATH)Source/ble/ble_advdata.c
C_SOURCE_FILES += $(SDK_PATH)Source/ble/ble_services/ble_srv_common.c
C_SOURCE_FILES += $(SDK_PATH)Source/ble/softdevice_handler.c

INCLUDEPATHS += -I"$(SDK_PATH)Include/ble"
INCLUDEPATHS += -I"$(SDK_PATH)Include/app_common"
INCLUDEPATHS += -I"/opt/softdevices/s110_nrf51822_7.0.0_API/include/"
#INCLUDEPATHS += -I"/opt/softdevices/s130_nrf51822_0.5.0-1.alpha_API/include/"
INCLUDEPATHS += -I"$(SDK_PATH)Include/sd_common"
INCLUDEPATHS += -I"$(SDK_PATH)Include/ble/ble_services"
INCLUDEPATHS += -I"../include/ble_transport"
INCLUDEPATHS += -I"../include"
INCLUDEPATHS += -I"../"

DEVICE_VARIANT := xxaa
#DEVICE_VARIANT := xxab

USE_SOFTDEVICE := S110
#USE_SOFTDEVICE := S210
#USE_SOFTDEVICE := S130

LINKER_SCRIPT = gcc_$(DEVICESERIES)_bootloader_$(DEVICE_VARIANT).ld
OUTPUT_FILENAME := $(OUTPUT_FILENAME)_bootloader_$(DEVICE_VARIANT)

include $(SDK_PATH)Source/templates/gcc/Makefile.common
