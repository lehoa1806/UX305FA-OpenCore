# UX305FA-CLOVER
Clover EFI bootloader ASUS UX305FA

##  Hardware
* ASUS ZenBook UX305FA
* Intel(R) Core(TM) M-5Y10c
* Intel HD 5300 (1920 x 1080)
* 8 GB Ram
* Wifi and bluetooth: Replaced by Broadcom BCM94352Z
* BIOS version 213

##  Overview
* I am a fan of Linux and I have used Ubuntu, CentOS and openSUSE for around 14
years. Everything is OK before Wireless Headphones era comes. I have three
wireless audio devices and I have been using them all day, every day. That was
why random drops while connecting to Linux were killing me these time. So I
decided to switch to another environment after trying many other flavors of
Linux e.g. Kubuntu and Fedora. And it is definitely the Hackintosh, since I
tried it several times before and it is similar to Linux environment. The most
important thing, NO MORE DROP.
* I have used Mojave for almost a year, for both personal use and work related
(I am a Full Stack Developer). And now is the time to upgrade to Catalina.
This is not a public guide to help people to install Hackintosh to their
devices. It is rather a note for me to reinstall my Hackintosh just in case I
cannot upgrade my laptop to Catalina or it is not suitable for me. So, as
people said, I take my own risk and you should too.

###  What works: (necessity order)
* Keyboard: Function keys - Brightness, audio volumes 
* Touchpad: a bit weird somehow - Triple fingers for right click
* Video: Intel HD 5300
* USB
* Stock USB to Ethernet adapter
* Wifi and bluetooth (BCM94352Z)
* Audio: microphone, internal audio and HDMI audio
* Internal webcam
* Battery: Status and native power management
* Ambient light sensing (Fn + A doesn't work)
* Card reader
* Sleep

###  What doesn't work
* Intel wireless - definitely needs to be replaced
* No other things so far

###  Not tested
* File Vault 2
* Hibernation
* Or any other which I don't need

##  BIOS
* Restore Defaults
* Advanced/VT-d: Disabled
* Advanced/Graphics Configuration/DVMT Pre-Allocated: 128M
* Boot/Fast Boot: Disabled
* Boot/Lauch CMS: Disabled
* Security/Secure Boot Control: Disabled

##  Clover EFI bootloader
###  config.plist:
* We all know where we can get it

###  EFI/CLOVER/ACPI/patched:
* We all know where we can get it

###  EFI/CLOVER/drivers/UEFI: 
* HFSPlus.efi - useful in installing phase
* AptioMemoryFix.efi should be used instead of OsxAptioFix3Drv.efi, it will
help to avoid a lot of frozen boots (my experiences)

##  Kexts:
###  EFI/CLOVER/kexts/Other
* FakeSMC.kext - necessary for upgrading

###  /Library/Extensions
* ACPIBatteryManager.kext
* ACPIDebug.kext
* AirportBrcmFixup.kext
* AppleALC.kext
* ApplePS2SmartTouchPad.kext
* AsusNBFnKeys.kext
* BrcmFirmwareRepo.kext
* BrcmPatchRAM2.kext
* FakeSMC.kext
* Lilu.kext
* USBPorts.kext
* VoodooPS2Controller.kext
* WhateverGreen.kext
<p align="center">
  <img src="https://raw.githubusercontent.com/lehoa1806/UX305FA-CLOVER/master/images/overview-14.6.png">
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/lehoa1806/UX305FA-CLOVER/master/images/geekbench.5.0.2-14.6.png">
</p>
