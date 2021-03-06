# **MANJARO** *Duel Boot with* WINDOWS

### This Article will help you installing Manjaro in Windows pre-installed system.

## Step 1 
Download MANJARO ISO file from [this page](https://manjaro.org/download/ "Official Manjaro Download Page")
> I prefer KDE edition 

## Step 2
* In Linux:  
> 1_ Make sure you have the 4GB or larger USB Flash Disk (USB 3.0 is highly recommended).  
> 2_ Plugin USB Flash Disk.  
> 3_ Get path to your device(USB Flash Disk) node using `lsblk` command.  
> 4_ unmount USB Flash Disk *(don't unplug)* by  
>    `sudo umount <PATH>` replace '\<PATH>' by path of your USB Flash Disk.  
> 5_ Write iso image to USB Flash Disk by  
>    `sudo dd bs=4M if=<ISO-PATH> of=<PATH> status=progress && sync`  
>    replace '\<ISO-PATH>' by path of manjaro iso file.  
>    and replace '\<PATH>' by path of your USB Flash Disk.  
> 6_ Now unplug your USE Flash Disk.  

* In Windows:
> 1_ Download [Rufus](https://github.com/pbatard/rufus "Create bootable USB drives the easy way ") from [https://rufus.ie/](https://rufus.ie/ "Home Page") *(or)* [Github Releases](https://github.com/pbatard/rufus/releases "Up To Date").  
> 2_ Run it if you downloaded *Portable Version* otherwise Install and Run it.  
> 3_ Select your USB Flash Disk in 'Device' drop down list box.  
> 4_ Select Manjaro iso file in 'Boot selection' drop down list box.  
> 5_ Then click 'START' Button *(only once)*.  
> 6_ After done unplug your USE Flash Disk.  

* In Android:
> [https://github.com/EtchDroid/EtchDroid](https://github.com/EtchDroid/EtchDroid "An application to write OS images to USB drives, on Android, no root required.")

## Step 3
Now your USE Flash Disk is ready to BOOT :]  
1_ Plug your USB Flash Disk and Restart your PC.  
2_ Probably it will now show window with 'Welcome to Manjaro' title.  
> ### If Not :(  
> It need some modifications in BIOS. (see [this](/man-manjaro/EditBIOS2Boot "to solve not booting from USB"))  

3_ Now select 'Boot: Manjaro.x86_64 .\*' to boot into live-environment.  

## Step 4
Now we are good to install MANJARO to one of the partision ^-^  
1_ This time also we have a window with 'Welcome to Manjaro' title and 'Launch installer' button.  
2_ Click 'Launch installer' button, set Location, then Keyboard (choose English US - Default).  
3_ In Partitions section:  [Detailed INFO](https://wiki.archlinux.org/index.php/Partitioning#Example_layouts "Must see")  

> i) create a partision for root:  
>> Size = most of space allocated for Linux  
>> Type = ext4; Mount Point = /; Flag = root

> ii) create a partision for [swap](/man-manjaro/Swap) (virtual RAM):  
>> Size = mostly 3GB  
>> Type = linuxswap; Flag = swap

> iii) if installer asked to create partision for /boot/efi:  
>> Size = Max 500 MB  
>> Type = fat32; Mount Point = /boot/efi; Flag = boot  

4_ Enter username and password  
5_ press INSTALL  
6_ After installation completed shutdown, unplug USB Flash Disk, and start.  

## Step 5
* If grub shows both MANJARO and Windows, then Installation done successfully :) (see [this](/man-manjaro) for ease setup)  
* If grub shows only MANJARO, then we have to update grub :|  
> Boot Manjaro, goto terminal, enter `sudo update-grub`. Now grub will show both MANJARO and Windows.  
* If grub stuck or grub rescue appears. It is due to no proper grub config available :(  
> 1_ This time we need the Bootable USB Flash Disk we used for installation.  
> 2_ Shutdown, Plugin USB Flash Disk, start.  
> 3_ Execute this commands in live boot. /dev/sdX is the disk has manjaro installed.  
```bash
su
manjaro-chroot -a # choose manjaro installed partition.
cd /boot/grub
grub-mkconfig -o grub.cfg
grub-install /dev/sdX
exit
exit
```  
> 4_ Shutdown, Unplug USB Flash Disk, start.  
> 5_ Boot Manjaro, goto terminal, enter `sudo update-grub`. Now grub will show both MANJARO and Windows.  

## Step 6
MANJARO installed successfully. Now its time to setup MANJARO properly, update, and install necessary packages.  
see [bit.ly/man-manjaro](/man-manjaro "Blog by MANJARO User for MANJARO Users")  
