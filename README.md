# Move-Xduino

Arduino support package for Cicerone board and generic MAMWLE-based boards.

## Introduction

This repo adds the support of STM32 MCU in Arduino IDE.<br>

This porting is based on:
* [STM32duino Project](https://github.com/stm32duino/Arduino_Core_STM32):
    * [STM32Cube MCU Packages](https://www.st.com/en/embedded-software/stm32cube-mcu-packages.html) including:
        * The HAL hardware abstraction layer, enabling portability between different STM32 devices via standardized API calls
        * The Low-Layer (LL) APIs, a light-weight, optimized, expert oriented set of APIs designed for both performance and runtime efficiency
        * CMSIS device definition for STM32
    * [CMSIS](https://developer.arm.com/embedded/cmsis): Cortex Microcontroller Software Interface Standard (CMSIS) is a vendor-independent hardware abstraction layer for the Cortex®-M processor series and defines generic tool interfaces. It has been packaged as a module for Arduino IDE: https://github.com/stm32duino/ArduinoModule-CMSIS
    * [GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm): Arm Embedded GCC compiler, libraries and other GNU tools necessary for bare-metal software development on devices based on the Arm Cortex-M. Packages are provided thanks [The xPack GNU Arm Embedded GCC](https://xpack.github.io/arm-none-eabi-gcc/): https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack

## Getting Started

This repo is available as a package usable with [Arduino Boards Manager](https://www.arduino.cc/en/guide/cores).

Add this link in the (Arduino IDE) "*Additional Boards Managers URLs*" field:

https://github.com/Move-X/Move-Xduino/raw/main/package_move-x_index.json

**Tested on Arduino IDE 1.8 and Arduino IDE 2.0**

## Requirements
1. The Uploader Tool is based on the [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html) utility. 
Please install it and ensure that 'STM32CubeProgrammer installation path/bin' is included in the (user) PATH environment
2. **CP210X Usb-to-Serial** present on Cicerone board to be used for __serial communication__:
    * Windows Users
        * Install CP210x VCP Drivers from https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers
    * MacOs Users and Linux Users
        * CP210x Drivers should be natively inserted in kernel. If this is not the case, please install it (https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers)
3. **CP210X Usb-to-Serial** present on Cicerone board to be used for __serial programming__:
    * MacOs Users [BETA]
        * Install [Python 3](https://www.python.org/downloads/) if not yet present on the system
    * Linux Users [BETA]
        * Install [Python 3](https://www.python.org/downloads/) if not yet present on the system
        * Execute add_rules.sh script to allow non-root users to access ttyUSB device
