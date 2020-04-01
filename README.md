# UX305FA-CLOVER
Clover EFI bootloader ASUS UX305FA
Calatina 10.15.4 (19E266)

##  Hardware
* ASUS ZenBook UX305FA
* Intel(R) Core(TM) M-5Y10c
* Intel HD 5300 (1920 x 1080)
* 8 GB Ram
* Wifi and bluetooth: Replaced by Broadcom BCM94352Z
* BIOS version 213

##  Overview
Updated to Calatina 10.15.4 (19E266)

Removed these following configurations since I don't use them at all.
The old configurations still work on Catalina.
* Ambient light sensing
* Keyboard: Function keys - Brightness, audio volumes 

###  What works: (necessity order)
* Keyboard
* Touchpad
* Video: Intel HD 5300
* USB
* Stock USB to Ethernet adapter
* Wifi and bluetooth (BCM94352Z)
* Audio: microphone, internal audio and HDMI audio
* Internal webcam
* Battery: Status and native power management
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
* Latest version - 10.15.4 (19E266) requires Clover bootloader 5017 or above

## Install
* Create USB using createinstallmedia method
* Install Clover Bootloader to USB
* Copy VirtualSmc.efi, HFSPlus.efi, apfs.efi from [/drivers]
(https://github.com/lehoa1806/Asus-Maximus-IX-CODE-CLOVER/tree/master/drivers)
to /Clover/drivers/UEFI/

###  EFI/CLOVER/drivers/UEFI: 
* HFSPlus.efi - useful in installing phase
* AptioMemoryFix.efi should be used instead of OsxAptioFix3Drv.efi, it will
help to avoid a lot of frozen boots (my experiences)

##  Kexts:
All kexts were moved to EFI/CLOVER/kexts/Other due to the read-only issue on
Catalina
###  EFI/CLOVER/kexts/Other
* AirportBrcmFixup.kext <- wifi
* AppleALC.kext <- audio
* ApplePS2SmartTouchPad.kext <- touchpad
* BrcmBluetoothInjector.kext <- bluetooth
* BrcmFirmwareData.kext <- bluetooth
* BrcmPatchRAM3.kext <- bluetooth
* Lilu.kext
* SMCBatteryManager.kext <- battery indicator
* VirtualSMC.kext
* WhateverGreen.kext

## Compile kexts

Prepare xcode
```
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```

```
# Unzip kexts in /kexts
mkdir -p ~/workspace/HACKINTOSH/UX305FA/build/kexts
cd ~/workspace/HACKINTOSH/UX305FA/build/kexts
mkdir DEBUG
mkdir RELEASE

# Build DEBUG ========================================================
# Lilu
cd ~/workspace/HACKINTOSH/UX305FA/build
git clone https://github.com/acidanthera/Lilu.git && cd Lilu
xcodebuild -configuration Debug
cp -R build/Debug/Lilu.kext ./../kexts/DEBUG/

# AppleALC
cd ~/workspace/HACKINTOSH/UX305FA/build
git clone https://github.com/acidanthera/AppleALC.git && cd AppleALC
cp -R ../Lilu/build/Debug/Lilu.kext .
xcodebuild -configuration Debug
cp -R build/Debug/AppleALC.kext ./../kexts/DEBUG/

# VirtualSMC
cd ~/workspace/HACKINTOSH/UX305FA/build
git clone https://github.com/acidanthera/VirtualSMC.git && cd VirtualSMC
cp -R ../Lilu/build/Debug/Lilu.kext .
xcodebuild -configuration Debug
cp -R build/Debug/VirtualSMC.kext ./../kexts/DEBUG/
cp -R build/Debug/SMCBatteryManager.kext ./../kexts/DEBUG/

# WhateverGreen
cd ~/workspace/HACKINTOSH/UX305FA/build
git clone https://github.com/acidanthera/WhateverGreen.git && cd WhateverGreen
cp -R ../Lilu/build/Debug/Lilu.kext .
xcodebuild -configuration Debug
cp -R build/Debug/WhateverGreen.kext ./../kexts/DEBUG/

# Build RELEASE ========================================================
# Lilu
cd ~/workspace/HACKINTOSH/UX305FA/build/Lilu
xcodebuild
cp -R build/Release/Lilu.kext ./../kexts/RELEASE/

# AppleALC
cd ~/workspace/HACKINTOSH/UX305FA/build/AppleALC
xcodebuild
cp -R build/Release/AppleALC.kext ./../kexts/RELEASE/

# VirtualSMC
cd ~/workspace/HACKINTOSH/UX305FA/build/VirtualSMC
xcodebuild
cp -R build/Release/VirtualSMC.kext ./../kexts/RELEASE/
cp -R build/Debug/SMCBatteryManager.kext ./../kexts/DEBUG/

# WhateverGreen
cd ~/workspace/HACKINTOSH/UX305FA/build/WhateverGreen
xcodebuild
cp -R build/Release/WhateverGreen.kext ./../kexts/RELEASE/
```
<p align="center">
  <img src="https://raw.githubusercontent.com/lehoa1806/UX305FA-CLOVER/master/images/Catalina_info.png">
</p>
<p align="center">
  <img src="https://raw.githubusercontent.com/lehoa1806/UX305FA-CLOVER/master/images/Catalina_geekbench5.png">
</p>
