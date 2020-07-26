# Ease MANJARO (ARCH Linux) Installation and Setup

<details>
    <summary>
        <img src="https://raw.githubusercontent.com/nkpro2000sr/man-manjaro/master/_static/img/pwm.png" align="right" height="50" width="150"
             title="Install manjaro '/WithWin'dows and '/AlsoPrime'OS">
    </summary>
    <div align="right"> <br>
    <h3>PrimeOS | Manjaro | Windows</h3>
    <p>Install manjaro <a href="https://nkpro2000sr.github.io/man-manjaro/WithWin">/WithWin</a>dows and
        <a href="https://nkpro2000sr.github.io/man-manjaro/AlsoPrime">/AlsoPrime</a>OS</p>
    </div>
</details>

## To update mirror list for faster pacman ;)
`sudo pacman-mirrors -c India`
> `reboot` to update changes

## Update and Upgrade 
`sudo pacman -Syyuu` to update and upgrade all packages including system packages.

## To install earlier versions of package
1. Download package from [https://archive.archlinux.org/packages/](https://archive.archlinux.org/packages/ "Arch Package Archive")
2. Update it `sudo pacman -U path/to/downloaded/package.pkg.tar.xz`  

## frequent pacman errors
1. "unable to lock database” or “failed to synchronize any databases”
   > `sudo rm /var/lib/pacman/db.lck`
2. "invalid or corrupted package:"
   > `sudo find /var/cache/pacman/pkg/ -iname "*.part" -exec rm {} ;`  
   > `sudo pacman -Syyu`

## Install some useful packages
`sudo pacman -Syu pacaur` to get packages from [Arch User Repository](https://aur.archlinux.org/ "https://aur.archlinux.org/")  
`sudo pacman -Syu snapd` [snap](https://snapcraft.io/ "One build for all Linux and IoT") cross-distribution package manager  
> also try [FLATPAK](https://flatpak.org/ "Linux cross-distribution application sandboxing and distribution framework") 
and [AppImage](https://appimage.org/ "Download an application, make it executable, and run! No need to install")

`pacaur -S stacer` [stacer](https://oguzhaninan.github.io/Stacer-Web/ "https://github.com/oguzhaninan/Stacer") for system optimizing and monitoring  
`sudo pacman -Syu bleachbit htop powertop iftop iotop`  

`sudo pacman -Syu git` [git](https://git-scm.com/ "https://git-scm.com/") to get packages from open source repos like github,etc,.

`sudo pacman -Syu docker` [docker](https://www.docker.com/ "https://www.docker.com/") to use containers (a form of operating system virtualization)

`sudo pacaur -Syu apt --noedit`  
yes, you can use apt in manjaro !  
> but it is still buggy :smirk:  

### Simple Python Version Management: pyenv  
pyenv lets you easily switch between multiple versions of Python.  
It's simple, unobtrusive, and follows the UNIX tradition of single-purpose tools that do one thing well.

you can setup pyenv (py) using a single line  
`curl -L bit.ly/setup-pyenv | sh`

<details>
<summary></summary>

> this included some useful startup commands  
> the above line just executes these commands
<script src="https://gist.github.com/nkpro2000sr/53049a2372a6e2ba2cc779b98b33c975.js"></script>  
>> If you are using [Zsh](https://www.zsh.org/ "Zsh is a shell designed for interactive use")  
>> change ~/.bashrc to ~/.zshrc *(or)* manually copy paste '#pyenv{[\s\S]\*#pyenv}' in .bashrc into ~/.zshrc  
</details>

### windows
`sudo pacman -Syu wine`  
[wine](https://www.winehq.org/ "https://www.winehq.org/") to run windows executable in linux

### android
* [anbox](https://anbox.io/ "https://anbox.io/") Anbox is a free and open-source compatibility layer that aims to allow mobile applications and mobile games developed for Android to run on GNU/Linux distributions.
> you can install it [this way](https://forum.manjaro.org/t/running-android-applications-on-arch-using-anbox/53332 "to install anbox")  
* [AndroidStudio](https://developer.android.com/studio "https://developer.android.com/studio") you can install by [this way](https://linuxconfig.org/how-to-install-android-studio-on-manjaro-18-linux "to install AndroidStudio") or simply `sudo pacman -Syu androidstudio`
> for more details about moving apps to AVD, etc,. [see](/man-manjaro/AndroidStudio)

## To backup and restore whole system 
use timeshift (recommended)  
`sudo pacman -Syu timeshift`

## To apply system themes for all apps
While changing theme or style in Appearance section in System Settings,
some apps won't change.

To solve this  
You need to set your GTK theme. It is in System Settings > Application Style > GNOME/GTK Application Style

This is because they are gnome/gtk apps, we have to set theme for them seperatly.

Also for browsers we have to make some configurations.

1. Chromium : enabled the use of gtk3 theme
2. FireFox : 
    1. In Firefox, go to the about:config page (type about:config in the address bar).
    2. Click through the warning dialog.
    3. Right-click anywhere and select New > String.
    4. For the preference name, type widget.content.gtk-theme-override.
    5. For the value, type Breath2-Dark.
    6. Close the about:config tab.
    7. Close and reopen the Firefox application.

> For full dark experience in browser, use [darkreader](https://darkreader.org/ "Extension for Browser")

## Autostart
[see this](https://wiki.archlinux.org/index.php/XDG_Autostart "in wiki.archlinux")

## Extra tools
* [buildozer](https://github.com/kivy/buildozer "github") Buildozer is a tool for creating application packages easily, using [python](https://www.python.org/ "https://www.python.org/") and [kivy](https://kivy.org "https://kivy.org")  
> to setup and configure buildozer [see](/man-manjaro/buildozer)
* [debtap](https://github.com/helixarch/debtap "DEB To Arch \(Linux\) Package") A script for converting .deb packages into Arch Linux packages, focused on accuracy.
> then install it using pacman `sudo pacman -U path/to/arch/pak`
* [alien](https://github.com/mildred/alien "Package converter .many -> .deb") A program that converts between the rpm, dpkg, stampede slp, and slackware tgz file formats.
> If you want to use a package from another distribution than the one you have installed on your system, you can use alien to convert it to your preferred package format and install it.
* [LDD](https://linoxide.com/linux-command/ldd-command-examples-linux/ "List Dynamic Dependencies") To find missing shared library dependencies.
> After found missing librarys
> * download library and paste it in appropriate locations eg:`/usr/lib/`
> * (or) find which package has the required and install it
>> To get info and list the files owned by package  
>> `pacman -Qil <package-name>`
* [SoundWire](http://georgielabs.net/ "HomePage") To Stream Audio from Your Linux PC to Android
> `pacaur -S soundwire` to install SoundWire from ArchlinuxUserRepository  
> dependencies: `sudo pacman -Syu pavucontrol`  
>> If you find the GUI claims the Android device is connected, but you’re not hearing any sound on your mobile device,
>> go back to the SoundWire Server GUI and click on the Open PulseAudio Volume Control button.
>> In this new window, go to the Recording tab and make sure Monitor of Built-In Audio Analog Stereo is selected from the Alsa Capture from drop-down.
>> Once that is selected, the sound should start spilling from your Android device.
>>> [detailed how to do](https://www.linux.com/topic/desktop/how-stream-audio-your-linux-pc-android/ "more details")
* *comming_soon... :smiley:*
