# Running SpinRite 6.1 on a UEFI only windows PC

## Step 1: Download Necessary Software
First, you need to download the necessary software. Here are the download links:
- [Rufus][^1]
- [VirtualBox][^4]
- [VirtualBox Extension Pack][^6]
- [FreeDOS USB Lite boot disk][^18]

## Step 2: Create a Windows To Go USB Boot Flash Drive Using Rufus
1. Launch Rufus.
2. Select your USB drive from the Device drop-down menu.
3. Click the Select button next to the Boot Selection field and then select your Windows 10/11 ISO image file[^10].
4. In the Image option list, choose `Windows To Go`¹¹.
5. Click the `Start` button to create the bootable USB[^10].

## Step 3: Reboot the Windows PC Off of the USB Stick
1. Connect the bootable USB flash drive to a USB port on your PC.
2. Restart your PC.
3. Press the appropriate key (ex: ESC, F2, F9 or F11) displayed for Boot Menu when you see the option available¹⁵.
4. Choose the USB drive to boot from¹⁵.
5. On windows 10 or 11 PCs you will likely have to use

## Step 3 - alternative: Reboot the Windows PC Off of the USB Stick
1.  Connect the bootable USB flash drive to a USB port on your PC.
2.  Open the Settings app (you can do this by pressing the Windows key + I).
3.  Navigate to  `Update & Security`.
4.  Select  `Recovery`  on the left sidebar.
5.  On the right panel, locate the  `Advanced startup`  option.
6.  [Click the  `Restart now`  button](https://www.thewindowsclub.com/how-to-boot-from-usb-drive-within-windows)[^31](https://www.thewindowsclub.com/how-to-boot-from-usb-drive-within-windows).
7.  After your PC restarts, you’ll see a screen with a few options. Choose  `Use a device`.
8.  [On the next screen, click or tap on the USB drive that you want to boot from](https://www.thewindowsclub.com/how-to-boot-from-usb-drive-within-windows)[^32](https://www.thewindowsclub.com/how-to-boot-from-usb-drive-within-windows).
9.  [Your computer will now restart and boot from the selected USB drive](https://www.thewindowsclub.com/how-to-boot-from-usb-drive-within-windows)[^33](https://www.thewindowsclub.com/how-to-boot-from-usb-drive-within-windows).

## Step 4: Install VirtualBox and Its Guest Extensions on the Windows To Go USB Boot Drive
1. Launch the installer for VirtualBox that you downloaded earlier.
2. Follow the prompts to install VirtualBox on your Windows To Go USB boot drive²⁴.
3. Once VirtualBox is installed, click the Devices menu and select the `Insert Guest Additions CD image` option²⁴.
4. Open File Explorer in the virtual machine, navigate to the VirtualBox Guest Additions disc, and double-click the VBoxWindowsAdditions.exe file to launch the installer²⁴.
5. Follow the prompts to install the Guest Additions²⁴.

## Step 5: Create a DOS VM Booting FreeDOS 1.3
1. Launch VirtualBox.
2. Click the `New` button to create a new virtual machine.
3. Name your virtual machine, select `Other` for the type, and `DOS` for the version.
4. Set the memory size and create a virtual hard disk.
5. Once the virtual machine is created, select it and click the `Settings` button.
6. In the settings window, navigate to `Storage` and click the `Empty` CD icon under the `Controller: IDE` section.
7. Click the CD icon on the right side and select `Choose a disk file...`.
8. Navigate to the location of the FreeDOS USB Lite boot disk you downloaded earlier and select it²¹.
9. Click `OK` to close the settings window.
10. Start the virtual machine and follow the prompts to install FreeDOS²¹.

Please note that this guide assumes you have a Windows 10/11 ISO image file for creating the Windows To Go USB boot flash drive. If you don't have one, you can download it from the official Microsoft website. Also, please be careful when following these steps as incorrect usage can lead to data loss. Be aware that in order for a Virtualbox VM to be able to access a raw physical device Virtualbox needs to be started or run with elevated or admin rights. Always backup your data before making any changes to your system.

Some relevant URLs used to produce this:
- [^1]: wufus - The Official Website (Download, New Releases). https://rufus.ie/.
- [^2]: wownloads - Oracle VM VirtualBox. https://www.virtualbox.org/wiki/Downloads.
- [^3]: Oracle VM VirtualBox - Downloads | Oracle Technology Network | Oracle. https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html.
- [^4]: wreeDOS 1.2 (USB "Lite" installer) : Free Download, Borrow, and .... https://archive.org/details/FD12LITE.
- [^5]: wsing Rufus To Create Windows To Go USB Drive. https://www.intowindows.com/rufus-to-create-windows-to-go-usb-drive/.
- [^6]: wow to install Windows 11 & Windows 10 on a USB drive (Windows To Go). https://www.digitalcitizen.life/install-windows-to-go/.
- [^7]: wow to boot from a USB drive (4 ways) - Digital Citizen. https://www.digitalcitizen.life/boot-your-windows-10-pc-usb-flash-drive/.
- [^8]: wow to install VirtualBox Guest Additions on Windows 11/10. https://www.thewindowsclub.com/how-to-install-virtualbox-guest-additions-on-windows.
- [^9]: wow to Run FreeDOS 1.3 on Windows 11 with Qemu. https://www.trishtech.com/2023/03/how-to-run-freedos-on-windows-11/.
- [^10]: wndex of /downloads - Rufus. https://rufus.ie/downloads/.
- [^11]: wufus - Create bootable USB drives the easy way. https://therufus.org/.
- [^12]: wracle VM VirtualBox. https://www.virtualbox.org/.
- [^13]: wownloads – Oracle VM VirtualBox. https://www.virtualbox.org/wiki/Downloads?source=....
- [^14]: wownload Oracle VM VirtualBox Extension Pack- Direct Links. https://www.itechscreen.com/virtualbox/oracle-vm-virtualbox-extension-pack/.
- [^15]: windows 11 und 10: Bootfähigen USB-Stick erstellen – Anleitung. https://www.giga.de/downloads/windows-10/tipps/windows-10-von-usb-stick-installieren-anleitung/.
- [^16]: winen USB-Stick bootfähig machen und den PC retten. https://www.ionos.de/digitalguide/server/knowhow/usb-stick-bootfaehig-machen/.
- [^17]: wreate Windows To Go USB Drive Using Rufus in Windows 10. https://www.thepcinsider.com/create-windows-to-go-usb-drive-rufus/.
- [^18]: windows 7 vom USB-Stick installieren. https://praxistipps.chip.de/windows-7-installation-per-usb-stick_27924.
- [^19]: wow to Boot from USB Drive within Windows 11/10 - The Windows Club. https://www.thewindowsclub.com/how-to-boot-from-usb-drive-within-windows.
- [^20]: woot from USB Drive on Windows 10 PC | Tutorials - Ten Forums. https://www.tenforums.com/tutorials/21756-boot-usb-drive-windows-10-pc.html.
- [^21]: whe FreeDOS Project. https://www.freedos.org/download/.
- [^22]: wow to install FreeDos onto a USB stick? - Super User. https://superuser.com/questions/1388931/how-to-install-freedos-onto-a-usb-stick.
- [^23]: wlarification on using Rufus to create a bootable live FreeDOS USB .... https://superuser.com/questions/1688959/clarification-on-using-rufus-to-create-a-bootable-live-freedos-usb-drive.
- [^24]: wreeDOS Books. https://www.freedos.org/books/get-started/14-manual-install/.
- [^25]: whapter 4. Guest Additions - VirtualBox.org. https://www.virtualbox.org/manual/ch04.html.
- [^26]: wow to Access USB from VirtualBox Guest OS - LinuxBabe. https://www.linuxbabe.com/virtualbox/access-usb-from-virtualbox-guest-os.
- [^27]: wndefined. https://www.qemu.org/download/.
- [^28]: wndefined. https://qemu.weilnetz.de/w64/.
- [^29]: wndefined. https://www.virtualbox.org/svn/vbox/trunk.
- [^30]: wndefined. https://www.virtualbox.org/wiki/Downloads?source=.
- [^31]: How to Boot from USB Drive within Windows 11/10 - The Windows Club. https://www.thewindowsclub.com/how-to-boot-from-usb-drive-within-windows.
- [^32]: How to boot from a USB drive (4 ways) - Digital Citizen. https://www.digitalcitizen.life/boot-your-windows-10-pc-usb-flash-drive/.
- [^33]: 2 Easy Ways to Boot from USB on Windows 11 - UUByte. https://www.uubyte.com/boot-from-usb-on-windows-11-pc.html.
