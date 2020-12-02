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


