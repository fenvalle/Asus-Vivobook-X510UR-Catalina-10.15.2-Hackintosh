# Asus Vivobook X510URR-BT378Q

![Alt text](https://ivanov-audio.com/wp-content/uploads/2014/01/Hackintosh-Featured-Image.png)

## System specification

1. Name:           Asus Vivobook X510URR-BT378Q
2. CPU:            Intel Core i5-8250U
3. Graphics:       Intel UHD Graphics 620 // Dual monitor with HDMI (Index 2) and 1536 MB VRAM
4. Wifi:           Intel Dual Band Wireless-AC 8265 - with bluetooth // Tp-link AC600 Nano USB
5. Card Reader:    Connected via USB
6. Camera:         ASUS UVC HD
7. Audio:          Conexant Audio CX8050
8. Touchpad:       ELAN1200
9. Bios Version:   309

## Steps to install

1. Prepair a macOS installer in USB (Use creationmedia method or MBR HFS Firmware Check Patch available in https://www.insanelymac.com/forum/files/file/985-catalina-mbr-hfs-firmware-check-patch/ for both Mojave and Catalina).
2. Replace EFI folder in USB EFI partition with the EFI folder in Clover EFI.
3. Boot into USB and select macOS installer.
4. During the installation, touchpad does not work. You need a mouse connected through USB. (Or you may delete the IOGraphicsFamily dependency from VoodooI2CHID.kext/info.plist.) Follow installation instructions found on tonymacx86 or other hackintosh forums.
    - If you have chosen to install Catalina in HFS+ file system, follow the directions given in https://www.insanelymac.com/forum/files/file/985-catalina-mbr-hfs-firmware-check-patch/
5. After a successful installation, boot into macOS, copy kexts In /kexts/Other -> /Library/Extension.
6. Use Kext Utility (or simply copy this line without the quotation marks: "sudo chmod -R 755 /L*/E*&&sudo chown -R 0:0 /L*/E*&&sudo kextcache -i /") to rebuild kext cache then reboot.
    - If you have installed Catalina, use Hackintool to disable Gate Keeper beforehand. http://headsoft.com.au/download/mac/Hackintool.zip.
7. Now the touchpad and sound input should function correctly. You need to mount EFI and copy Clover EFI to the system EFI partition in like what you have done on USB EFI partition.
8. After System EFI replaced by your EFI, use Clover Configurator to change SMBIOS, generate your serial and MBL.
- Note: You may want to complete these extra steps.
    - You have not replaced the WiFi & BT module with DW1560 but want to have working iMessage and FaceTime with USB WiFi dongle or USB LAN -- Install RehabMan's Null Ethernet

## Install RehabMan's Null Ethernet

1. Copy /kexts/other/additional/NullEthernet.kext to /L*/E* and rebuild cache.
2. Copy /ACPI/additional/SSDT-RMNE to /ACPI/patched.
3. Reboot.
- Note: For iMessage, FaceTime, and App Store to function correctly with RMNE, I recommend you install RMNE before trying to connect to any USB networking devices. Otherwise, you need to reset the network mapping by having RMNE set to en0. Use Google.

## Credits

Apple for macOS

tctien342 and hieplpvip for Asus repositories

the VoodooI2C helpdesk for working touchpad

headkaze for Hackintool

RehabMan for Null Ethernet and many other things

CrazyBird for HFS+ partitioning in 10.14+

daliansky and williambj1 for many hotpatch methods

whatnameisit for all hard work, my main inspiration
