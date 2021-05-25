# macOS on Thinkpad X1 Carbon 7th Generation, Model 20R1\*

[![macOS](https://img.shields.io/badge/macOS-Big_Sur-yellow.svg)](https://www.apple.com/macos/big-sur/)
[![version](https://img.shields.io/badge/11.2.3-yellow)](https://www.apple.com/newsroom/2020/11/macos-big-sur-is-here/)
[![MODEL](https://img.shields.io/badge/Model-20R1*-blue)](https://github.com/huyhoang8398/x1c7-hackintosh-20r1/blob/master/docs/references/ThinkPad_X1_Carbon_7th_Gen_Spec.PDF)
[![OpenCore](https://img.shields.io/badge/OpenCore-0.6.9-green)](https://github.com/acidanthera/OpenCorePkg)

<img align="right" src="https://github.com/huyhoang8398/x1c7-hackintosh-20r1/blob/master/docs/Images/preview.png" alt="x1c7 thinkpad hackintosh Bigsur" width="300">

### Follow my website [dohoang.me](https://dohoang.me/)

#### READ THE ENTIRE README.MD BEFORE YOU START.

#### I am not responsible for any damages you may cause.

### Should you find an error, or improve anything, be it in the config itself or in the my documentation, please consider opening an issue or a pull request to contribute.

`I AM A ONE MAN TEAM, AND A FULL TIME STUDENT. SO, I MIGHT NOT BE ABLE TO RESPOND OR HELP YOU IN A TIMELY MANNER. BUT, I PROMISE I WILL GET TO YOU EVENTUALLY. PLEASE UNDERSTAND.`
`Lastly, if my work here helped you. Please consider donating, it would mean a lot to me.`

<details>
<summary><strong> SUMMARY </strong></summary>
<br>

> ### Non-Fuctional:
| Feature                              | Status | Dependency          | Remarks                      |
| :----------------------------------- | ------ | ------------------- | ---------------------------- |
| Fingerprint Reader   | ❌ | `DISABLED` in BIOS to save power if not used in other OSes.   | Linux support was only recently added    |
| Wireless WAN         | ❌ | `DISABLED` in BIOS to save power if not used in other OSes.   | Unable to investigate as I have no need and my model did not come with WWAN. |
| Internal Microphone         | ❌ | `DISABLED` in BIOS to save power   | - |

> ### Video and Audio
| Feature                              | Status | Dependency          | Remarks                      |
| :----------------------------------- | ------ | ------------------- | ---------------------------- |
| Full Graphics Accleration (QE/CI)    | ✅   | `WhateverGreen.kext`                   | -   |
| Audio Recording                      | ✅   | `AppleALC.kext` with Layout ID = 71    | -   |
| Audio Playback                       | ✅   | `AppleALC.kext` with Layout ID = 71    | -   |
| Automatic Headphone Output Switching | ✅   | `AppleALC.kext` with Layout ID = 71    | -   |

> ### Power, Charge, Sleep and Hibernation
| Feature                              | Status | Dependency          | Remarks                      |
| :----------------------------------- | ------ | ------------------- | ---------------------------- |
| Battery Percentage Indication | ✅    | `SSDT-Battery.aml` and `/patches/OpenCore Patches/Battery.plist`             | 
| CPU Power Management (SpeedShift)    | ❌     | - | Implement soon
| iGPU Power Management        | ✅ | `XCPM`, enabled by `SSDT-PLUG.aml`                   | 
| NVMe Drive Battery Management | ✅     | `NVMeFix.kext`  | In my experience, NVMe drives will drain more power than SATA drives.           |
| S3 Sleep/ Hibernation Mode 3 | ✅ | `SSDT-SLPWAK.aml` | |
| Custom Charge Threshold      | ✅ | `SSDT-ECRW.aml`, [YogaSMC.kext](https://github.com/zhen-zen/YogaSMC), and [YogaSMCPane](https://github.com/zhen-zen/YogaSMC)| Adjust with YogaSMCPane in System Preferences
| Fan Control                  | ✅ | `SSDT-ECRW.aml`, [YogaSMC.kext](https://github.com/zhen-zen/YogaSMC), and [YogaSMCPane](https://github.com/zhen-zen/YogaSMC)| Adjust with YogaSMC App.
| Battery Life                 | ✅ | Native, comparable to Windows/Linux. Biggest impact is TB3| - |

> ### Input/ Output
| Feature                              | Status | Dependency          | Remarks                      |
| :----------------------------------- | ------ | ------------------- | ---------------------------- |
| WiFi                                       | ✅ | AirportIltwm  | -       |
| Bluetooth                                  | ✅ | AirportIltwm, IntelBluetoothFirmware.kext and IntelBluetoothInjector.kext | ⚠️ audio input (e.g. of headset) is not working 
| Ethernet                                   | ✅ | `IntelMausi.kext` | -                  |
| HDMI hotplug                               | ✅ |- | - |
| USB 2.0, USB 3.0 | ✅ | -   | -     |
| USB 3.1                                    |  ✅  | -   | Hotplug     |
| USB Power Properties in macOS              | ✅ | -    | -     |
| Thunderbolt 3 Hotplug                      | ✅ | -    | Native interface within System Report   |

> ### Display, TrackPad, TrackPoint, and Keyboard
| Feature                              | Status | Dependency          | Remarks                      |
| :----------------------------------- | ------ | ------------------- | ---------------------------- |
| Brightness Adjustments | ✅  | `WhateverGreen.kext`, `SSDT-PNLF-CFL.aml`, `AppleBacklightSmoother.kext`, and `BrightnessKeys.kext`| `AppleBacklightSmoother.kext` is optional for smoother birghtness adjustments |
| TrackPoint             | ✅  | `VoodooPS2Controller.kext`                                      | -       |
| TrackPad               | ✅  | `VoodooPS2Controller.kext`  | - |
| Built-in Keyboard      | ✅  | `VoodooPS2Controller.kext` | - |
| Multimedia Keys        | ✅  | `BrightnessKeys.kext` and [YogaSMC](https://github.com/zhen-zen/YogaSMC) | `YogaSMC` is recommended and preferred over ThinkpadAssisstant  | 

> ### macOS Continuity
| Feature                              | Status | Dependency          | Remarks                      |
| :----------------------------------- | ------ | ------------------- | ---------------------------- |
| iCloud, iMessage, FaceTime | ✅ | Whitelisted Apple ID, Valid SMBIOS   | See [dortania /OpenCore-Install-Guide](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html)  |
| Continuty              | ❌    | Not yet test | - |
| AirDrop                | ❌     | Not yet test |- |
| Sidecar                | ❌     | Not yet test ( donate me to buy an Ipad | - |
| FileVault              | ✅ | as configured in `config.plsit` per [Dortania's Post-Install](https://dortania.github.io/OpenCore-Post-Install/universal/security/filevault.html)|  |
| Time Machine           | ✅     | Native | TimeMachine only backups your Macintosh partition. Manually backup your EFI partition using another method.  |

</details>

<details>
<summary><strong> REFERENCES </strong></summary>
<br>

* Read these before you start:
- [dortania's Hackintosh guides](https://github.com/dortania)
- [dortania's OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [dortania's OpenCore Post Install Guide](https://dortania.github.io/OpenCore-Post-Install/)
- [dortania/ Getting Started with ACPI](https://dortania.github.io/Getting-Started-With-ACPI/)
- [dortania/ opencore `multiboot`](https://github.com/dortania/OpenCore-Multiboot)
- [dortania/ `USB map` guide](https://dortania.github.io/OpenCore-Post-Install/usb/)
- [WhateverGreen Intel HD Manual](https://github.com/acidanthera/WhateverGreen/blob/master/Manual/FAQ.IntelHD.en.md)
- `Configuration.pdf` and `Differences.pdf` in each `OpenCore` releases.
- Additionally, references specific to the x1c7 are located in `docs/references/`

* ### No seriously, please read those.
</details>

<details>
<summary><strong> REQUIREMENTS </strong></summary>
<br>

- A macOS machine(optional): to create the macOS installer.
- Flash drive, 12GB or more, for the above purpose.  
- Xcode works fine for editing plist files on macOS, but I prefer [PlistEdit Pro](https://www.fatcatsoftware.com/plisteditpro/).  
- [ProperTree](https://github.com/corpnewt/ProperTree) if you need to edit plist files on Windows.  
- [MaciASL](https://github.com/acidanthera/MaciASL), for patching ACPI tables and editing ACPI patches.
- [MountEFI](https://github.com/corpnewt/MountEFI) to quickly mount EFI partitions.  
- [IORegistryExplorer](https://developer.apple.com/downloads), for diagnosis.  
- [Hackintool](https://www.insanelymac.com/forum/topic/335018-hackintool-v286/), for diagnostic ONLY, Hackintool should not be used for patching, it is outdated.
- Patience and time, especially if this is your first time Hackintosh-ing.

</details> 


<details>
<summary><strong> HARDWARE </strong></summary>
<br>
- These are relevant components on my machine which may differ from yours, keep these in mind as you will need to adjust accordingly, depending on your machine's configuration.

| Category  | Component                            | Remarks |
| --------- | ------------------------------------ | ------------ |
| CPU       | [i5-10210U](https://ark.intel.com/content/www/us/en/ark/products/195436/intel-core-i5-10210u-processor-6m-cache-up-to-4-20-ghz.html) | - |
| SSD       |  WDC PC SN730 SDBQNTY-512G-1001        | - |
| Display   | 14.0" (355mm) FHD (1920x1080)   | -|
| WWAN      | None | Unless needed in other OSes, disable at BIOS to save power
| Ports       | 2x USB 3.1 Gen 1 (Right USB Always On) |
|                  | 2x USB 3.1 Type-C Gen 2 / Thunderbolt 3 (Power Delivery and DisplayPort) [Max 5120x2880 @60Hz] |
|                  | HDMI 1.4b (Max 4096x2160 @24Hz) |                 |
| Ethernet    | via ThinkPad Ethernet Extension Adapter Gen 2: I219-LM Ethernet (vPro) |
| WLAN + BT    | Intel Wireless-AC 9560, Wi-Fi 2x2 802.11ac + Bluetooth 5.0 |
| WWAN(optional) | Nothing else supported, no adapters, nothing. Locked by BIOS |
| Camera       | IR and HD720p camera with ThinkShutte. Chicony manufacturer |
| Audio       | Realtek ALC3286 codec <br> Linux: ``Realtek ALC285``, layout 11, 21, 31 ; [@acidanthera/AppleALC > Supported codecs [Github]](https://github.com/acidanthera/AppleALC/wiki/Supported-codecs) |
| Fingerprint reader | ✔️ |
| NFC (optional) | ✔️ |


- Refer to [/docs/references/](https://github.com/huyhoang8398/x1c7-hackintosh-20r1/blob/master/docs/references/ThinkPad_X1_Carbon_7th_Gen_Spec.PDF) for possible stock ThinkPad X1 7th Gen configurations.

</details> 

<details>
<summary><strong> GETTING STARTED </strong></summary>
<br>

Before you do anything, please familiarize yourself with basic Hackintosh terminologies and the basic Hackintosh process by throughly reading Dortania guides as linked in `REFERENCES`

- Creating a macOS installer: refer to [Dortania's OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/)
- [**1_README-HARDWAREandBIOS**](https://github.com/huyhoang8398/x1c7-hackintosh-20R1/blob/master/docs/1_README-HARDWAREandBIOS.md): Requirements before installing.  
- Updating
</details> 

> ## CONTACT

https://dohoang.me

> ## SUPPORT

<details>
<summary><strong> CREDITS </strong></summary>
<br>

- [@zhen-zen](https://github.com/zhen-zen) for YogaSMC

The greatest thank you and appreciation to the [Acidanthera](https://github.com/acidanthera) team.

And to everyone else who supports and uses my project.

Please let me know if I missed you.

</details> 