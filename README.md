# XPS 13
Current BIOS revision: 1.4.4
This includes the whole CLOVER folder from my XPS 13
(credits to the whole CLOVER team https://sourceforge.net/projects/cloverefiboot/)

The original OEM ACPI tables are included in /ACPI/origin

The patched ACPI tables, only containing the DSDT and SSDT (non-dynamic SSDT’s) are included in /ACPI/patched. My CPU PM SSDT is named SSDT.aml (credits to PikerRAlpha)

DO NOT COPY AND USE, use the patches that I have used recommended on this repo.

To avoid errors during recompilation of ACPI tables, use the iasl CLI utility to disassemble tables and any refs needed. Also use RehabMan’s fork of MaciASL because the original branch of MaciASL does not include iasl 6.1 which is the current most recent standard of ACPI.

# Guide
Use setup_var to change DVMT prealloc IGPU memory and disable MSR 0xe2 CPU Register lock (also known as CFG Lock)
Usage: (address of BIOS option is different for every machine) <br />
1. Use a UEFI ROM flash dumper such as FPT/AMIFlash to dump UEFI image. Use UEFITool to extract Setup image and Universal IFR Extractor to retrieve BIOS option data. Find CFG Lock and DVMT and determine the address of the BIOS option to change as well as the option to write to NVRAM. <br />
2. Boot into the setup_var shell <br />
3. CFG Lock: setup_var 0x109 0x0 <br />
4. DVMT Prealloc: setup_var 0x432 0x3 <br />
WARNING: any damages or problems with the above commands are not my responsibility. This is for informational purposes only! <br />
<br />
Comprehensive guide for creating a bootable Clover USB
http://www.insanelymac.com/forum/topic/305255-making-a-10101011-usb-installer-w-clover-uefi-and-legacy-the-correct-way/ <br />
Note: patch IOKit for correct pixel clock 
https://github.com/Floris497/mac-pixel-clock-patch-V2

# Patches

1. “Rename GFX0” (DSDT and SSDT-5) 
2. “PNLF backlight”
3. “Skylake LPC”
4. “USB_PRW_0x6D_Skylake”
5. "Fix _WAK Arg0 v2"
6. ”HPET Fix"
7. ”SMBUS Fix"
8. ”IRQ Fix"
9. ”RTC Fix"
10. ”OS Check Fix (Win 8)“
11. ”Fix Mutex with non-zero SyncLevel"
12. ”Fix PNOT/PPNT" (use only if you're dropping CPU related SSDTs)
13. ”Rename HECI device to IMEI" <br />
Note: the battery status patch is not necessary, although there is an XPS 13 patch on RehabMan’s ACPI repository. (https://github.com/RehabMan/Laptop-DSDT-Patch) <br />
<br />
Sleep - if you have HD 530 or higher GFX, enter sudo pmset hibernatemode 25 in Terminal for proper display wake (machine goes to hibernate mode)


# Kexts 

1. FakeSMC.kext
2. IntelBacklight.kext
3. ApplePS2SmartTouchpad.kext
4. ACPIBatteryManager.kext
5. FakePCIID.kext - optional (for BCM94352Z)
6. FakePCIID_BCM94352*.kext - optional (for BCM94352Z)
7. AppleHDADisabler.kext - optional
8. VoodooHDA.kext - optional 
9. patched AppleHDA.kext - optional (choose)
10. Patched IONVMeFamily or HackrNVMeFamily/IONVMeFamilyBorg.kext (see section NVMe)


# NVMe
NVMe hardware only works in OS X for Apple SSDs. For those who do not have an Apple SSD, you have been granted a huge gift from the OSX86 community. NVMe now works on most NVMe compliant hardware with patches provided by PikeRAlpha and a neat script to perform the correct patches by RehabMan. See https://github.com/RehabMan/patch-nvme <br />
The resulting HackrNVMeFamily kext that is created with patch-nvme can be installed alongside IONVMeFamily in LE/SLE or CLOVER kext folder. For faster boot times, I have my kexts in SLE. I do not provide the kext because it is different for each new revision of IONVMeFamily so you must perform the patches yourself with the correct OS X version. The patches are also provided with another tool called NVMeP which has updated patches for macOS Sierra, credits to Mickey1979 (https://github.com/Micky1979/NVMeP)

# Credits
EDK 2 https://github.com/tianocore/edk2 <br />
Clover dev team https://sourceforge.net/projects/cloverefiboot/ <br />
InsanelyMac forum http://insanelymac.com/forum <br />
PJALM (many ACPI patches) <br />
RehabMan (ACPIBatteryManager, IntelBacklight, etc) <br />
emlydinesh <br />
Download-Fritz <br />
Poco (the goat) <br />

# Resources
http://www.uefi.org <br />
https://sourceforge.net/projects/maciasl/ <br />
https://github.com/RehabMan/OS-X-MaciASL-patchmatic <br />
http://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/ <br />


