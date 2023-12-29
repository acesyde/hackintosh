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


### Setup the BIOS
>
>**ℹ️ NOTE :**
>
> - All of these options may not be present in your BIOS, it is recommended to match as closely as possible but don't be too concerned if many of these options are not available in your BIOS.
> - It is recommended to change the language of your BIOS to English while configuring it. You can put it back in your preferred language once the changes have been made.

| ❌ You should disable | ✅ You should enable |
| -------------------- | ------------------- |
| Fast Boot            | VT-x                |
| Secure Boot          | Above 4G Decoding   |
| Serial/COM Port      | Hyper-Threading     |
| Parallel Port        | Execute Disable Bit |
| VT-d                 | EHCI/XHCI Handoff   |
| CSM                  |                     |
| Thunderbolt          |                     |
| Intel SGX            |                     |
| Intel Platform Trust |                     |
| CFG Lock             |                     |

| 🛠️ Settings you should change                             |
| -------------------------------------------------------- |
| **OS Type :** `Windows 8.1/10 UEFI Mode` (or `Other OS`) |
| **DVMT Pre-Allocated (iGPU Memory) :** `128MB` or higher |
| **SATA Mode :** `AHCI`                                   |


## Credits

- Thanks to [Apple](https://apple.com) for [macOS](https://www.apple.com/macos/)
- Thanks to [Acidanthera](https://github.com/acidanthera) for providing [Apple ALC](https://github.com/acidanthera/AppleALC), [CPUFriend](https://github.com/acidanthera/CPUFriend), [CpuTscSync](https://github.com/acidanthera/CpuTscSync), [FeatureUnlock](https://github.com/acidanthera/FeatureUnlock), [IntelMausi](https://github.com/acidanthera/IntelMausi), [Lilu](https://github.com/acidanthera/Lilu), [NVMeFix](https://github.com/acidanthera/NVMeFix), [OpenCore Bootloader](https://github.com/acidanthera/OpenCorePkg), [VirtualSMC](https://github.com/acidanthera/VirtualSMC) and [WhateverGreen](https://github.com/acidanthera/WhateverGreen)
- Thanks to [Dortania](https://github.com/dortania) for providing [AMFIPass](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Acidanthera/AMFIPass-v1.4.0-RELEASE.zip), [CtlnaAHCIPort](https://github.com/dortania/OpenCore-Install-Guide/blob/master/extra-files/CtlnaAHCIPort.kext.zip), [IO80211FamilyLegacy](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Wifi/IO80211FamilyLegacy-v1.0.0.zip), [IOSkywalkFamily](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Wifi/IOSkywalkFamily-v1.0.0.zip) and [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher)
- Thanks to [Olarila](https://www.olarila.com) for providing the [macOS Sonoma 14.0 Image](https://www.mediafire.com/file/wio1f0s9e8bzyiw/Olarila+Sonoma.raw/file)
- Thanks to [Aurélien Audero](https://github.com/AurelienAudero) for building the [Intel i5-7400 Hackintosh EFI](https://github.com/AurelienAudero/Intel-i5-7400-Hackintosh-EFI)