# Info and Development resources for the ZTE Quartz smartwatch (Codename: Platy)

## Firmware
(Latest) NWD1.170831.001 Factory fastboot images
[Here](https://www.androidfilehost.com/?fid=11410932744536982243)

NXH20F Factory fastboot images
[Here](https://www.androidfilehost.com/?fid=11410932744536982242)

> [!CAUTION]
> (Do not use for developers only)
> 
> > P890W01V1.0.0B02 Pre-release Factory fastboot images
[Here](https://www.androidfilehost.com/?fid=11410932744536982241)
> > 
> > P890W01V1.0.0B04 Pre-release Factory fastboot images
[Here](https://www.androidfilehost.com/?fid=1322778262904025020)

## Official Twrp download:
[Here](https://twrp.me/zte/platy.html)

## T-Mobile Sales Force factory reset tool download:
[Here](https://www.androidfilehost.com/?fid=1322778262904025023)

## Kernel Source:
[Here](https://github.com/OpenWatchProject/android_kernel_zte_msm8909w)

## Twrp source:
[Here](https://github.com/TeamWin/android_device_zte_platy)


## Unlocking bootloader:
1. Setup ADB and Fastboot on your PC.
1. Enable USB debugging and OEM Unlock on your watch.
1. Connect your watch to the PC with a USB cable.
1. Open a command window on your PC.
1. Boot your watch into bootloader mode using the following command:
```adb reboot bootloader```
1. You may get a request to authorize USB debugging on the device, accept it.
1. Once your device is in bootloader mode, issue the following command to unlock bootloader:
```fastboot oem unlock```
1. You’ll get a confirmation screen on your watch and follow what it says This will begin bootloader unlocking process, which shouldn’t last more than a couple of minutes.
1. Once bootloader is unlocked, your device will reboot into bootloader mode. You need to boot into system now, either press Power button to reboot OR issue the following command:
```fastboot reboot```
1. During reboot, your watch will go through a factory reset and then finally boot into system.
1. That’s all. Your watch’s bootloader is now unlocked.

## T-Mobile Sales Force factory reset tool usage
> [!IMPORTANT]
> This fully wipes your device and returns it to stock along with removing your ESIM configuration:
1. Download the tool
1. Install it
1. Run it
1. Unlock the bootloader
1. Enable adb on your watch
1. Plug the watch into your computer
1. Click start in the application
1. Wait for it to finish and enjoy
