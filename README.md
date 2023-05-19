There are some differences in the onboard wireless card between revisions of this motherboard:
* ddr4 rev 1.0：     Intel AX201
* ddr4 rev 1.1/1.2： Intel AX200
* ddr4 rev 1.3/1.4： Intel AX210(Wi-Fi 6E)
* ddr4 V2 rev 1.0:   Intel Ax210(Wi-Fi 6E)
![R23](cinabench.png)

## Notice:
1. The EFI also supports `Z690 Aorus Elite ddr4` , but the onboard network card is blocked by me
using SSDT-DAX200.aml, this SSDT is only applicable to the ax version, so `Z690 Aorus Elite ddr4`
needs SSDT-DAX200.aml turn off.
2. The USB port of the Z690 Aorus Elite/Elite AX ddr5 has a slight difference and is not recommended.
## My configuration
| Components | Model |
| --- | --- |
| CPU | 12th Gen Intel(R) Core(TM) i7-12700K |
| Motherboard | Gigabyte Z690 Aorus Elite AX DDR4 v1.4 |
| OpenCore Version | 0.9.1 |
| macOS version | macOS Monterey 13.2.1 (22D68) |
## What things work?
1. Almost all
## What doesn't work?
1. Sleep works conditionally, see [Known Issues] (#Known Issues) .
2. There are some problems with Bluetooth after wake-up, see [Bluetooth problem after wake-up]
(#Bluetooth problem after wake-up) .
3. Since the core display of the 12th and 13th generation CPUs cannot be driven normally, the
accompanying flight is not available.
## Update log
### 2022-04-22
1. AppleALC.kext v1.8.0 -> v1.8.1。
2. RestrictEvent.kext v1.0.9 -> v1.1.0。
3. BrcmFirmwareData.kext v2.6.4 -> v2.6.5。
4. BrcmPatchRAM3.kext v2.6.4 -> v2.6.5。
5. BlueToolFixup.kext v2.6.4 -> v2.6.5。
6. OpenCore v0.9.0 -> v0.9.1。
### 2022-03-11
1. Update AppleALC.kext to v1.8.0.
2. Update RadeonSensor.kext to v0.3.3.
3. Update SMCRadeonGPU.kext to v0.3.3.
4. Update SMCProcessor.kext to v1.3.1.
5. Update SMCSuperIO.kext to v1.3.1.
6. Update VirtualSMC.kext to v1.6.4.
7. Update Lilu.kext to v1.6.4.
8. Update WhateverGreen.kext to v1.6.4.
9. Update OpenCore to v0.9.0.
10. Found a solution for [Known Issue #1] (#Known Issue) , need to set `Aperture Size` to 1024MB
in BIOS . Solution from: https://www.tonymacx86.com/threads/gigabyte-z690-aero-g-i5-12600k-amdrx-6800-xt.317179/page-236#post-2361924
### 2022-01-07
1. Update Lilu.kext to v1.6.3.
2. Update WhateverGreen.kext to v1.6.3
3. Update AppleALC.kext to v1.7.8
4. Add two amls for turning off sleep, which are not turned on by default. When using it, you
need to tick the two patches of S3/S4-disable.aml and _S3/4 to XS3/4.
### 2022-01-05
1. ADBG is no longer required.
2. Fix the conflict caused by duplication of MCHC devices, and now all SSDTs are loaded
correctly.
3. Update OpenCore to v0.8.8.