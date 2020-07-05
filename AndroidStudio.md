
# To install Android-SDK
`pacaur -S android-sdk`

## Dependencies
pretty much all the dependencies will be installed by pacaur.
But it installs jdk-10 which still has some errors with sdkmanager.

##### So to use jdk-8
```bash
# To install java-8
sudo pacman -Syu jdk8-openjdk
# To set java-8 as default
sudo ln -sfT /usr/lib64/jvm/java-8-openjdk /usr/lib64/jvm/default-runtime
sudo ln -sfT /usr/lib64/jvm/java-8-openjdk /usr/lib64/jvm/default
```

# To start AVD
You need more three packages: The platform, the system-image and the build-tools.
You can download these packages for any Android version you prefer.

Use the `sdkmanager --list` command to find these packages and download them using the command `sdkmanager <package name>`.

* To download platform (demo)  
  `sdkmanager 'platforms;android-28'`
* To download system-image (demo)  
  `sdkmanager 'system-images;android-28;default;x86'`
* To download build-tools (demo)  
  `sdkmanager 'build-tools;28.0.3'`

Emulator is also installed while installing android-sdk

* To create AVD (demo)  
  `avdmanager create avd --name android29 --package 'system-images;android-28;default;x86'`
* To list all available AVDs  
  `emulator -list-avds`
* To start 'android29' (demo) Android Virtual Device  
  `emulator -avd 'android29'`

# To install adb
`pacman -S android-tools`

## adb commands
```bash
adb push myapp.apk /sdcard/Download/myapp.apk # to copy apk to anbox or AndroidStudio
adb pull /sdcard/Download/file.ext file.ext   # to copy file from anbox or AndroidStudio
adb install path/to/app.apk                   # to install app in anbox or AndroidStudio
adb install -k --user 0 path/to/app.apk       # to install app in phone

adb shell pm list packages -f                 # to list
adb shell pm list packages -s                 # to list only system apps
adb shell pm list packages -3                 # to list only 3rd party apps
adb shell pm uninstall com.my.demo.app             # to uninstall app in anbox or AndroidStudio
adb shell pm uninstall -k --user 0 com.my.demo.app # to uninstall app in phone

...
```
