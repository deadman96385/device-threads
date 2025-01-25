# Info and Development resources for the Light L16 (Codename: LFC)

## Navigating the device
Bootloader mode:
1. Power off & Unplug device
2. Hold Shutter button all the way down while plugging usb in

EDL usb cable
1. Power off & Unplug device
2. Plug in EDL cable
3. Turn off/Switch usb cables for 9008 mode

`adb reboot edl` to boot into EDL
1. Useful for backing up, but if your bricked you will need the cable

EDL Keycombo not avaliable

Recovery keycombo
1. Exists but can't trigger it reliably with the shutter it's a timing thing after boot it seems

## Hardware specs
- CPU: Qualcomm APQ8096 (Modem-less Snapdragon 820)
- GPU: Adrento 530
- Ram: 4GB
- EMMC: 256GB
- Battery: 4120mAh
- Sound: WCD9320 audio chip?
- WLAN: 2.4ghz/5ghz
- Bluetooth: 4.0/BLE
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
fastboot oem FacMode (Get|Disable) Show device info barcodes (IMEI, Serial, etc)
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

## Update to latest firmware via built-in updater (Only works on unmodifed stock)
[Reference instructions in the Archive repo](https://github.com/helloavo/Light-L16-Archive/tree/main?tab=readme-ov-file#firmware)

## Firmware
[1.3.5.1 OTA Update](https://github.com/helloavo/Light-L16-Archive/releases/tag/1.3.5.1)

1.3.5.1 Full Firmware dump - Soon

[1.3.2.5 Full Firmware dump](https://drive.google.com/file/d/1-wv_FVC8u9uhtOCqDXhud95O9DBl3pxL/view?usp=sharing)

[1.0.6.0 nb0 formated firmware](https://public.cieric.com/l16_backup/other_files/LFC-1060-0-00WW-A01.nb0.zip)

[1.0.6.0 qfil formated firmware](https://public.cieric.com/l16_backup/other_files/LFC-1060-0-00WW-A01-extracted.7z)

## EDL Client (Windows/Linux)
[Main Github Repo with all info](https://github.com/bkerler/edl)

Use the firehose loader from [this zip](https://public.cieric.com/l16_backup/other_files/light-l16-edl-files.7z)

#### Backup important partitions
I recommend you to backup some critical partitions, including: bspdata, rf_nv, deviceinfo, lightcal, securefs, cust_nv, box, sutinfo

Download all partitions off your camera other then userdata and generate the xml files needed to flash them easily
`python edl --loader prog_emmc_firehose_8996_ddr.elf rl dumps --memory=ufs  --skip=userdata --genxml`

## QFIL (Windows)
1. Download and install the [Qualcomm drivers](https://mega.nz/#F!ud8VwKRJ!-cJr7EJyhb1PkziNx5KvLQ?yFtVySyL)
2. Download the qfil firmware from above
3. Extract the firmware to a folder that you can easily access them from like your desktop
4. Download and install [QPST](https://www.androidfilehost.com/?fid=1395089523397896264)
5. Open the QFIL application (Find it in your start menu)
6. In the "Select Build Type" field select Flat Build
7. In the "Select Programmer" field navigate to the folder you extracted the firmware and support files to and select the prog_emmc_firehose_8996.mbn file
8. Select the "Load XML" button and navigate to the folder you extracted the firmware and support files to and select the rawprogram0.xml and then the patch0.xml when prompted.
9. Plug in your tablet
10. Run the following command `adb reboot edl`
11. If the text at the top of the QFIL application says "No Port Available" click the "Select Port..." option and pick your device. If your device isn't showing up there you didn't install the drivers properly.
12. Click the Download Button to begin flashing your device

### Backup with QFIL
Partition Manager does not seem to work with the firehose in my testing

## Foxconn OST Flasher (Windows)
1. Download and extract the [Modded OST](https://androidfilehost.com/?fid=8889791610682920445)
2. Download and extract the nb0 formatted firmware from above
3. Install the dotnet and msv dependencies in the deployment folder
4. Run the Modded OST launcher.exe
5. Click login on the prompt
6. Select next and then press the 3 dot button and select the nb0 firmware you downloaded in step 2
7. In the update option select Emergency Download & Erase user data
8. Follow on-screen steps in the program to connect the device and start the flash
9. While camera is flashing do not touch the camera or mess with the usb connection

## Kernel Source: 
None :(

## Unlocking bootloader:
```
adb reboot bootloader
fastboot oem devlock off
fastboot reboot
```
