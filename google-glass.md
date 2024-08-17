# Info and Development resources for the Google Glass Explorer and Enterprise series devices
## Explorer Edition (XE-A, XE-B, XE-C)
#### Google documentation
[Here](https://developers.google.com/glass/tools-downloads/system)

#### Specs
##### Explorer Version 1 XE-A
- Android 4.4 (KitKat)[131]
- 640×360 Himax HX7309 LCoS display
- 5-megapixel camera, capable of 720p video recording[8]
- Wi-Fi 802.11b/g
- Bluetooth
- 16 GB storage (12 GB available)[8]
- Texas Instruments OMAP 4430 SoC 1.2 GHz Dual (ARMv7)
- 1 GB RAM
- 3 axis gyroscope, 3 axis accelerometer and 3 axis magnetometer (compass)
- Ambient light sensing and proximity sensor
- Bone conduction audio transducer

##### Explorer Version 2 XE-B
- 2 GB RAM
- Prescription frames available

##### Explorer Version 3 XE-C
- 3 GB RAM

#### Bootloader
The XE bootloader is unlockable by default

#### Kernel Source
[Here](https://android.googlesource.com/kernel/omap/+/refs/heads/glass-omap-xrx13)

## Enterprise Edition 1 (EE1)
#### Google documentation
This device was never publicly released so there is no documentation

#### Specs
 - Intel Atom TG100 processor
 - Dual-band 802.11n/ac wifi,
 - Assisted GPS & GLONASS
 - Barometer
 - 32 GB of storage
 - 780 mAh battery
 - Dynamic driver speaker instead of bone conduction audio transducer

### Bootloader
The EE1 bootloader is unlockable by default

### Kernel Source
This device was never publicly released so there is no GPL kernel source

## Enterprise Edition 2 (EE2)
#### Google documentation
[Here](https://developers.google.com/glass-enterprise/downloads/system-images)

#### Specs
 - Qualcomm Snapdragon XR1 quad core, up to 1.7 GHz, 10 nm
 - Android 8.1.0 AOSP
 - 3 GB LPDDR4
 - Bluetooth 5.x AoA
 - 8MP 80° FOV camera
 - 3 beam-forming microphones
 - USB Type-C port supporting USB 2.0 480 Mbit/s
 - 820 mAh battery with fast charge
 - 6-axis accelerometer/gyroscope
 - On-head detection sensor and Eye-on-screen sensor for power-saving features
 - Water and dust resistant
 - ~46g weight

### Bootloader
The EE2 bootloader is unlockable by default if the glasses are bought from a google authorized seller. Some Google Partner glasses are very locked down. Be sure to confirm that the Google stock firmware is installed before buying any.

### Kernel Source
[Here](https://github.com/deadman96385/android_kernel_google_glassv3)
#### History:
Initially back in early 2020, I had to fight through Google Glass support for them to release the source to me. But they now post it freely on the firmware dev docs. I have worked on turning the files they released into a kernel source with a good history and an explanation of the changes google did to the reference Qualcomm source. Both the kernel and techpack changes are included. Sadly due to how the Qualcomm wifi driver is licensed, they are not required to release it so I have instead imported the reference source which seems to work. The source has all changes as of the msm-4.9_221118	November 18, 2022.
