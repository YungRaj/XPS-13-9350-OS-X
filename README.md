# XPS 13
Current BIOS revision: 1.4.4
This includes the whole CLOVER folder from my XPS 13
(credits to the whole CLOVER team https://sourceforge.net/projects/cloverefiboot/)

The original OEM ACPI tables are included in /ACPI/origin

The patched ACPI tables, only containing the DSDT and SSDT (non-dynamic SSDT’s) are included in /ACPI/patched. My CPU PM SSDT is named SSDT.aml (credits to PikerRAlpha)

DO NOT COPY AND USE, use the patches that I have used recommended on this repo.

# Guide
Comprehensive guide for creating a bootable Clover USB
http://www.insanelymac.com/forum/topic/305255-making-a-10101011-usb-installer-w-clover-uefi-and-legacy-the-correct-way/
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
13. ”Rename HECI device to IMEI"
Note: the battery status patch is not necessary, although there is an XPS 13 patch on RehabMan’s ACPI repository. (https://github.com/RehabMan/Laptop-DSDT-Patch)


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


# Credits
EDK 2 https://github.com/tianocore/edk2
Clover dev team https://sourceforge.net/projects/cloverefiboot/
InsanelyMac forum http://insanelymac.com/forum
PJALM (many ACPI patches)
RehabMan (ACPIBatteryManager, IntelBacklight, etc)
emlydinesh
Download-Fritz
Poco (the goat)

# Resources
http://www.uefi.org
https://sourceforge.net/projects/maciasl/
https://github.com/RehabMan/OS-X-MaciASL-patchmatic
http://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/


