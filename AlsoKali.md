# Kali *with* MANJARO

### This Article will help you to setup Kali Linux with Manjaro (on same partition).
Kali Linux is a Debian-based Linux distribution aimed at advanced Penetration Testing and Security Auditing.
Kali Linux contains several hundred tools which are geared towards various information security tasks, such as
Penetration Testing, Security research, Computer Forensics and Reverse Engineering.

[Home Page](https://www.kali.org/)

## Step 1 (Download)
Download Kali ISO file from [this page](https://www.kali.org/downloads/ "Official page").  
Choose 64-Bit (Live).

## Step 2 (Live space)
Make a directory named 'live' in root of partition and move ISO to that location.  

(or)

```bash
sudo mkdir /live
sudo mv ~/Download/kali*.iso /live/
```

## Step 3 (Create Persistent Storage)
Make a directory named 'persistence' in '/live'.  
Create a text file persistence.conf in root of partition and write `/ union,source=live/persistence` in it.

(or)

```bash
sudo mkdir /live/persistence
sudo echo '/ union,source=live/persistence' > /persistence.conf
```

## Step 4 (Create Boot menu)
Add below lines in "/etc/grub.d/40_custom"
```bash
#KaliLive{
submenu 'Kali Linux' --class kali --class gnu-linux --class gnu --class os --group group_main {
    menuentry 'Live system' --class kali --class gnu-linux --class gnu --class os --group group_main {
        set isofile='/live/kali-linux-2020.2-live-amd64.iso'
        insmod ext2
        insmod loopback
        insmod iso9660
        search --file --no-floppy --set=root "${isofile}"
        loopback loop "(${root})${isofile}"
        linux (loop)/live/vmlinuz boot=live components quiet splash noeject findiso="${isofile}"
        initrd (loop)/live/initrd.img
    }
    menuentry 'Live system (fail-safe mode)' --class kali --class gnu-linux --class gnu --class os --group group_main {
        set isofile='/live/kali-linux-2020.2-live-amd64.iso'
        insmod ext2
        insmod loopback
        insmod iso9660
        search --file --no-floppy --set=root "${isofile}"
        loopback loop "(${root})${isofile}"
        linux (loop)/live/vmlinuz boot=live components noeject memtest noapic noapm nodma nomce nolapic nomodeset nosmp nosplash vga=normal findiso="${isofile}"
        initrd (loop)/live/initrd.img
    }
    menuentry 'Live system (forensic mode)' --class kali --class gnu-linux --class gnu --class os --group group_main {
        set isofile='/live/kali-linux-2020.2-live-amd64.iso'
        insmod ext2
        insmod loopback
        insmod iso9660
        search --file --no-floppy --set=root "${isofile}"
        loopback loop "(${root})${isofile}"
        linux (loop)/live/vmlinuz boot=live components quiet splash noeject findiso="${isofile}" noswap noautomount
        initrd (loop)/live/initrd.img
    }
    menuentry 'Live system (persistence)' --class kali --class gnu-linux --class gnu --class os --group group_main {
        set isofile='/live/kali-linux-2020.2-live-amd64.iso'
        insmod ext2
        insmod loopback
        insmod iso9660
        search --file --no-floppy --set=root "${isofile}"
        loopback loop "(${root})${isofile}"
        linux (loop)/live/vmlinuz boot=live components quiet splash noeject findiso="${isofile}" persistence persistence-label=linux
        initrd (loop)/live/initrd.img
    }
}
#KaliLive}
```
then `sudo update-grub`

> Replace 'kali-linux-2020.2-live-amd64.iso' by your ISO file name.  
> **Check your main partition lable is 'linux'. If not change it or edit /etc/grub.d/40_custom**

# Step 5
Kali Live is setuped successfully. Now reboot, select Kali Live, and HACK :smiling_imp::dragon:

<br /><br /><br />

##### References:
1. [https://www.tecmint.com/run-linux-live-images-from-hard-disk-in-linux/](https://www.tecmint.com/run-linux-live-images-from-hard-disk-in-linux/)
> presenting a way you can run some Linux ISO distributions directly from your hard disk  
2. [https://www.offensive-security.com/kali-linux/usb-multiple-persistent-stores/](https://www.offensive-security.com/kali-linux/usb-multiple-persistent-stores/)
> The persistent storages can be either encrypted, or unencrypted, and can be chosen at boot time using the persistence-label boot parameter.  
3. [http://manpages.ubuntu.com/manpages/trusty/man5/persistence.conf.5.html](http://manpages.ubuntu.com/manpages/trusty/man5/persistence.conf.5.html)
> Explains 'persistence.conf'.  
4. [https://ubuntuforums.org/showthread.php?t=1460756](https://ubuntuforums.org/showthread.php?t=1460756)
> why `insmod=ext2` while I use ext4 root partition.  
