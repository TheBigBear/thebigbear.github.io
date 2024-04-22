# Running Spinrite 6.1 On a Apple Intel Mac using VirtualBox VM

| *Disclaimer:* | 
|:----|
| this is a first draft and link references and footnotes are all messed up - so sorry refs like `¹² or [^12] or [^12^] are intermingled and messed up, will have to figure out how to fix my publishing pipeline :wink: |
| <sup>Thanks for the feedback Peter Blaise</sup> | 

## 1. Download the latest version of macOS:
- Go to the [Apple Support page](^27^) and follow the instructions to download the latest macOS that is compatible with your Mac²⁷.

## 2. Create a bootable installer for macOS on an external USB flash drive:
- Connect a USB flash drive to your Mac²¹.
- Open Terminal, which is in the Utilities folder of your Applications folder²¹.
- Run the following command in Terminal to create the bootable installer²¹:
```bash
sudo /Applications/Install\ macOS\ Sonoma.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```
Replace `MyVolume` with the name of your USB flash drive²¹.

## 3. Change System Integrity Protection (SIP):
- Restart your computer in Recovery mode¹².
- Launch Terminal from the Utilities menu¹².
- To disable SIP, run the command `csrutil disable`¹².
- To enable SIP, run the command `csrutil enable`¹².
- Restart your computer¹².

## 4. Boot from the newly created external USB flash drive:
- Restart your Mac and immediately press and hold the Option key²⁵.
- Release the Option key when you see the Startup Manager window²⁵.
- Select the external USB drive and click Return²⁵.

## 5. Install VirtualBox and VirtualBox Guest Extension Pack on the external USB drive:
- Download VirtualBox from the [official website](^10^) and install it on the external USB drive[^10^].
- Download the VirtualBox Guest Extension Pack from the [official website](^19^) and install it¹⁹.

## 6. Create a DOS VM using FreeDOS:
- Download the FreeDOS 1.3 USB Lite boot disk from the [FreeDOS website](^29^).
- Open VirtualBox and create a new VM[^30^].
- Set the type to `Other` and the version to `DOS`[^30^].
- Set the memory size to 64 MB[^30^].
- Choose `Use an existing virtual hard disk file` and select the FreeDOS 1.3 USB Lite boot disk[^30^].
- Click `Create`[^30^].

## 7a. Create a vmdk disk device that points to the Mac's internal SSD:
- Open Terminal².
- List all available disks and partitions by running the command `diskutil list`².
- Unmount the disk you want to use by running `diskutil unmountDisk /dev/disk#`, replacing `disk#` with the disk identifier².
- Navigate to the directory where you want to create the vmdk file².
- Run the following command to create a vmdk file referencing the physical disk²:
```bash
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk -rawdisk /dev/disk#
```
Replace `/path/to/file.vmdk` with the path where you want to create the vmdk file, and replace `disk#` with the disk identifier².

Please note that you need to run these commands as root or using sudo². Also, ensure that the disk is not in use (for example, don't use the disk where macOS is installed) to avoid data loss².

## 7b. Create a vmdk disk device that points to the Mac's internal SSD:
- Open Terminal².
- List all available disks and partitions by running the command `diskutil list`².
- Unmount the disk you want to use by running `diskutil unmountDisk /dev/disk#`, replacing `disk#` with the disk identifier².
- Navigate to the directory where you want to create the vmdk file².
- Run the following command to create a vmdk file referencing the physical disk²:
```bash
VBoxManage createmedium disk --filename /path/to/file.vmdk --sizebyte $(diskutil info /dev/disk# | grep "Total Size" | awk '{print $3}') --format VMDK
```
Replace `/path/to/file.vmdk` with the path where you want to create the vmdk file, and replace `disk#` with the disk identifier².

Please note that you need to run these commands as root or using sudo². Also, ensure that the disk is not in use (for example, don't use the disk where macOS is installed) to avoid data loss².

## 8. Unmount the disk:
- Open Disk Utility¹⁵.
- Select the disk that you want to unmount in the sidebar¹⁵.
- Click the `Unmount` button in the toolbar or beside the disk set name¹⁵.

## 9. Add the newly created raw physical vmdk disk as a second hard disk to the VM:
- In VirtualBox, select the VM and go to `Settings` -> `Storage`².
- Click the `Add Hard Disk` button, select `Choose existing disk`, and select the vmdk file².

Please note that you need to run the FreeDOS VM as root in order to be able to actually have the rights to access the raw physical disk².

Some relevant URLs used to produce this:
- [^1] How to download and install macOS - Apple Support. https://support.apple.com/en-us/102662.
- [^2] How to download and install macOS - Apple Support. https://support.apple.com/en-us/102662.
- [^3] Create a bootable installer for macOS - Apple Support. https://support.apple.com/en-us/101578.
- [^4] Disabling and Enabling System Integrity Protection. https://developer.apple.com/documentation/security/disabling_and_enabling_system_integrity_protection.
- [^5] How to Boot Mac From External USB Drive - AppleToolBox. https://appletoolbox.com/how-to-boot-mac-from-external-usb-drive/.
- [^6] How to Install VirtualBox in Your USB Drive and Run any Operating .... https://www.maketecheasier.com/install-virtualbox-in-usb/.
- [^7] How to Install VirtualBox in Your USB Drive and Run any Operating .... https://www.maketecheasier.com/install-virtualbox-in-usb/.
- [^8] How to Install VirtualBox Extension Pack - Lifewire. https://www.lifewire.com/install-virtualbox-extension-pack-4782422.
- [^9] How to Install VirtualBox Extension Pack - Lifewire. https://www.lifewire.com/install-virtualbox-extension-pack-4782422.
- [^10] The FreeDOS Project. https://www.freedos.org/download/.
- [^11] How to install FreeDos onto a USB stick? - Super User. https://superuser.com/questions/1388931/how-to-install-freedos-onto-a-usb-stick.
- [^12] Creating a raw disk VMDK and adding it to the Virtual machine ... - VMware. https://kb.vmware.com/s/article/2097401.
- [^13] Unmount a disk set or disk member using Disk Utility on Mac. https://support.apple.com/guide/disk-utility/unmount-a-disk-set-or-disk-member-dskud709f49b/mac.
- [^14] How to Use a Physical Hard Drive with a VirtualBox VM. https://www.serverwatch.com/guides/how-to-use-a-physical-hard-drive-with-a-virtualbox-vm/.
- [^15] hard drive - Use physical harddisk in Virtual Box - Super User. https://superuser.com/questions/495025/use-physical-harddisk-in-virtual-box.
- [^16] FreeDOS commands you need to know | Opensource.com. https://opensource.com/article/21/4/freedos-commands.
- [^17] Get started with FreeDOS | Opensource.com. https://opensource.com/article/21/6/get-started-freedos.
- [^18] FreeDOS Books. https://www.freedos.org/books/get-started/14-manual-install/.
- [^19] How to mount External Hard Drive in VirtualBox. https://www.eltima.com/article/virtualbox-usb-drive-passthrough/.
- [^20] VirtualBox USB Passthrough Extended GUIDE. https://www.net-usb.com/virtual-usb/virtualbox-usb-passthrough/.
- [^21] Anleitung: Externe Geräte mit virtuellen PCs verbinden. https://www.pcwelt.de/article/1154210/anleitung-externe-geraete-mit-virtuellen-pcs-verbinden.html.
- [^22] How to Install Your VirtualBox VM on an External Drive. https://www.youtube.com/watch?v=1oy6Uwr1RqU.
- [^23] About System Integrity Protection on your Mac - Apple Support. https://support.apple.com/en-us/102149.
- [^24] How to turn off System Integrity Protection on your Mac | iMore. https://www.imore.com/how-turn-system-integrity-protection-macos.
- [^25] How to Unmount A Disk On Mac|Fix Can't Unmount Drive on Mac - iBoysoft. https://iboysoft.com/howto/how-to-unmount-a-disk-on-mac.html.
- [^26] Couldn’t unmount the disk on Mac? Try this - MacPaw. https://macpaw.com/how-to/couldnt-unmount-disk-mac.
- [^27] How to Access USB from VirtualBox Guest OS - LinuxBabe. https://www.linuxbabe.com/virtualbox/access-usb-from-virtualbox-guest-os.
- [^28] Chapter 4. Guest Additions - VirtualBox.org. https://www.virtualbox.org/manual/ch04.html.
- [^29] How to install macOS on an external drive | Macworld. https://www.macworld.com/article/672585/how-to-install-macos-on-an-external-drive.html.
- [^30] How to Create a Bootable USB macOS Installer (Any MacOS Version). https://bing.com/search?q=how+to+install+macOS+on+an+external+USB+flash+drive.
- [^31] How to install macOS from a USB | TechRadar. https://www.techradar.com/how-to/how-to-install-macos-from-a-usb.
- [^32] How to Boot macOS From USB - The Mac Observer. https://www.macobserver.com/tips/how-to/boot-macos-from-usb/.
- [^33] How to download and install Apple's macOS 12 Monterey for your Mac. https://www.techradar.com/how-to/how-to-download-and-install-macos-12-monterey.
- [^34] Disk Operating System. https://www.freedos.link/.
- [^35] undefined. https://theartistunion.com/dyallas.
- [^36] undefined. http://download.virtualbox.org/virtualbox/.
- [^37] en.wikipedia.org. https://en.wikipedia.org/wiki/VirtualBox.
- [^38] User Guide for Release 7 - Oracle. https://docs.oracle.com/en/virtualization/virtualbox/7.0/user/EN-VBOX-7-0-USER.pdf.
- [^39] First Steps - Oracle Help Center. https://docs.oracle.com/en/virtualization/virtualbox/7.0/user/Introduction.html.
- [^40] Managing Oracle VM VirtualBox from the Command Line. https://www.oracle.com/technical-resources/articles/it-infrastructure/admin-manage-vbox-cli.html.
- [^41] VBoxManage createmedium - VirtualBox.org. https://www.virtualbox.org/export/86820/vbox/trunk/doc/manual/en_US/man_VBoxManage-createmedium.xml.
- [^42] 7.21. VBoxManage createmedium - Oracle. https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/vboxmanage-createmedium.html.
- [^43] VBoxManage createmedium - VirtualBox.org. https://www.virtualbox.org/export/97865/vbox/trunk/doc/manual/en_US/man_VBoxManage-createmedium.xml.

