 Supported Codecs w/ boot-args
    Though Dortania's only has guide's listing up to comet-lake, Alder Lake && the Z-690 are not as far removed as, let's say, a Z-390 and a Z-590 mainboard.
    Biggest differences between the two motherboards are (sometimes) the ethernet port, amount/generation USB ports (690 w/ usb-c && thunderbolt), and the socket.
        12700k hybrid architecture *shouldn't* affect the run-of-the-mill components that MSI slaps onto it's boards.

# ProperTree -> [path to bootdrive usb]\EFI\OC\config.plist -> (..\PlatformInfo)

# PlatformInfo
    (https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html#platforminfo)

         As this is the path of least resistance while still educating, I'll be building with CorpNewt's GenSMBIOS application.
        (https://github.com/corpnewt/GenSMBIOS).

# Main SMBIOS used for Comet Lake:

    ## SMBIOS	Hardware
    ## iMac20,1	i7-10700K and lower(ie. 8 core and lower)
    ## iMac20,2	i9-10850K and higher(ie. 10 core)

        ###Run GenSMBIOS, pick option 1 for downloading MacSerial and Option 3 for selecting out SMBIOS. This will give us an output similar to the following:

# UEFI - bootargs
    (https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html#uefi)

    ConnectDrivers: YES
        Forces .efi drivers, change to NO will automatically connect added UEFI drivers. This can make booting slightly faster, but not all drivers connect themselves. E.G. certain file system drivers  may not load.

# Drivers
    ## Add your .efi drivers here
        * ONLY DRIVERS THAT SHOULD BE HERE:
            HfsPlus.efi
            OpenRuntime.efi

# APFS
        (https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html#apfs)
        
    By default, OpenCore only loads APFS drivers from macOS Big Sur and newer. If you are booting macOS Catalina or earlier, you may need to set a new minimum version/date. Not setting this can result in OpenCore not finding your macOS partition!
    
    macOS Sierra and earlier use HFS instead of APFS. You can skip this section if booting older versions of macOS.