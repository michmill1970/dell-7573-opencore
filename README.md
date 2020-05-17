# dell-7573-opencore

Opencore hackintosh of a Dell 7573 2-in-1 notebook

## Dell Specs:

* Dell 7573 with BIOS v1.16.0
* i7-8550U
* UHD 620
* 16GB RAM
* 512GB Skynix M.2 SATA SSD
* 1080p touchscreen
* RealTek integrated webcam

I've hackintoshed the Dell 7XXX series for years now.  This is my 3 generation HacBookPro.  I like these machines because I feel they are easy to hack, you can find refurbs relatively cheap(-$700 USD), and the card reader actualy works.

This build is for Catalina 10.15.4 using Opencore 0.5.8.

## What's working

* Wifi and Bluetooth (replaced with Dell 1520 card)
* Trackpad
* Backlight
* Audio - Built in and HDMI
* All USB ports including USB-C
* Power management including sleep
* Touchscreen
* SD Card Reader
* HDMI Port (mostly, see below)
* Fn keys to control volume and keyboard backlight
* Combo jack
* iMessage and FaceTime (plist in repo sanitized.  You'll need to find your own SN)

## What's not working

* Integrated RealTek webcam
* HDMI not waking from sleep
* Fn keys to control display backlight

## BIOS Configuration
Turn off the Secure Boot. That should be all.

## UEFI Variables
In order to run macOS without having to use WhatEverGreen's framebuffer patching and CFG-related booter quirks, it is strongly recommended to modify a few UEFI variables. To do that, you can use ModifiedGrub.efi (credits brainsucker), which provides the setup_var command.

The following variables should be updated:
Variable|Offset|Default value|Desired value|Comment
---|---|---|---|---
CFG Lock|0x4C7|0x01 (enabled)|0x00 (disabled)|Disable CFG Lock to prevent MSR 0x02 errors on boot
DVMT Pre-allocated|0x76D|0x01 (32M)|0x02 (64M)|Increase DVMT pre-allocated size to 64M
DVMT Total GFX Memory|0x76E|0x02 (256M)|0x03 (MAX)|Increase total GFX memory limit to maximum

**DISCLAIMER: those offset values are taken from 1.15.0 and 1.16.0 firmwares. DO NOT use them with older versions unless you have checked that they are the same.**


Usage:
`setup_var <offset> <value>`
ex.
`setup_var 0x4C7 0x00`

## Notes
* The included CpuFriendDataProvider is made for i7-8550U. If you have the i5-8250U processor, **DO NOT** use this kext. You can make a new data provider kext for that CPU (and make a PR!).

## Credits
* [acidanthera](https://github.com/acidanthera) for [OpenCore](https://github.com/acidanthera/OpenCorePkg)
* The Dortania crew for their [documentation](https://dortania.github.io/)
* [konrad11901](https://github.com/konrad11901) for his [repo](https://github.com/konrad11901/Inspiron7373-macOS)
* Reddit user [/u/ZeroFourFour](https://www.reddit.com/user/ZeroFourFour) for helping me get an inital boot
