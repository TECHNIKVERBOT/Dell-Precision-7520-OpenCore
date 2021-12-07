# Dell-Precision-7520-OpenCore
 
### WICHTIG: Lest und führt den [Abschnitt](#Erstellung-einer-eigenen-Seriennummer) durch, bevor ihr euch an die Konfiguration wagt!

Diese Repository enthält eine OpenCore EFI-Konfiguration für ein Dell Precision 7520 (i7-6820HQ, Skylake).

Getestet auf:

Model | Dell Precision 7520
------------- | ---------------
CPU | Intel Core i7-6820HQ
iGPU | Intel HD Graphics 530
dGPU | NVIDIA Quadro M2200 (deaktiviert)
RAM | 32 GB DDR4
WiFi | Intel® Dual Band-Wireless-AC 8265
macOS | Monterey

## Was funktioniert?

- Ton
- Akkuanzeige
- Boot
- Helligkeitskontrolle
- Ethernet
- Grafikbeschleunigung
- Tastatur + Trackpad
- Power Management
- SD-Kartenleser
- WLAN
- Bluetooth
- Sleep
- USB
- Webcam
- Lautsprecher
- Trackpoint

## Was funktioniert nicht?

- dedizierte Grafikeinheit (NVIDIA Maxwell+ wird seit Mojave nicht mehr unterstützt)
- Klinkenanschluss
- Thunderbolt (nicht getestet)

## BIOS-Einstellungen

- Virtualization Support: Enabled
- SATA Mode: AHCI
- Thunderbolt: Disabled
- TPM: Disabled
- Legacy Mode: Disabled

## Installation

Konfiguration herunterladen und den EFI-Ordner auf die EFI Partition des Speichermediums kopieren, wo sich macOS befindet.

## macOS Monterey installieren

Es gibt zwei Wege zum Kreieren eines Installationsstick:

1. Bei einer vorhandenen macOS-Installation muss lediglich der Installer aus dem App Store heruntergeladen werden und mit dem Befehl `createinstallmedia` im Terminal auf einen USB Stick mit mind. 16 GB untergebracht werden: `sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

2. Windows-Nutzer müssen sich mit [macrecovery.py](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/winblows-install.html) vom OpenCore-Paket bedienen.

Nach der Erstellung muss der EFI-Ordner auf die EFI-Partition des Installationsmediums kopiert werden und schon kann die Installation von macOS durchgeführt werden. Nach der Installation muss die EFI-Partition der SSD/HDD, worauf macOS installiert wurde, eingehängt und der EFI-Ordner dort eingefügt werden.

## Erstellung einer eigenen Seriennummer

Für's Generieren einer eigenen Seriennummer wird GenSMBIOS (https://github.com/corpnewt/GenSMBIOS) eingesetzt. Als SMBIOS wird MacBookPro13,3 angegeben.

Für das Eintragen der im Video folgenden Daten eignet sich ein Plist-Bearbeitungsprogramm wie PlistEdit Pro oder ProperTree (SystemSerialNumber, MLB, and UUID)

https://user-images.githubusercontent.com/59102649/116117179-3ea51200-a6bc-11eb-8a18-a03f7bb5bf1d.mp4

Die MAC-Adresse der internen Netzwerkkarte des Notebooks sollte ebenfalls angegeben werden.

## Credits

* [acidanthera](https://github.com/acidanthera) (for OpenCore and the kexts)
* [dortania](https://dortania.github.io/OpenCore-Install-Guide/) (for their awesome guide)
* [OpenIntelWireless](https://github.com/OpenIntelWireless) (for Intel WiFi and Bluetooth)
* [blankmac](https://github.com/blankmac/AlpsHID) (for the APLS I2C TouchPad kext)
