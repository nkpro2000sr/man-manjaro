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
4. .....
