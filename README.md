# SOFTWARES:
- CPU-Name-Master (Renaming CPU)
- GenSMBios (Generate compatible bios)
- ProperTree or OC Auxiliary Tools (Configure)
- SSDTTime (Gen ACPI)

Inside Mac:
- Hackintool
- ESP Mounter Pro
- OC Auxiliary Tools


Note|Description
:----|:----
Initial macOS Support|macOS 10.12, Sierra.
Last Supported OS|macOS 13 Ventura.

- Opencore version: 1.0.3
- Release date: 03/12/2024

# Basic Steps

1. [Download](https://discord.com/channels/887798875069505587/1184144798312038512) the latest release [Discord, #efi-base channel];
2. Includes **additional** kexts (for ethernet, audio, etc);
3. Include the **necessary** ACPI patches (.aml);
4. Review the special notes;
5. Generate and complete your SMBIOS infos - **ALWAYS**;
6. Adjust your BIOS;
7. Generate FakeID
8. Install macOS and enjoy :)

# Compatible SMBIOS, for Desktop

SMBIOS|Description
:----|:----
iMac18,3|Used for computers using a dGPU for displaying, and an iGPU for computing tasks only.


### GPU-Specific `boot-args`
Parameter|Description
:----|:----
-radcodec| For enabling RX 550 Lexa


# BIOS Settings

### Disable
- Fast Boot
- Secure Boot
- Serial/COM Port
- Parallel Port
- VT-d (can be enabled if you set `DisableIoMapper` to YES)
- Compatibility Support Module (CSM).
- Thunderbolt(For initial install, as Thunderbolt can cause issues if not setup correctly)
- Intel SGX
- Intel Platform Trust
- CFG Lock (MSR 0xE2 write protection)
	- This must be off, if you can't find the option then **`ENABLE`** `AppleXcpmCfgLock`. 
	- Your hack will not boot with `CFG-Lock` enabled.

### Enable
- VT-x
- Above 4G decoding. 
	- This must be on, if you can't find the option then add `npci=0x2000` to `boot-args`. 
	- Do not have both this option and `npci` on `boot-args` enabled at the same time.
- Hyper-Threading
- Execute Disable Bit
- EHCI/XHCI Hand-off
- OS type: Windows 8.1/10 UEFI Mode
- DVMT Pre-Allocated(iGPU Memory): 64MB
- SATA Mode: AHCI

# References
[Desktop, Kaby Lake](https://dortania.github.io/OpenCore-Install-Guide/config.plist/kaby-lake.html)
<br>
[Laptop, Kaby Lake & Amber Lake Y](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/kaby-lake.html)
<br>
[Gabriel Luchina Repository](https://github.com/luchina-gabriel/BASE-EFI-INTEL-7THGEN-KABY-LAKE-PUBLIC/blob/main/README.md?plain=1)
