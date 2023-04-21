#Dual boot of Windows 11 and Ubutnu 22.10 on a 15 Retina Macbookpro 
Disclaimer: 
*Machine used: 15 Retina Macbookpro with Nvidia GT750M graphics
*OS choosed: Ubuntu 22.10 and Windows 11
Before choosing Ubuntu I tried PopOS and Fedora37. 
I initially wanted to stick to Fedora but had problems getting the Dual-graphics feature to work (I could only use full time Nvidia or full time Intel, and couldn´t switch between them as it would break the OS completly), and the machine after sleep took an averge of 10 min to wake up and extreme overheating. 
Other distros, like Arch seem to dificult (By that time I was a noobie with Linux and had a very basic idea on how things worked)

Conclusion: for newbies to Linux with a Mac, I believe Ubuntu should be your first try (mkaes Linux easier and seems to run better on mac)

Preparartion(Done on MacOS):
1. From MacOS, you will need to download and Ubuntu and Windows iso (or choosed OS), then I sued balena etcher to make the USB drive bootable. If you are installing windows, balenaEtcher may not work, for that I created the usb from a working windows 11 machine
<The following steps are only if you have a dedicated GPU and want to make use of it. This include the HDMI port, which is connected to the dedicated GPU, so not having it means no display output. If you only have Intel GPU, you can skip the following steps: from 2 to 7>
2. Disable SIP (System Integrity Protection)
3. Go to rEFInd webpage, and downlaod the binnay version (should be a .zip file)
4. Extract it to anyplace, open a terminal and go to there you extracted the folder
5. run ./refind.sh to install it. It will ask for root privilege, so type your password 
6. Run "sudo su", and then "cd /boot/EFI/efi/refind" and search for refind.conf. Now do "nano refind.conf". it should open the file on the terminal
7. press control+w (should appear a search field on the botton) and type spoof. Once you pressed enter, using the arrows key go to the line with has somethging liek spoof_mac_os and remove the # at the beggingning of the line. Then press control+o and then confirm it. 
<Following part is just for installing Windows 11, if you don´t want you can skip this part>
8. Shut down the machine and attach the USB and magsafe
9. Turn on the machine. Now you should boot into the R
