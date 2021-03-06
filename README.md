# OAndBackupX  <img align="left" src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/icon.png" width="64" />

OAndBackupX is a fork of the infamous OAndBackup with the aim to bring OAndBackup to 2020. For now most of the functionality and UI of the app are rewritten, next steps would be making it stable and adding some features which could ease the backup/restore work with any device. Therefore all types of contribution are welcome.

Usecases: a combination with your favourite sync solution (e.g. Syncthing, Nextcloud...)  keeping a copy of your apps and data on your server or "stable" device could bring a lot of benefits and save you a lot of work while changing ROMs or just cleaning your mobile device.

Now on OAndBackup: a backup program for android. requires root and allows you to backup individual apps and their data.
both backup and restore of individual programs one at a time and batch backup and restore of multiple programs are supported (with silent / unattended restores). 
restoring system apps should be possible without requiring a reboot afterwards. OAndBackup is also able to uninstall system apps. handling system apps in this way depends on whether /system/ can be remounted as writeable though, so this will probably not work for all devices (e.g. htc devices with the security flag on).  
backups can be scheduled with no limit on the number of individual schedules and there is the possibility of creating custom lists from the list of installed apps.

## Changes & TODOs

- [x] Fixing OAB-Utils build problem which was caused by a deprecated method in Rust
- [x] Adapt FastAdapter: for Main and Batch
- [x] Rewrite Batch-(Activity, Adapter and Sorter) 
- [x] Rewrite Main-(Activity, Adapter and Sorter)
- [ ] Rewrite Scheduler
- [x] Add more informative dialog when clicking an app in Main
- [x] Rewrite Scheduler
- [x] Modeling Sort/Filter
- [ ] Add some new filters
- [x] Rewrite Preferences
- [x] Rewrite backup folder selector
- [x] Integrate Tools and Help in Preferences
- [ ] New android scope storage permissions compatibility: fixed for Android 10 with legacy mode(fix priority: med)
- [x] Add in-app check for updates
- [x] Updating UI and UX: Design improvement proposals are always welcome
- [x] Add Dark/Light themes
- [ ] Update dialogs' UI: partially done
- [ ] Abstracting the structure of the app
- [x] Fragmenting the Preferences: partially done
- [ ] Rewrite the logic of Backup/Restore
- [x] Add support for protected data backup
- [ ] Fix and Add in-app encryption solution(fix priority: med)
- [ ] Add a Flashable-ZIP feature
- [ ] You suggest!...


## Screenshots

### Dark Theme
<p float="left">
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/1.png" width="170" />
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/2.png" width="170" />
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/3.png" width="170" />
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/4.png" width="170" />
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/5.png" width="170" />
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/6.png" width="170" />
</p>

### Light Theme
<p float="left">
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/7.png" width="170" />
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/8.png" width="170" />
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/9.png" width="170" />
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/10.png" width="170" />
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/11.png" width="170" />
 <img src="https://raw.githubusercontent.com/machiav3lli/OAndBackupX/master/fastlane/metadata/android/en-US/images/phoneScreenshots/12.png" width="170" />
</p>

## Building

OAndBackupX is built with gradle. you need the android sdk, rust for building the oab-utils binary, and bash or a compatible shell for executing the oab-utils build script (patches for making this buildable on windows are welcomed).

P.S: If you have any problem building OAB-Utils: you can find some helping notes in its Readme.md

```
./gradlew build
# building only debug
./gradlew assembleDebug
# building for a specific abi target
./gradlew assembleArm64
```

## Version Control

OAndBackupX is handled on Github:   
https://github.com/machiav3lli/oandbackupx

## Busybox / OAB-Utils

a working busybox installation is required at the moment, but work is in progress to include all the needed functionality in a binary included in the apk. this program is called oab-utils and is written in rust.

you can get the source for busybox here: https://busybox.net/. you then need to cross-compile it for the architecture of your device (e.g. armv6). you can also try the binaries found here: https://busybox.net/downloads/binaries/.   
if you have a working toolchain for your target device, you should only need to run the following commands on the busybox source:

```
    make defconfig # makes a config file with the default options
    make menuconfig # brings up an ncurses-based menu for editing the options
        # set the prefix for your toolchain under busybox settings -> build options 
        # (remember the trailing dash, e.g. 'arm-unknown-linux-gnueabihf-')
        # build as a static binary if needed
    make
```

copy the busybox binary to your system, for example /system/xbin or /data/local, and make it executable. symlinking is not necessary for use with oandbackupx. in the oandbackupx preferences, provide the whole path to the busybox binary, including the binary's file name (e.g. /data/local/busybox).

translations of the original OAndBackup are currently being managed on transifex: https://www.transifex.com/projects/p/oandbackup/
so please come help us there or spread the link if you want the app available in your own language.

## Licenses

as a fork of OAndBackup, OAndBackupX is licensed under the MIT license (see LICENSE.txt)

App's icon is based on an Icon made by [Catalin Fertu](https://www.flaticon.com/authors/catalin-fertu) from [www.flaticon.com](https://www.flaticon.com)

Placeholders Icon made by [Smashicons](https://www.flaticon.com/authors/smashicons) from [www.flaticon.com](https://www.flaticon.com)

## Credits

[Jens Stein](https://github.com/jensstein) for his unbelievably valuable work on OAndBackup.

[Rahul Patel](https://github.com/whyorean) whose hard work on AuroraStore inspired this work.

Open-Source libs: [ButterKnife](https://github.com/JakeWharton/butterknife), [FastAdapter](https://github.com/mikepenz/FastAdapter), [AppUpdater](https://github.com/javiersantos/AppUpdater), [NNFilePicker](https://github.com/spacecowboy/NoNonsense-FilePicker), [RootBeer](https://github.com/scottyab/rootbeer).

## author

Antonios Hazim
