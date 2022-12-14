# Move-Xduino

Arduino support package for Cicerone board and generic MAMWLE-based boards.

![Move-Xduino Logo](/Docs/Move-Xduino_logo.png?raw=true)

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

Add this link in the (Arduino IDE) "*Additional Boards Managers URLs*" field (*File -> Preferences*):

https://github.com/Move-X/Move-Xduino/raw/main/package_move-x_index.json

Then, from *Boards Manager* (*Tools -> Board*), search for "*Move-X*" and install the latest version of "*MAMWLE based boards by Moxe-X*"

**Tested on Arduino IDE 1.8 and Arduino IDE 2.0**

## Requirements
1. **CP210X Usb-to-Serial** (present on Cicerone board) for __serial communication__:
    * Windows Users
        * Install CP210x VCP Drivers from https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers
    * MacOs Users and Linux Users
        * CP210x Drivers should be natively inserted in kernel. If this is not the case, please install it (https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers)
        * For MacOS users, please allow system access to the board after first connection (a popup will be displayed).
2. **CP210X Usb-to-Serial** (present on Cicerone board) for __serial programming__:
    * All OS
        * The customized (Arduino IDE) Uploader Tool is based on the [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html) utility. Please install it and ensure that 'STM32CubeProgrammer installation path/bin' is included in the (user) PATH environment
    * Windows Users
        * No other requirements
    * MacOs Users [BETA]
        * Install [Python 3](https://www.python.org/downloads/) if not yet present on the system
        * Please allow system access to the board after first connection (a popup will be displayed).
        * On Apple M1 you may need to execute "sudo xattr -r -d com.apple.quarantine ~/Library/Arduino15/packages/Move-X/tools/MAMWLE_Tool/*/macos/libusb-1.0_arm.dylib" to allow execution of libusb
    * Linux Users [BETA]
        * Install [Python 3](https://www.python.org/downloads/) if not yet present on the system
        * Execute "sudo sh ~/.arduino15/packages/Move-X/tools/MAMWLE_Tool/*/linux/add_rule.sh" to allow non-root users to access ttyUSB device

## Utilities

### **Manual Boot Mode controller for Cicerone Board (for version 1.0.2+)**

This tool lets you control manually the BOOT0 pin of Cicerone Board to enter/exit Boot Mode.
It enables the use of STM32CubeProgrammer for Serial Connection to the STM32 MCU

* Windows Users
    * Go to "%LOCALAPPDATA%/Arduino15/packages/Move-X/tools/MAMWLE_Tool/{version}/"
    * Open a terminal in this directory
    * execute ".\win\busybox.exe sh .\CiceroneBootControl.sh {mode} {com_port}"
        * {mode}:
            * "boot" -> enter boot mode (code downloading)
            * "run"  -> enter run mode (code execution)
        * {com_port}:
            * Ex. "COM1"
* MacOs Users
    * Go to "/Users/{username}/Library/Arduino15/packages/Move-X/tools/MAMWLE_Tool/{version}/" (Finder -> Menu -> Go -> [hold option key] Library -> Arduino 15)
    * Open a terminal in this directory
    * execute "sh .\CiceroneBootControl.sh {mode} {com_port}"
        * {mode}:
            * "boot" -> enter boot mode (code downloading)
            * "run"  -> enter run mode (code execution)
        * {com_port}:
            * Ex. "/dev/cu.usbserial-00406114"
* Linux Users
    * Go to "/home/{username}/.arduino15/packages/Move-X/tools/MAMWLE_Tool/{version}/" (is hidden by default)
    * Open a terminal in this directory
    * execute "sh .\CiceroneBootControl.sh {mode} {com_port}"
        * {mode}:
            * "boot" -> enter boot mode (code downloading)
            * "run"  -> enter run mode (code execution)
        * {com_port}:
            * Ex. "/dev/ttyUSB0"

### **Manual Firmware Uploader tool for Cicerone Board (for version 1.0.2+)**

This tool lets you flash manually a ".bin/.hex" compiled firmware to the Cicerone Board using serial communication.

* Windows Users
    * Go to "%LOCALAPPDATA%/Arduino15/packages/Move-X/tools/MAMWLE_Tool/{version}/"
    * Open a terminal in this directory
    * execute ".\win\busybox.exe sh .\stm32CubeProg.sh 1 {file_path} {com_port}"
        * {file_path}: file path name to be downloaded (bin, hex)
        * {com_port}:  Ex. "COM1"
* MacOs Users
    * Go to "/Users/{username}/Library/Arduino15/packages/Move-X/tools/MAMWLE_Tool/{version}/" (Finder -> Menu -> Go -> [hold option key] Library -> Arduino 15)
    * Open a terminal in this directory
    * execute "sh .\stm32CubeProg.sh 1 {file_path} {com_port}"
        * {file_path}: file path name to be downloaded (bin, hex)
        * {com_port}:  Ex. "/dev/cu.usbserial-00406114"
* Linux Users
    * Go to "/home/{username}/.arduino15/packages/Move-X/tools/MAMWLE_Tool/{version}/" (is hidden by default)
    * Open a terminal in this directory
    * execute "sh .\stm32CubeProg.sh 1 {file_path} {com_port}"
        * {file_path}: file path name to be downloaded (bin, hex)
        * {com_port}:  Ex. "/dev/ttyUSB0"