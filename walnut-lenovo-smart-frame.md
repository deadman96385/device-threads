# Info and Development resources for the Lenovo Smart Frame (Codename: Walnut) (Model Number: CD-3L501F)

## Firmware
> [!NOTE]
> Userdebug builds may lag more then User versions
> 
- Jan 14th 2022 Userdebug Build [Here](https://www.androidfilehost.com/?fid=16385555061192798583)
- Sept 29th 2021 User Build [Here](https://www.androidfilehost.com/?fid=16385555061192798594)
- April 5th 2021 User Build [Here](https://www.androidfilehost.com/?fid=16385555061192798585)
- Jan 17th 2021 User Build [Here](https://www.androidfilehost.com/?fid=16385555061192798598)
- May 28th 2020 User Build [Here](https://www.androidfilehost.com/?fid=16385555061192798579)

## Lenovo Self-extracting factory reset tool download (Jan 17th 2021 User Build): [Here](https://www.androidfilehost.com/?fid=16385555061192798593)

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

## (Windows) Lenovo Self-extracting factory reset tool usage
> [!IMPORTANT]
> This fully wipes your device and returns it to stock
1. Download the tool
1. Run it (It will ask to install drivers say yes)
1. It will install to ```C:\Users\USERNAME\AppData\Roaming\Lenovo_SmartFrame_Flash```
1. Run Flash.cmd to fully flash your device with whatever image files are in the image folder
