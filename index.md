## To update mirror list for faster pacman ;)
`sudo pacman-mirrors -c India`
> `reboot` to update changes

## Update and Upgrade 
`sudo pacman -Syyuu` to update and upgrade all packages including system packages.

## install some useful packages
`sudo pacman -Syu pacaur` to get packages from [Arch User Repository](https://aur.archlinux.org/ "https://aur.archlinux.org/")  
`sudo pacman -Syu git` [git](https://git-scm.com/ "https://git-scm.com/") to get packages from open source repos like github,etc,.   

`sudo pacman -Syu docker` [docker](https://www.docker.com/ "https://www.docker.com/") to use containers (a form of operating system virtualization)  

`sudo pacaur -Syu apt --noedit`  
yes, you can use apt in manjaro !  
> but it is still buggy :smirk:  

### Simple Python Version Management: pyenv  
pyenv lets you easily switch between multiple versions of Python.  
It's simple, unobtrusive, and follows the UNIX tradition of single-purpose tools that do one thing well.

you can setup pyenv (py) using a single line  
`curl $(curl bit.ly/setup-pyenv 2>/dev/null | cut -d'"' -sf2) 2>/dev/null | sh`
> this included some useful startup commands  
> the above line just executes these commands
<script src="https://gist.github.com/nkpro2000sr/53049a2372a6e2ba2cc779b98b33c975.js"></script>

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

## Extra tools
* [buildozer](https://github.com/kivy/buildozer "github") Buildozer is a tool for creating application packages easily, using [python](https://www.python.org/ "https://www.python.org/") and [kivy](https://kivy.org "https://kivy.org")  
> to setup and configure buildozer [see](/man-manjaro/buildozer)
* *comming_soon... :smiley:*


<script data-ad-client="ca-pub-4586260317371453" async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
