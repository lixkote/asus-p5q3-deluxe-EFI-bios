# ASUS P5Q3 Deluxe – UEFI BIOS Port (Aptio 4)

Port of the beta Aptio 4 UEFI BIOS (rev. 0221) from the **ASUS P5Q Deluxe** (DDR2) to the **ASUS P5Q3 Deluxe** (DDR3).
<p align="left">
    <img src="https://raw.githubusercontent.com/lixkote/asus-p5q3-deluxe-EFI-bios/refs/heads/main/splash.png">
</p>

>  **Use at your own risk.** Flash only if you have a way to recover the BIOS chip (e.g. a programmer or a hot-swappable chip).
> (There are 2 bios chips on that board, you can only flash this on one of them with a programmer like CH341a, and remove + store the other one somewhere safely as a original backup)

## General info:
- This bios completely eliminated POST issues on high amounts of ram (16gb) for me, fixed stability issues, and greatly improved modern GPU compatibility (Even an RTX3050 boots now)
- Includes a power-cycle fix which makes the UEFI much more stable and eliminates boot issues that were present on original P5Q Deluxe beta UEFI
- Xeon CPUs with a 771 conversion are 100% supported and working
- Overclocking was not tested, because this is a old rare board and i don't want to risk it nor do i need oc...

## Changes

Base: `P5Q-ASUS-DELUXE-EFI-0221.ROM` (P5Q Deluxe beta UEFI from asus's website).

**- Rebranded all references of "P5Q Deluxe" to "P5Q3 Deluxe", even on the bootlogo which i custom designed based on the original P5Q Deluxe/EFI one**
- SMBIOS reports correct motherboard model
- Replaced the CSMCore, MemDetect modules with the one from the **MSI P45D3**, so the bios recorgnises DDR3 ram.
- OCMR_PEI removed so that MSI's bios parts are compatible, plus other EFI modules patched.
- Removed **ASUS Express Gate** (that crappy limited linux distro that boots before bios), because it is in my opinion completely useless in 2026 and only caused hangs sometimes...
- Added an option in setup to disable the WiFi module as in the original bios of P5Q3 Deluxe.
- Restart POST issue fix - rebooting now does a full power-cycle reset:
  - the ACPI reset value is `0x0E` instead of `0x06`;
  - the cold and warm reset paths in `SBRun` and `Runtime` also do a full reset.
  - This fixes the hang on reboots (POST code `4645`) that the original P5Q Deluxe EFI had too and made it basically unusable
 

## Notes:
some patching was done with the help of [claude](https://www.anthropic.com/claude)
...so yeah, you can call it vibecoded but i'm happy my motherboard is actually more useful and stable now lmao.
Sharing it, because other owners of this board might find it useful.
