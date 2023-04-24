#Dual boot of Windows 11 and Ubutnu 22.10 on a 15 Retina Macbookpro

**Disclaimer:**

*Machine used: 15 Retina Macbookpro with Nvidia GT750M graphics


*OS choosed: Ubuntu 22.10 and Windows 11

Before choosing Ubuntu I tried PopOS and Fedora37. 
I initially wanted to stick to Fedora but had problems getting the Dual-graphics feature to work (I could only use full time Nvidia or full time Intel, and couldn´t switch between them as it would break the OS completly), and the machine after sleep took an averge of 10 min to wake up and extreme overheating. 
Other distros, like Arch seem to dificult (By that time I was a newbie with Linux and had a very basic idea on how things worked)

Conclusion: for newbies to Linux with a Mac, I believe Ubuntu should be your first try (makes Linux easier and seems to run better on mac)

Preparartion(Done on MacOS):
1. From MacOS, you will need to download and Ubuntu and Windows iso (or choosed OS), then I used balena etcher to make the USB drive bootable. If you are installing windows, you will need to use Bootcamp, so you get the drivers needed

Installation of Ubuntu (not installing Ubuntu first will cause you to afterwards not be able to boot Windows)
1. Attatch the USB drive with Ubuntu and boot from it. From the installation menu, choose to use all the disk and earse it. I also checked the "Downlaod adittional drivers"
2. Once the installation is finished, reboot and make sure everything went ok
3. Now reboot, but from the Live USB, once there, select "Try Ubuntu"
4. Once on the desktop (booted from the USB drive) go to the Disks app, and shrink the dosk whyere you have Ubuntu (I left 80 Gb for Windows) 

Installation of Ubuntu
So for doing this part, or either you have 2 USB drivers or you need to install MacOS again on the 80GB free partition to get the drivers from BootCamp, and then install Windows. I did the second way, it takes more time but it ended up working good for me. I will asume you have a USB drive with all the drivers needed from Bootcamp from now 
1. Attach the USB drive, boot from on it
2. On windows 11 when you get the set up screen, press Shift+F10, and type "regedit" on the terminal
3. Now go to HKEY_LOCAL_MACHINE\SYSTEM\Setup
4. Create a new key called "LabConfig"
5. Create 3 new DWORD(32 bit) called "BypassTPMCheck", "BypassSecureBootCheck" and "BypassCPUCheck"
6. Set all the their values to 1 
7. Now close terminal and regedit and proceed to nnormla instllation
8. Install windows 11 on the 80 GB partition 
9. Once everything is setup, proceed to the installation of bootcamp 

Final adjustment 
By now you probably can't boot to Ubuntu. Fro fixing this we are goinf to use a boot manager, in this case rEFInd (which also has a tool that allows us to use the integrated GPU on Windows and Ubuntu) 
1. Create again a bootable USB of Ubuntu or reuse it 
2. Boot and get to Firefox, and proceed to https://www.rodsbooks.com/refind/installing.html
3. Scroll a bit and you should see the comands needed to install it on Ubuntu using APT. Follow the instructions
4. Once installed, type the following commands on the terminal:
5. sudo su
6. cd /boot/efi/EFI/refind
7. ls (you should see a file named refind.conf)
8. nano refind.conf (the file will open on the terminal)
9. press crtl + w and type spoof
10. Uncomment the line with the comand to spoof osx (remove #)
11. press crtl + o and then y
12. reboot
13. now you should reboot, and be able to choose which ps to boot from using rEFInd
