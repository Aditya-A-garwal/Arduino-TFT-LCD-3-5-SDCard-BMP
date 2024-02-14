# Load BMP Image from SD Card And Display It On a 3.5" TFT LCD Touchscreen With Arduino UNO R3/R4

![GitHub License](https://img.shields.io/github/license/Aditya-A-garwal/Arduino-TFT-LCD-3-5-SDCard-BMP)
![GitHub forks](https://img.shields.io/github/forks/Aditya-A-garwal/Arduino-TFT-LCD-3-5-SDCard-BMP?style=flat-square&color=blue)
![GitHub Repo stars](https://img.shields.io/github/stars/Aditya-A-garwal/Arduino-TFT-LCD-3-5-SDCard-BMP?style=flat-square&color=blue)
![GitHub issues](https://img.shields.io/github/issues-raw/Aditya-A-garwal/Arduino-TFT-LCD-3-5-SDCard-BMP?style=flat-square&color=indianred)
![GitHub closed issues](https://img.shields.io/github/issues-closed-raw/Aditya-A-garwal/Arduino-TFT-LCD-3-5-SDCard-BMP?style=flat-square)
![GitHub pull requests](https://img.shields.io/github/issues-pr/Aditya-A-garwal/Arduino-TFT-LCD-3-5-SDCard-BMP?style=flat-square&color=indianred)
![GitHub closed pull requests](https://img.shields.io/github/issues-pr-closed/Aditya-A-garwal/Arduino-TFT-LCD-3-5-SDCard-BMP?style=flat-square)
![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/Aditya-A-garwal/Arduino-TFT-LCD-3-5-SDCard-BMP/build.yml?style=flat-square)

## Overview

This repository contains a program to load a BMP Image from an SD Card and display it on a 3.5" touch screen display shield with an Arduino UNO R3/R4, as shown below -

|![Image of LCD Touch Shield from Top](images/LCD_top.png)|![Image of LCD Touch Shield from Bottom](images/LCD_bottom.png)|
|-|-|

Most 3.5" LCD Touch displays use the ILI9486 Display Driver and include a resistive touchscreen. **The PCB Layout & silkscreen text may vary slightly between displays. This does not change their behaviour and functionality.** This repository depends on the following libraries -

- [Adafruit Touch Screen Library](https://github.com/adafruit/Adafruit_TouchScreen) to manage touch input
- [Adafruit GFX Library](https://github.com/adafruit/Adafruit-GFX-Library/tree/master) for graphics primitives
- [This fork of the MCUFriend KBV library](https://github.com/slviajero/MCUFRIEND_kbv) to drive the display (this makes it compatible with the UNO R4)

The program has been written using PlatformIO, and has been tested on the [Arduino UNO R3](https://docs.arduino.cc/hardware/uno-rev3/), [Arduino UNO R4 Minima](https://docs.arduino.cc/hardware/uno-r4-minima/) & [Arduino UNO R4 WiFi](https://docs.arduino.cc/hardware/uno-r4-wifi/).

The loadBMP, read16 and read32 functions in [```src/main.cpp```](/src/main.cpp) have been taken from [this example in the MCUFRIEND repository](https://github.com/prenticedavid/MCUFRIEND_kbv/blob/master/examples/showBMP_kbv_Uno/showBMP_kbv_Uno.ino), for fair use and educational purposes. All code taken from other repositories belongs to their respective authors and are protected by their respective licenses.

## Building/Uploading With PlatformIO

Since this project has been written using PlatformIO by default, simply run the following commands to fetch the libraries, build the project and upload the program -

```shell
pio pkg install
pio run
pio run --target upload
```

## Building/Uploading With Arduino IDE

Create a new sketch and copy the contents of [```src/main.cpp```](/src/main.cpp) from this repository into the default ```.ino``` file. Create a new tab/file in the IDE named ```constants.h``` and copy the contents of [```src/constants.h```](/src/main.cpp) from this repository into this file.

Install the Adafruit Touch Screen Library and Adafruit GFX Library from the Library Manager (under *Sketch>Include Library>Manage Libraries...*)

Download [this](https://github.com/slviajero/MCUFRIEND_kbv) repository as a ZIP file and install it by navigating to *Sketch>Include Library>Add .ZIP Library*, and selecting the downloaded file from the file explorer.

After this, you can Build and Upload the program as usual.


## Using the Example

Format an SD Card with a FAT32 filesystem with a single drive. Load a BMP Image whose dimensions are under 320x480 into the SD Card and plug the SD Card into the slot situated on the back of the display. A [BMP Image File](/example.bmp) is included in the repository in case one is not immediately available.

As soon as the program is uploaded, the display should turn red and the image should be slowly painted on the display, starting from the top-left corner.

## Troubleshooting

Some common problems and their solutions -

|Problem|Solution|
|-|-|
|Display stays white after uploading program|Non-Standard Driver (not ILI9486)|
|Display not responding after touch|Try changing the order of the touch pins in [```src/constants.h```](/src/constants.h) file, i.e. swap the values of ```XP```, ```YP```, ```XM``` and ```YM```|
|Compilation issues related to SPI|Update the Arduino IDE version and/or install the SPI library|
|Display Flickering/Arduino is reset automatically|Faulty Power Supply/Cable|

