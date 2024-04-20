# Info and Development resources for the Lenovo Smart Frame (Codename: Walnut) (Model Number: CD-3L501F)

## Navigating the device
This device does not have a touchscreen so you need to usb mouse plugged into the usb c port with an otg adapter to begin with.

## IR Proximity & Button info
The black pill shaped section is an IR powered proximity sensor that has UP/Down/Left/Right gesture detection which are reported to the OS as the following:
1. ```GESUTRE_DIR_UP (Keycode 289)```
1. ```GESUTRE_DIR_DOWN (Keycode 290)```
1. ```GESTURE_DIR_LEFT (Keycode 291)```
1. ```GESTURE_DIR_RIGHT (Keycode 292)```

There are 3 capacitive hw buttons, 2 arrows and a star icon.
1. ```KEYCODE_VOLUME_UP (Keycode 115)```
1. ```KEYCODE_VOLUME_DOWN (Keycode 114)```
1. ```KEYCODE_FAVORITE (Keycode 295)```

## Enable ADB access
1. Remove the silcone cover over the USB C port on the back of the frame near the exposed power port
1. Plug in your usb adapter/hub and a usb mouse
1. Use the mouse to quickly try and pull the statusbar down from the top multiple times until it expands
1. Click the gear icon to go to settings
1. Unlock development settings and then turn adb access on
1. You will need a bluetooth controller or mouse to accept the adb authorization prompt, use your wired mouse to pair it in settings and then connect the device to your computer via a usb c cable 
1. (Optional) Enable oem unlock in developer settings to save time for future modding

## Firmware
Each package contains a FrameROM.exe or you can flash the images manually with sp flash on windows/linux
> [!NOTE]
> Userdebug build may lag more then User versions
> 
- Jan 14th 2022 Userdebug Firmware [Here](https://www.androidfilehost.com/?fid=16385555061192798583)
- Sept 29th 2021 User Firmware [Here](https://www.androidfilehost.com/?fid=16385555061192798594)
- April 5th 2021 User Firmware [Here](https://www.androidfilehost.com/?fid=16385555061192798585)
- Jan 17th 2021 User Firmware [Here](https://www.androidfilehost.com/?fid=16385555061192798598)
- May 28th 2020 User Firmware [Here](https://www.androidfilehost.com/?fid=16385555061192798579)

## Kernel Source: [Here](https://github.com/deadman96385/android_kernel_lenovo_mt8167)

## Kernel Module Source: [Here](https://github.com/deadman96385/android_vendor_mediatek_kernel_modules_connectivity)

## Official Lenovo Smart Frame Companion app: [Here](https://www.androidfilehost.com/?fid=16385555061192798588)

## Unlocking bootloader:
1. Setup ADB and Fastboot on your PC.
1. Connect a mouse via a USB OTG adapter to the USB C port under a rubber flap by the power connector
1. Use the mouse to reveal the statusbar by dragging down on the top of the screen and get into settings
1. Enable USB debugging and OEM Unlock in Development Settings.
1. Pair a bluetooth mouse or tv/game controller to the device so you can accept the usb debugging authorization prompt later
1. Unplug the OTG adapter & Mouse and connect your device to the PC with a USB C cable.
1. Open a command prompt window on your PC.
1. Run the following command to make sure adb shows up ```adb devices```
1. Make sure you select the adb authorization prompt with your BT Mouse/Controller
1. Boot your device into bootloader mode using the following command:
```adb reboot bootloader```
1. Once your device is in bootloader mode, issue the following command to unlock bootloader:
```fastboot flashing unlock```
1. You’ll get a confirmation screen on your device it will say you need to press a volume button, but it will auto unlock it if you leave it for 20-30 seconds
1. During reboot, your device will go through a factory reset and then finally boot into system.
1. That’s all. Your device’s bootloader is now unlocked.

## GSI Install/Usage
### GSI System Type:
Arm64 AB

### Tested GSI's: 
Phh AOSP 12.1 v416 (system-squeak-arm64-ab-vanilla.img.xz)

### Steps:
1. Unlock your bootloader
1. Download one of the firmware packages
1. Extract vbmeta_system.img
1. Disable vbmeta for system with this fastboot command in bootloader (Fastboot mode)
   ```fastboot --disable-verity --disable-verification flash vbmeta_system vbmeta_system.img```
1. Reboot to fastbootd
   ```fastboot reboot fastboot```
1. Flash the GSI system image 
   ```fastboot flash system system-squeak-arm64-ab-floss.img```
1. Sadly there is no way to directly boot to recovery so you must boot up into the very broken non-factory reset os
1. Then factory reset the device via settings or via adb
   
   Settings Method:

   Settings -> Backup & Reset -> Reset data -> full factory reset

   ADB Method:
   1. ```adb shell```
    1. ```recovery -wipe_data```
   1. ```adb reboot recovery```

## (Windows) Lenovo Self-extracting factory reset tool usage
### Lenovo Self-extracting factory reset tool download (Jan 17th 2021 User Build): [Here](https://www.androidfilehost.com/?fid=16385555061192798593)
> [!IMPORTANT]
> This fully wipes your device and returns it to stock
1. Download the tool
1. Run it (It will ask to install drivers say yes)
1. It will install to ```C:\Users\USERNAME\AppData\Roaming\Lenovo_SmartFrame_Flash```
1. Run Flash.cmd or FrameROM.exe to fully flash your device with whatever image files are in the image folder
