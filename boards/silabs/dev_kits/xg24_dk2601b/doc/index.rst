.. zephyr:board:: xg24_dk2601b

Overview
********

The EFR32MG24 Mighty Gecko Board dev kit contains
a Wireless System-On-Chip from the EFR32MG24 family built on an
ARM Cortex®-M33F processor with excellent low power capabilities.

Hardware
********

- EFR32MG24B310F1536IM48-B Mighty Gecko SoC
- CPU core: ARM Cortex®-M33 with FPU
- Flash memory: 1536 kB
- RAM: 256 kB
- Transmit power: up to +20 dBm
- Operation frequency: 2.4 GHz
- Crystals for LFXO (32.768 kHz) and HFXO (38.4 MHz).
- On board devices:

  - Silicon Labs Si7021 relative humidity & temperature sensor
  - Silicon Labs Si7210 hall effect sensor
  - 2x TDK InvenSense ICS-43434 MEMS microphones with I2S output
  - TDK InvenSense ICM-20689 6-axis inertial measurement sensor
  - Vishay VEML6035 ambient light sensor
  - Bosch BMP384 pressure sensor with internal temperature sensor
  - MX25R3235F 32 Mbit SPI data flash

For more information about the EFR32MG24 SoC and BRD2601B board, refer to these
documents:

- `EFR32MG24 Website`_
- `EFR32MG24 Datasheet`_
- `EFR32xG24 Reference Manual`_
- `BRD2601B User Guide`_

Supported Features
==================

.. zephyr:board-supported-hw::

Connections and IOs
===================

In the following table, the column **Name** contains Pin names. For example, PA2
means Pin number 2 on Port A, as used in the board's datasheets and manuals.

+------+--------------+---------------------+
| Name | Function     | Usage               |
+======+==============+=====================+
| PA4  | GPIO         | LED0                |
+------+--------------+---------------------+
| PB0  | GPIO         | LED1                |
+------+--------------+---------------------+
| PD2  | GPIO         | LED2                |
+------+--------------+---------------------+
| PB2  | GPIO         | Push Button 0       |
+------+--------------+---------------------+
| PB3  | GPIO         | Push Button 1       |
+------+--------------+---------------------+
| PA5  | USART0_TX    | UART Console        |
+------+--------------+---------------------+
| PA6  | USART0_RX    | UART Console        |
+------+--------------+---------------------+
| PC3  | EUSART1_TX   | SPI bus: flash, IMU |
+------+--------------+---------------------+
| PC2  | EUSART1_RX   | SPI bus: flash, IMU |
+------+--------------+---------------------+
| PC1  | EUSART1_SCLK | SPI bus: flash, IMU |
+------+--------------+---------------------+
| PC0  | EUSART1_CS   | SPI bus: flash      |
+------+--------------+---------------------+
| PC4  | I2C0_SCL     | I2C bus             |
+------+--------------+---------------------+
| PC5  | I2C0_SDA     | I2C bus             |
+------+--------------+---------------------+

The default configuration can be found in
:zephyr_file:`boards/silabs/dev_kits/xg24_dk2601b/xg24_dk2601b_defconfig`

System Clock
============

The EFR32MG24 SoC is configured to use the 39 MHz external oscillator on the
board.

Serial Port
===========

The EFR32MG24 SoC has one USART and two EUSARTs.
USART0 is connected to the board controller and is used for the console.

Programming and Debugging
*************************

.. note::
   Before using the kit the first time, you should update the J-Link firmware
   in Simplicity Studio.

Flashing
========

The sample application :zephyr:code-sample:`hello_world` is used for this example.
Build the Zephyr kernel and application:

.. zephyr-app-commands::
   :zephyr-app: samples/hello_world
   :board: xg24_dk2601b
   :goals: build

Connect the xg24_dk2601b to your host computer using the USB port and you
should see a USB connection.

Open a serial terminal (minicom, putty, etc.) with the following settings:

- Speed: 115200
- Data: 8 bits
- Parity: None
- Stop bits: 1

Reset the board and you'll see the following message on the corresponding serial port
terminal session:

.. code-block:: console

   Hello World! xg24_dk2601b

Bluetooth
=========

To use the BLE function, run the command below to retrieve necessary binary
blobs from the SiLabs HAL repository.

.. code-block:: console

   west blobs fetch hal_silabs

Then build the Zephyr kernel and a Bluetooth sample with the following
command. The :zephyr:code-sample:`bluetooth_observer` sample application is used in
this example.

.. zephyr-app-commands::
   :zephyr-app: samples/bluetooth/observer
   :board: xg24_dk2601b
   :goals: build

.. _EFR32MG24 Website:
   https://www.silabs.com/wireless/zigbee/efr32mg24-series-2-socs#

.. _EFR32MG24 Datasheet:
   https://www.silabs.com/documents/public/data-sheets/efr32mg24-datasheet.pdf

.. _EFR32xG24 Reference Manual:
   https://www.silabs.com/documents/public/reference-manuals/efr32xg24-rm.pdf

.. _BRD2601B User Guide:
   https://www.silabs.com/documents/public/user-guides/ug524-brd2601b-user-guide.pdf
