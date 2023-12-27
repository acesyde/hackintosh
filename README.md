[![Stars](https://img.shields.io/github/stars/acesyde/hackintosh?label=Stars)](https://github.com/acesyde/hackintosh/stargazers)
[![Forks](https://img.shields.io/github/forks/acesyde/hackintosh?label=Forks)](https://github.com/acesyde/hackintosh/network/members)
[![Release](https://img.shields.io/github/v/release/acesyde/hackintosh?label=Download)](https://github.com/acesyde/hackintosh/releases/latest)

## Contents

| Specifications      | Detail                          |
| ------------------- | ------------------------------- |
| Processor           | Intel Core i5-6500T             |
| Memory              | CT16G4SFD824A 32GB DDR4 2400MHz |
| Motherboard         | Asus Q170T                      |
| macOS Hard Drive    | KXG50ZNV256G TOSHIBA            |
| Others Hard Drives  | 2x 2To CT2000BX500SSD1          |
| Ethernet            | RTL8111 / I219-LM               |
| Audio               | Realtek ALC887                  |
| Integrated Graphics | Intel HD Graphics 530           |
| Monitor 1           | LG 35WN75CP-W                   |

## What works ?

| Service                | State |
| ---------------------- | ----- |
| HDMI                   | ?     |
| DVI                    | ?     |
| Ethernet               | ?     |
| iGPU                   | ?     |
| DRM                    | ?     |
| USB                    | ?     |
| Sleep                  | ?     |
| iCloud                 | ?     |
| iMessage and FaceTime  | ?     |
| Handoff and Continuity | ?     |
| Mac App Store          | ?     |

## Installation

### Make the Installation USB

1. Download [balenaEtcher](https://www.balena.io/etcher/) and the [macOS Big sur 11.0 Image](https://www.olarila.com/topic/6278-olarila-vanilla-images-macos-installer/) (⚠️ It's recommanded to use an Ad Blocker ⚠️).
2. Open balenaEtcher, select the `.raw` image you downloaded earlier, select the USB you want to use and click "Flash".
> **⚠️ THIS WILL ERASE ALL THE DATA PRESENT ON YOUR USB, PLEASE BACKUP IMPORTANTS FILES !**
3. Once the flash is successfully completed, you will need to mount the EFI of your USB (search on Google if you need help).
4. Open the EFI of your USB and **delete everything** (the root of the EFI should be blank).
5. [Download the latest version of this EFI](https://github.com/acesyde/hackintosh/releases/latest) and paste the "EFI" folder at the root of the USB

Finally, your USB is ready but before using it you will have to [Setup the SMBIOS](#setup-the-smbios)

>**⚠️ It will not boot if you skip this part, so make sure to follow the following steps carefully**

### Setup the SMBIOS

To use this EFI, you will need to setup the SMIOS.

1. Download [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) and extract it.
2. Launch the program by executing `GenSMBIOS.bat` if you're on Windows or `GenSMBIOS.command` if you're on macOS.
3. Once the script is running, pick the option 1 for downloading MacSerial.
4. Pick option 3 for selecting the SMBIOS and enter `iMac17,1` (case sensitive).

> This will give you an output similar to the following : 
> 
> ```
> #####################################################
> #              iMac17,1 SMBIOS Info                 #
> #####################################################
> 
> Type:         iMac17,1
> Serial:       C07LNUYMJYVX
> Board Serial: C07345500CDKXPGJC
> SmUUID:       C58DD217-9C50-439D-9D72-E81D99DBB062
> Apple ROM:    903C92E450A1
> ```

5. Check the generated serial number on [Apple Check Coverage](https://checkcoverage.apple.com/). You want to get this message back : "We’re sorry, we’re unable to check coverage for this serial number". If you don't get it, you need to regenerate another serial.
6. Using [ProperTree](https://github.com/corpnewt/ProperTree), modify your `config.plist` file using the output given by GenSMBIOS :
    - The `Type` part gets copied to `Generic -> SystemProductName`.
    - The `Serial` part gets copied to `Generic -> SystemSerialNumber`.
    - The `Board Serial` part gets copied to `Generic -> MLB`.
    - The `SmUUID` part gets copied to `Generic -> SystemUUID`.
    - Don't use the `Apple ROM` part !
    - For `Generic -> ROM`, we use the MAC Address of the network interface, in all lowercase, and without `:`

> **ℹ️ For example :**
> - **MAC :** `00:16:CB:00:11:22`
> - **ROM :** `0016cb001122`
>
>**⚠️ NOTE AND WARNINGS :**
> - You need to have the [latest version of Python](https://www.python.org/downloads/) installed to run GenSMBIOS.
> - You and you alone are responsible for your Apple ID, read the guide carefully and take full responsibility if you screw up. Dortania, me and any other guides are not held accountable for what you do.

### Setup the BIOS
>**ℹ️ NOTE :**
> - All of these options may not be present in your BIOS, it is recommended to match as closely as possible but don't be too concerned if many of these options are not available in your BIOS.
> - It is recommended to change the language of your BIOS to English while configuring it. You can put it back in your preferred language once the changes have been made.

| ❌ You should disable | ✅ You should enable |
|-----------------------|----------------------|
| Fast Boot             | VT-x                 |
| Secure Boot           | Above 4G Decoding    |
| Serial/COM Port       | Hyper-Threading      |
| Parallel Port         | Execute Disable Bit  |
| VT-d                  | EHCI/XHCI Handoff    |
| CSM                   |                      |
| Thunderbolt           |                      |
| Intel SGX             |                      |
| Intel Platform Trust  |                      |
| CFG Lock              |                      |

|                🛠️ Settings you should change              |
|-----------------------------------------------------------|
| **OS Type :** `Windows 8.1/10 UEFI Mode` (or `Other OS`)  |
| **DVMT Pre-Allocated (iGPU Memory) :** `128MB` or higher  |
| **SATA Mode :** `AHCI`                                    |

### Post-Install
1. Mount the EFI of the hard disk on which macOS is installed.
2. Mount the EFI of the USB you used to install macOS.
3. Copy all the contents of the EFI partition from the USB to the EFI of the hard disk where macOS is installed.
> It should look like this :
> ![EFI-directory-Screenshot](/Images/EFI-directory-Screenshot.png)
4. You can now boot directly from your Hard Drive.

## Credits

- Thanks to [Apple](https://apple.com) for [macOS](https://www.apple.com/macos/)
- Thanks to [Acidanthera](https://github.com/acidanthera) for providing [Apple ALC](https://github.com/acidanthera/AppleALC), [CPUFriend](https://github.com/acidanthera/CPUFriend), [CpuTscSync](https://github.com/acidanthera/CpuTscSync), [FeatureUnlock](https://github.com/acidanthera/FeatureUnlock), [IntelMausi](https://github.com/acidanthera/IntelMausi), [Lilu](https://github.com/acidanthera/Lilu), [NVMeFix](https://github.com/acidanthera/NVMeFix), [OpenCore Bootloader](https://github.com/acidanthera/OpenCorePkg), [VirtualSMC](https://github.com/acidanthera/VirtualSMC) and [WhateverGreen](https://github.com/acidanthera/WhateverGreen)
- Thanks to [Dortania](https://github.com/dortania) for providing [AMFIPass](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Acidanthera/AMFIPass-v1.4.0-RELEASE.zip), [CtlnaAHCIPort](https://github.com/dortania/OpenCore-Install-Guide/blob/master/extra-files/CtlnaAHCIPort.kext.zip), [IO80211FamilyLegacy](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Wifi/IO80211FamilyLegacy-v1.0.0.zip), [IOSkywalkFamily](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Wifi/IOSkywalkFamily-v1.0.0.zip) and [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher)
- Thanks to [Olarila](https://www.olarila.com) for providing the [macOS Sonoma 14.0 Image](https://www.mediafire.com/file/wio1f0s9e8bzyiw/Olarila+Sonoma.raw/file)
- Thanks to [Aurélien Audero](https://github.com/AurelienAudero) for building the [Intel i5-7400 Hackintosh EFI](https://github.com/AurelienAudero/Intel-i5-7400-Hackintosh-EFI)

## Need help ?

Click [here](https://github.com/acesyde/hackintosh/issues/new/choose) to create an issue on GitHub.

If you have a question, you can create a thread [here](https://github.com/acesyde/hackintosh/issues/new/choose)