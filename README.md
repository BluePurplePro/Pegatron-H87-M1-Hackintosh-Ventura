# Pegatron-H87-M1-Hackintosh-Ventura
This repository and project hosts the files necessary to boot macOS Ventura with OpenCore ~~0.9.9~~ 1.0.3 successfully on the Pegatron H81-M1 motherboard using [Haswell GT2 Graphics](https://wikipedia.org/wiki/Intel_Graphics_Technology#Haswell)
![Pegatron H87-M1](https://github.com/BluePurplePro/Pegatron-H87-M1-Hackintosh-Ventura/assets/84092284/cc48178e-e9e2-4d32-b704-543837fbb600)


# DISCLAIMER
THIS INFORMATION/RESEARCH HAS BEEN DONE AND SHARED PURELY FOR EXPERIMENTAL AND RESEARCH PURPOSES, AND IS IN NO MAY MEANT TO PROMOTE CIRCUMVENTING OF ANYTHING THAT IS SOMEONE ELSE'S CORPORATE PRIVATE PROPERTY. THE INFORMATION LISTED HERE IS PURELY FOR EDUCATIONAL PURPOSES AND SHOULD YOU CHOOSE TO UTILIZE IT IN ANY WAY, I AM IN NO WAY RESPONSIBLE FOR ANY INJUNCTIONS/PROBLEMS THAT MAY OR MAY NOT ARISE AND/OR BE BROUGHT AGAINST ANOTHER FOR THEIR CHOOSING TO HAVE DONE SO.

# Acknowledgements
- https://dortania.github.io/OpenCore-Install-Guide/
- https://dortania.github.io/OpenCore-Legacy-Patcher/

# Deployment
To deploy this project properly, please obtain the EFI folder from this repository, edit the config.plist to **generate new serial number, rom, UUID, etcetera**, then save config.plist, and place the files onto the appropriate ESP EFI partition in order to boot using OpenCore bootloader and proceed with your installation of macOS.

# Documentation
_The hardware in this Machine is as follows_:
- CPU: Intel Core i7-4790 (could be replaced by Core i3/i5)
- GPU: Intel HD Graphics 4600 (included Device-id	Data 12040000 for HD4200 and HD4400)
- Mobo: Pegatron H87-M1
- Memory: 16GB Kingston PC3-12800 (2x8GB)
- Drive: Samsung SSD PM871 mSATA 256GB (111,76GiB for MacOS)
- Wifi & Bluetooth: Intel Dual Band Wireless-AC 3165
- Ethernet: Realtek RTL8111
- Audio: Realtek ALC892 (alcid=18)

# Kernel Extensions corresponding to hardware/utility
| Hardware  | Kext(s) |
| ------------- | ------------- |
| Intel(R) HD Graphics 4400/4600 | [Whatevergreen.kext](https://github.com/acidanthera/WhateverGreen) |
| mSATA SSD | AppleAHCIPort.kext (patching **com.apple.driver.AppleAHCIPort** with find ``40600200``, replace ``00000000`` |
| Realtek Ethernet  | [RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X) |
| Audio Realtek ALC892 | [AppleALC.kext](https://github.com/acidanthera/AppleALC) |


| Utility  | Kext(s) |
| ------------- | ------------- |
| Disabling AMFI | AMFIPass.kext |


# BIOS Settings
- **Advanced**
  - CPU Configuration ~> Virtualization Tech ~> Enabled
  - SATA Configuration ~> SATA Controller Mode ~> AHCI Mode
  - Onboard Devices Settings ~> Serial Port1 Configuartion ~> Disabled
- **Security**
  - Secure Boot ~> Disabled
- **Boot**
  - Launch CSM ~> Disabled

# OCLP
- Download and install [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher)
- Open OCLP and click **Post-Install Root Patch** to patch iGPU
