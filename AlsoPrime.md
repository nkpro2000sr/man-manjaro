# PrimeOS *with* **MANJARO**

### This Article will help you to setup PrimeOS with Manjaro.
PrimeOS operating system gives a complete desktop experience similar to Windows or MacOS with access to millions of Android apps.It is designed to bring you the best of both worlds - a complete fusion of Android and PC.

PrimeOS is another [Android-x86](https://www.android-x86.org/ "Home Page") fork

[Home Page](https://primeos.in/)
[Xda](https://forum.xda-developers.com/member.php?u=9505288 "forum.xda-developers.com")

## Step 1 (Download)
Download PrimeOS ISO file from [this page](https://primeos.in/download/ "Official Page")
> PrimeOS Mainline 64 bit (for newest systems 2014+)  
> PrimeOS Standard 64 bit (for newer systems 2011+)  
> PrimeOS Classic 32 bit (for older systems)  

## Step 2 (Extract)
copy files

1. initrd.img
2. ramdisk.img
3. system.sfs
4. install.img
5. kernel

from ISO to `/primeos/` (directory in root of Manjaro)

*(or)*

```bash
sudo mkdir /primeos /mnt/primeos
sudo mount -o loop path/to/ISO/file.iso /mnt/primeos
cd /mnt/primeos
sudo cp system.sfs kernel initrd.img install.img ramdisk.img /primeos/
sudo umount /mnt/primeos
```

## Step 3 (Create Persistent Storage)
Make "data" file, you can use 2 ways below:

a. Make data.img with this command:

   ```bash
   sudo dd if=/dev/zero of=/primeos/data.img bs=1M count=32768 # 32GB
   sudo mkfs.ext4 /primeos/data.img
   ```

b. Or, you can just make some folder with the name is "data".

> If persistent storage is not needed *skip this step*
>> Now any changes done in prime os, won't be saved

## Step 4 (Create Boot menu)
* install grub-customizer `sudo pacman -Syu grub-customizer`

* open grub-customizer `sudo grub-customizer`

* create new *Edit > New*

* Enter *Name* as "PrimeOS" and Select *Type* "Other"

* Paste below in *Boot sequence* textbox

  ```bash
  insmod part_gpt
  search --file --no-floppy --set=root /primeos/system.sfs
  linux /primeos/kernel root=/dev/ram0 androidboot.selinux=permissive buildvariant=userdebug SRC=/primeos
  initrd /primeos/initrd.img
  ```

* Click **Save** button

*(or)*

Add below lines in "/etc/grub.d/40_custom"

```bash
menuentry "PrimeOS"{
        insmod part_gpt
        search --file --no-floppy --set=root /primeos/system.sfs
        linux /primeos/kernel root=/dev/ram0 androidboot.selinux=permissive buildvariant=userdebug SRC=/primeos
        initrd /primeos/initrd.img
}
```

then `sudo update-grub`

## Step 5
PrimeOS is setuped successfully. Now reboot, select PrimeOS, and ENJOY :yum:
