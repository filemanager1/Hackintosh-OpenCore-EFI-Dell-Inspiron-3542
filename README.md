## Hackintosh on the Dell Inspiron 15 3542
Repository containing files necessary to run macOS Catalina on the Dell Inspiron 15 3542, I would **NOT** recommend using this as your daily driver!

<p align="center">
	<img  src="https://github.com/filemanager1/Hackintosh-OpenCore-EFI-Dell-Inspiron-3542/blob/main/Unrelated/Laptop.png?raw=true"  alt="Your Hackintosh will look like this!"/>
</p>

## Hardware configuration
Your laptop should have specifications similar to the one listed in the table below for this to be compatible, if you laptop has a dGPU or a different wireless card you'll have to configure it yourself, **no support is provided at all**.

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
* macOS Catalina (10.15.7)
* Keyboard
* Touchpad
* USB ports
	* Two 2.0 USB ports and one 3.0 USB port
* iGPU - Intel HD 4400
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
* Wi-Fi
	* Network speed is halved, Wi-Fi icon always shows poor reception no matter how close you're to the access point.
* Bluetooth
	* Doesn't work at all.
* AirPlay
	* Doesn't work at all.
* Wake on USB
	* Thanks to the DVD drive, the laptop won't suspend if you enable "USB Wake Support" on the BIOS; so we have to disable it.
	* This causes the laptop to fully shut down **every** USB port. If you need to wake up the laptop you have to press the power button.

## What I haven't tested yet
* Touch
	* I've a broken digitizer
* Anything related to iServices or continuity between several iDevices
	* I don't have any Apple devices

## If you plan on using this, read this first
* To get sleep and wake working properly you have to make some changes in the BIOS. Go to the Advanced tab and make sure your settings look like what I've written below:
	* Intel(R)SpeedStep(TM): **Enabled**
	* Integrated NIC: **Enabled**
	* Virtualization: **Enabled**
	* USB Emulation: **Disabled**
	* USB Wake Support: **Disabled**
	* SATA Operation: **AHCI**

* There's also one small setting you have to change in Miscellaneous Devices:
	* External USB Ports: **Enabled**
	* USB debug: **Disabled**

* My `config.plist` has some invalid SMBIOS values, **this is done on purpose**, you'll have to generate your own using [corpnewt's GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)!
	* Guide yourself using what's written on [OpenCore's config.plist Guide](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/haswell.html#platforminfo).
	* Use `MacBookAir6,1` as model when requested.
