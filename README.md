# MAMWLE_ArduinoSupport

Arduino support package for Cicerone board and generic MAMWLE-based boards.

## Introduction

This repo adds the support of STM32 MCU in Arduino IDE.<br>

This porting is based on:
* [STM32Cube MCU Packages](https://www.st.com/en/embedded-software/stm32cube-mcu-packages.html) including:
    * The HAL hardware abstraction layer, enabling portability between different STM32 devices via standardized API calls
    * The Low-Layer (LL) APIs, a light-weight, optimized, expert oriented set of APIs designed for both performance and runtime efficiency
    * CMSIS device definition for STM32
* [CMSIS](https://developer.arm.com/embedded/cmsis): Cortex Microcontroller Software Interface Standard (CMSIS) is a vendor-independent hardware abstraction layer for the Cortex®-M processor series and defines generic tool interfaces. It has been packaged as a module for Arduino IDE: https://github.com/stm32duino/ArduinoModule-CMSIS
* [GNU Arm Embedded Toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm): Arm Embedded GCC compiler, libraries and other GNU tools necessary for bare-metal software development on devices based on the Arm Cortex-M. Packages are provided thanks [The xPack GNU Arm Embedded GCC](https://xpack.github.io/arm-none-eabi-gcc/): https://github.com/xpack-dev-tools/arm-none-eabi-gcc-xpack

## Getting Started

This repo is available as a package usable with [Arduino Boards Manager](https://www.arduino.cc/en/guide/cores).

Add this link in the (Arduino IDE) "*Additional Boards Managers URLs*" field:

https://github.com/Move-X/MAMWLE_ArduinoSupport/raw/main/package_move-x_index.json

**Tested on Arduino IDE 1.8 and Arduino IDE 2.0**

## Requirements
1) The uploader tool that flash the scripts into mcu needs "*STM32CubeProgrammer*" utility available at https://www.st.com/en/development-tools/stm32cubeprog.html. Please install it. (Ensure that '[STM32CubeProgrammer path]/bin' is included in the PATH environment)


~~2) For MacOs and Linux users, Python 3.7 or higher need to be installed. Follow this link https://www.python.org/downloads/ if not yet installed on system. (Ensure that '[python installation path]' is included in the PATH environment)~~

**Please note that Serial upload through usb port of Cicerone board is not yet supported on macOS and Linux**


## Original Project:
https://github.com/stm32duino/Arduino_Core_STM32
