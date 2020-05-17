# dell-7573-opencore

Opencore hackintosh of a Dell 7573 2-in-1 notebook

Dell Specs:

* i7-8550U
* UHD 620
* 16GB RAM
* 512GB Skynix M.2 SATA SSD
* 1080p touchscreen
* RealTek integrated webcam

I've hackintoshed the Dell 7XXX series for years now.  This is my 3 generation HacBookPro.  I like these machines because I feel they are easy to hack, you can find refurbs relatively cheap(-$700 USD), and the card reader actualy works.

This build is for Catalina 10.15.4 using Opencore 0.5.8.

What's working:

* Wifi and Bluetooth (replaced with Dell 1520 card)
* Trackpad
* Backlight
* Audio - Built in and HDMI
* All USB ports including USB-C
* Power management
* Touchscreen
* SD Card Reader
* HDMI Port (mostly)
* Fn keys to control volume and keyboard backlight
* iMessage and FaceTime (plist in repo sanitized.  You'll need to find your own SN)

What's not working:

* Integrated RealTek webcam
* HDMI not waking from sleep
* Fn keys to control display backlight
