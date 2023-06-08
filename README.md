# Dell-Precision-7520-OpenCore

### Before you give this EFI a try, make sure you read [this](#UEFI-settings) and [this](#Generating-your-own-serial-and-Editing-ROM)!

This repo includes an OpenCore EFI for the Dell Precision 7520.

Testing on:

Model | Dell Precision 7520
------------- | ---------------
CPU | Intel Core i7-6820HQ
iGPU | Intel HD Graphics 530 (spoofed to HD 630)
dGPU | NVIDIA Quadro M2200 (disabled)
RAM | 32 GB DDR4
WiFi | Intel® Dual Band-Wireless-AC 8265
macOS | Ventura 13.5 Beta

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
- headphone jack (white noise)
- Thunderbolt (untested)
- HDMI (untested)
- Bluetooth Audio (untested)

## UEFI settings

- Parallel Port: Disabled
- Serial Port: Enabled
- Virtualization Support: Enabled
- SATA Operation: AHCI
- Thunderbolt: Disabled
- Secure Boot: Disabled
- Legacy Option ROM: Disabled
- Wake on LAN/WLAN: Disabled

## How to install

Download this repo and place the EFI folder into your internal drive's EFI partition... That's it.

## How to Install macOS Ventura

1. Have a working install of macOS, [download](https://mrmacintosh.com/macos-ventura-13-full-installer-database-download-directly-from-apple/) the full installer package, install it to get the installer app, then make a bootable Installer with `createinstallmedia` by using this command in Terminal `sudo /Applications/Install\ macOS\ Ventura.app/Contents/Resources/createinstallmedia --volume /Volumes/NameOfTheUSB`

After you have created a bootable Installer, copy the EFI folder to the EFI partition of the installer drive and install as usual (GUID Partiton Map; APFS). After the installation, mount the EFI partition of the installed OS and copy the EFI folder to its partition.

## Generating your own serial and Editing ROM

Use GenSMBIOS (https://github.com/corpnewt/GenSMBIOS) to generate a serial for MacBookPro13,3 (Skylake) or 14,3 (Kaby Lake)

use Xcode, ProperTree or any decent plist editor to manually enter the details in the following sections of the config (as shown in the video): (SystemSerialNumber, MLB, and UUID)

https://user-images.githubusercontent.com/59102649/116117179-3ea51200-a6bc-11eb-8a18-a03f7bb5bf1d.mp4

You should also put in your ethernet adapter's MAC address into the ROM section.

## Credits

* [acidanthera](https://github.com/acidanthera) (for OpenCore and the kexts)
* [dortania](https://dortania.github.io/OpenCore-Install-Guide/) (for their awesome guide)
* [OpenIntelWireless](https://github.com/OpenIntelWireless) (for Intel WiFi and Bluetooth)
* [blankmac](https://github.com/blankmac/AlpsHID) (for the APLS I2C TouchPad kext)
