# **MANJARO** *Duel Boot with* WINDOWS

### This Article will help you installing Manjaro in Windows pre-installed system.

## Step 1 
Download MANJARO ISO file from [this page](https://manjaro.org/download/ "Official Manjaro Download Page")
> I prefer KDE edition 

## Step 2
* In Linux:  
> 1. Make sure you have the 4GB or larger USB Flash Disk (USB 3.0 is highly recommended).  
> 2. Plugin USB Flash Disk.  
> 3. Get path to your device(USB Flash Disk) node using `lsblk` command.  
> 4. unmount USB Flash Disk *(don't unplug)* by  
>    `sudo umount <PATH>` replace '\<PATH>' by path of your USB Flash Disk.  
> 5. Write iso image to USB Flash Disk by  
>    `sudo dd bs=4M if=<ISO-PATH> of=<PATH> status=progress && sync`  
>    replace '\<ISO-PATH>' by path of manjaro iso file.  
>    and replace '\<PATH>' by path of your USB Flash Disk.  
> 6. Now unplug your USE Flash Disk.  

* In Windows:
> 1. Download [Rufus](https://github.com/pbatard/rufus "Create bootable USB drives the easy way ") from [https://rufus.ie/](https://rufus.ie/ "Home Page") *(or)* [Github Releases](https://github.com/pbatard/rufus/releases "Up To Date")  
> 2. Run it if you downloaded *Portable Version* otherwise Install it.  
> 3. Select your USB Flash Disk in 'Device' drop down list box.  
> 4. Select Manjaro iso file in 'Boot selection' drop down list box.  
> 5. Then click 'START' Button *(only once)*.
> 6. After done unplug your USE Flash Disk.  

## Step 3
Now your USE Flash Disk is ready to BOOT :]  
1. Plug your USB Flash Disk and Restart your PC.  
2. Probably it will now show window with 'Welcome to Manjaro' title.  
> ### If Not :(
> It need some modifications in BIOS. (see [this](/man-manjaro/EditBIOS2Boot "to solve not booting from USB"))  
3. Now select 'Boot: Manjaro.x86_64 .\*' to boot into live-environment.  

## Step 4
Now we are good to install MANJARO to one of the partision ^-^  
1. This time also we have a window with 'Welcome to Manjaro' title and 'Launch installer' button.  
2. Click 'Launch installer' button, set Location, then Keyboard (choose English US - Default).  
3. In Partitions section:  
> i) create a partision for root:  
>> Size = most of space allocated for Linux  
>> Type = ext4; Mount Point = /; Flag = root

> ii) create a partision for swap (virtual RAM):  
>> Size = mostly 3GB  
>> Type = linuxswap; Flag = swap

> iii) if installer asked to create partision for /boot/efi:  
>> Size = Max 500 MB  
>> Type = fat32; Mount Point = /boot/efi; Flag = boot  
4. Enter username and password  
5. press INSTALL  
6. shutdown, unplug USB Flash Disk, and start.  

## Step 5
* If grub shows both MANJARO and Windows, then Installation done successfully :) (see [this](/man-manjaro) for ease setup)  
* If grub shows only MANJARO, then we have to update grub :|  
> Boot Manjaro, goto terminal, enter `sudo update-grub`. Now grub will show both MANJARO and Windows.  
* If grub stuck or grub rescue appears. It is due to no grub failure :(  
> 1. This time we need the Bootable USB Flash Disk we used for installation.  
> 2. Shutdown, Plugin USB Flash Disk, start.  
> 3. Execute this commands in live boot.  
```bash
su
mount <PATH> /mnt
mount -o bind /dev /mnt/dev
mount -o bind /dev/pts /mnt/dev/pts
mount -o bind /proc /mnt/proc
mount -o bind /run /mnt/run
mount -o bind /sys /mnt/sys
chroot /mnt
cd /boot/grub
grub-mkconfig -o /boot/grub/grub.cfg
grub-install <PATH>
exit
umount -a
```
> 4. Shutdown, Unplug USB Flash Disk, start.  
> 5. Boot Manjaro, goto terminal, enter `sudo update-grub`. Now grub will show both MANJARO and Windows.  

## Step 6
MANJARO installed successfully. Now its time to setup MANJARO properly, update, and install necessary packages.  
see [bit.ly/man-manjaro](/manjaro)  
