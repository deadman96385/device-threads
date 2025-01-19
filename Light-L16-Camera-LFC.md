# Info and Development resources for the Light L16 (Codename: LFC)

## Navigating the device
Bootloader/fastboot keycombo = Power off & Unplug device, Hold Shutter button while plugging usb in

EDL Keycombo not avaliable

EDL Cable not tested

Some form of update mode on early boot via internal storage

## Hardware specs
- CPU: Qualcomm APQ8096 (Modem-less Snapdragon 820)
- GPU: Adrento 530
- Ram: 4GB
- EMMC: 256GB
- Sound: WCD9320 audio chip?
- WLAN: Yes
- Bluetooth: Yes
- GPS: Yes
- Sensors:
  - Accelerometer (BMI160)
  - Gyroscope (BMI160)
  - Magnetometer (BMM150)
  - Ambient light sensor and proximity sensor (stk3x1x)
  - Hall Effect sensor (BU52053NVX)
- Camera:
  - On-Semi AR835 Camera Sensor
  - On-Semi AR1335 Camera Sensor
  - IMX386 Camera Sensor
  - Laser Time-of-flight (ToF) sensor (VL53L0X)
  - Two Tone Led Flash (OSRAM CBLPM1 LED with LM3644TT controller)
  - Mirrors: Dieletric SNX, Silver ZUSHO
  - Mirror Actuator: PZT (Pizo eletric)
  - Lens: Showin, Largan, Sunny, Kantatsu
  - Lens Type: Shicoh, PZT (Pizo eletric)
  - Linear Hall-effect Sensors (OSRAM AS5510)
- Nanya ASIC's
- Stock OS: Android 6.0.1
- Display:
   - Size: 5"
   - 60hz IPS Panel
   - Resolution: FHD (1920 x 1080)
   - Software Density: 480 dpi (xxhdpi)

## Fastboot Commands
```
fastboot oem btn
fastboot oem alive - Reboots the camera to fastboot next time its plugged in.
fastboot oem battery getcapacity - Checking current battery capacity
fastboot oem devlock (off, on) (Turns off FIH security restrictions and enables service mode)
fastboot oem FacMode (Get|Disable)
fastboot oem ForceAOS - Turns display green UNKNOWN
fastboot oem getBootloaderType
fastboot oem getversions - Shows FIH Build Version details.
fastboot oem HALT - Power off the phone.	
fastboot oem key
fastboot oem LCM SetProgressColor (black, whtie, red, green, blue, yellow) - Fills the entire screen with one single color.
fastboot oem LCM SetProgressMsg
fastboot oem log (lk, ld)
fastboot oem mfd
fastboot oem mpp
fastboot oem ptn
fastboot oem rec (clr, set, get)
fastboot oem vib
```
## Backup important partitions
I recommend you to backup some critical partitions, including: bspdata, rf_nv, deviceinfo, lightcal, securefs, cust_nv, box, sutinfo

## Update to latest firmware

## Firmware
[1.3.5.1 OTA Update](https://github.com/helloavo/Light-L16-Archive/releases/tag/1.3.5.1)

1.3.5.1 Full Firmware dump

1.3.2.5 qfil formated firmware

1.0.6.0 nb0 formated firmware

1.0.6.0 qfil formated firmware

## Update via built-in updater (Only works on unmodifed stock)
[Reference instructions in the Archive repo](https://github.com/helloavo/Light-L16-Archive/tree/main?tab=readme-ov-file#firmware)

## EDL Client (Windows/Linux)

## Foaxconn OST Flasher (Windows)

## QFIL (Windows)

## Kernel Source: 
None :(

## Unlocking bootloader:
```
adb reboot bootloader
fastboot oem devlock off
fastboot reboot
```

## Rooting with Magisk Manager and a boot.img
1. Download [Magisk manager](https://github.com/topjohnwu/Magisk/releases) and a file manager like [Material Files](https://github.com/zhanghai/MaterialFiles) on the camera
2. Open the Magisk app on the camera and press install near the top left. Press next, select and patch a file
3. Open the menu on the left and select material files, scroll down and select boot.img, and then press LET'S GO ->
4. After it completes check the output to see where it saved the file normally its in the folder you placed the boot.img
5. ```
   adb pull /sdcard/Download/magisk_patched-XXXXX_YYYYY.img magisk_patched.img
   adb reboot bootloader
   fastboot oem devlock off
   fastboot reboot bootloader
   fastboot flash boot magisk_patched.img
   fastboot reboot
   ```
6. The camera will bootup and the magisk app will now have a superuser tab and you can access the su command in adb shell/terminal for root accesss
