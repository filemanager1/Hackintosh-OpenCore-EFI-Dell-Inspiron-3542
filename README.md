
# Hackintosh on the Dell Inspiron 15 3542
Repository containing personal files needed to run macOS Catalina on the Dell Inspiron 15 3542, still a work in progress so don't use this as your daily driver!

<p align="center">
  <img src="https://github.com/filemanager1/Hackintosh-OpenCore-EFI-Dell-Inspiron-3542/blob/main/Unrelated/Laptop.png?raw=true" alt="Your Hackintosh will look like this!"/>
</p>

## Hardware configuration
Your laptop should have specifications similar to the ones listed in the table below for this to be compatible, if you laptop has a dGPU or a different Wireless card you'll have to configure it yourself, **no support is provided at all**.
|Specification|Detail|
|--|--|
|Model|Inspiron 3542|
|BIOS|A16 (24/09/2020)|
|Processor|i3-4030U|
|RAM|1 x 4GB 1600 MHz DDR3|
|Graphics|Intel HD 4400|
|Audio Codec|ALC3234|
|Display|LCD HD 1366x768 (15.6 inches)|
|Wi-Fi/Bluetooth Card|Atheros AR9565|
|Ethernet Controller|Realtek RTL8106E|

## What works
* macOS Catalina (10.15)
* Keyboard
* Touchpad
* USB ports
	* Two 2.0 USB ports and one 3.0 USB port
* iGPU - Intel HD 4400
	* Can run up to 4K @ 24 Hz via the HDMI port
* Full hardware acceleration
	* This also includes hardware accelerated decoding and encoding
* Sleep and wake
* Analog audio
	* Internal speaker, microphone and 3.5mm audio jack
* Digital audio
	* HDMI audio works perfectly fine
* Camera
	* Activity light works as well
* Wi-Fi
	* More on that later
* Ethernet
* SD Card reader
* DVD drive
	* Supports both reading and burning
* Backlight
	* You can even turn off the backlight completely

## What doesn't work or has issues
* DRM
	* Anything that relies on hardware DRM doesn't work
* Wi-Fi
	* Network speed is halved, Wi-Fi icon always shows poor reception no matter how close you're to the access point.
* Bluetooth
	* Doesn't work at all.
* AirPlay
	* This is due to the Wireless chip, there's nothing to do about it.
* macOS 11+
	* Can't get it to boot, though people have gotten Monterey working on this model. I'll have to investigate why.
* Wake on USB
	* When the laptop goes to sleep it fully shutdowns every USB port. If you need to wake up the laptop you have to press the power button.

## What I haven't tested yet
* OpenCore GUI
* OpenCore Boot Chime
* Touch
	* I've a broken digitizer
* Power management
	* I've a worn out battery
* Anything related to iServices or continuity between several iDevices
	* I don't have any Apple devices

## Notice
* My `config.plist` has some invalid SMBIOS values, **this is done on purpose**, you'll have to generate your own using [corpnewt's GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)!
	* Guide yourself using what's written on [OpenCore's config.plist Guide](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/haswell.html#platforminfo).
	* Use `MacBookAir8,1` as model when requested.
