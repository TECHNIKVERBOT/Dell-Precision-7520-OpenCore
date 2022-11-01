# Dell-Precision-7520-OpenCore
 
### Before you give this EFI a try, make sure you read [this](#Disabling-CFG-Lock) and [this](#Generating-your-own-serial-and-Editing-ROM)!

This repo includes an OpenCore EFI for the Dell Precision 7520.

Testing on:

Model | Dell Precision 7520
------------- | ---------------
CPU | Intel Core i7-6820HQ
iGPU | Intel HD Graphics 530 (spoofed to HD 630)
dGPU | NVIDIA Quadro M2200 (disabled)
RAM | 32 GB DDR4
WiFi | Intel® Dual Band-Wireless-AC 8265
macOS | Ventura 13.0

## What works?

- Audio
- Battery readout
- Boot
- Brightness Control
- Ethernet
- GPU acceleration
- Keyboard + Trackpad
- Power Management
- SD card reader
- WiFi
- Bluetooth
- Sleep
- USB
- Webcam
- Speaker
- Trackpoint

## What doesn't work?

- dGPU (no support past High Sierra)
- headphone jack
- Thunderbolt (untested)

## BIOS settings

- Virtualization Support: Enabled
- SATA Mode: AHCI
- Thunderbolt: Disabled
- Legacy Mode: Disabled

## How to install

Download this repo and place the EFI folder into your internal drive's EFI partition... That's it.

## How to Install macOS Ventura Beta

1. Have a working install of macOS, [download](https://mrmacintosh.com/macos-ventura-13-full-installer-database-download-directly-from-apple/) the full installer package, install it to get the installer app, then make a bootable Installer with `createinstallmedia` by using this command in Terminal `sudo /Applications/Install\ macOS\ Ventura\ beta.app/Contents/Resources/createinstallmedia --volume /Volumes/NameOfTheUSB`

After you have created a bootable Installer, copy the EFI folder to the EFI partition of the installer drive and install as usual (GUID Partiton Map; APFS). After the installation, mount the EFI partition of the installed OS and copy the EFI folder to its partition.

## Disabling CFG-Lock

In order for macOS to boot at all, you'll need to disable CFG-Lock.
To do that, boot the EFI, press Space and select modGRUBShell.efi

From there type this command: setup_var 0x4ED 0x00

To confirm CFG-Lock has been disabled, boot back into OpenCore and ControlMsrE2.efi and verify the firmware has an unlocked register present

## Generating your own serial and Editing ROM

Use GenSMBIOS (https://github.com/corpnewt/GenSMBIOS) to generate a serial for MacBookPro13,3

use Xcode, ProperTree or any decent plist editor to manually enter the details in the following sections of the config (as shown in the video): (SystemSerialNumber, MLB, and UUID)

https://user-images.githubusercontent.com/59102649/116117179-3ea51200-a6bc-11eb-8a18-a03f7bb5bf1d.mp4

You should also put in your ethernet adapter's MAC address into the ROM section.

## Credits

* [acidanthera](https://github.com/acidanthera) (for OpenCore and the kexts)
* [dortania](https://dortania.github.io/OpenCore-Install-Guide/) (for their awesome guide)
* [OpenIntelWireless](https://github.com/OpenIntelWireless) (for Intel WiFi and Bluetooth)
* [blankmac](https://github.com/blankmac/AlpsHID) (for the APLS I2C TouchPad kext)
