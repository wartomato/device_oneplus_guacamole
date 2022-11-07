# Device Tree for OnePlus 7 Pro (guacamole)

The OnePlus 7 Pro (codenamed _"guacamole"_) is a flagship smartphone from OnePlus.
It was released in May 2019.


|                Hardware | Spec Sheet                                                                                                                    |
| ----------------------: | :---------------------------------------------------------------------------------------------------------------------------- |
|                     CPU | Octa-core (1x2.84 GHz Kryo 485 & 3x2.42 GHz Kryo 485 & 4x1.78 GHz Kryo 485)                                                   |
|                 Chipset | Qualcomm SM8150 Snapdragon 855 (7 nm)                                                                                         |
|                     GPU | Adreno 640                                                                                                                    |
|                  Memory | 6/8/12 GB RAM                                                                                                                 |
| Shipped Android Version | 9.0 (_"Pie"_) / OxygenOS 10 (_"Q"_)                                                                                           |
|                 Storage | 128/256 GB                                                                                                                    |
|                 Battery | Non-removable Li-Po 4000 mAh battery                                                                                          |
|                 Display | Fluid AMOLED capacitive touchscreen, 16M colors, 6.67 inches, 1440 x 3120 pixels, 19.5:9 ratio (~516 ppi density)             |
|           Camera (Back) | Triple setup: 48 MP (f/1.6, wide, 1/2", 0.8µm, PDAF, Laser AF, OIS) + 8 MP (f/2.4, 78mm, telephoto, 3x optical zoom,          |
|                         | PDAF, Laser AF, OIS) + 16 MP (f/2.2, 13mm, ultrawide, AF), Dual-LED flash, panorama, HDR, 2160p@30/60fps, 1080p@30/60/240fps, |
|                         | 720p@480fps, Auto HDR, gyro-EIS                                                                                               |
|          Camera (Front) | Motorized pop-up 16 MP, f/2.0, 25mm (wide), 1/3.0", 1.0µm, Auto-HDR, 1080p@30fps, gyro-EIS                                    |

*Currently these devices are supported:*


| codename | Devicename    | Target area   | projectname | baseband (rf) |
| -------- | ------------- | ------------- | ----------- | ------------- |
| GM1913   | OnePlus 7 Pro | Europe (-EEA) | 18821       | 4             |
| GM1917   | OnePlus 7 Pro | Global/US     | 18821       | 5             |

*Unsupported as of writing:*


| codename | Devicename       | Target area    | projectname | baseband (rf) |
| -------- | ---------------- | -------------- | ----------- | ------------- |
| GM1910   | OnePlus 7 Pro    | China          | 18821       | 1             |
| GM1911   | OnePlus 7 Pro    | India          | 18821       | 3             |
| GM1915   | OnePlus 7 Pro    | T-Mobile       | 18831       | -             |
| GM1920   | OnePlus 7 Pro NR | Europe (5G)    | 18827       | -             |
| GM1925   | OnePlus 7 Pro NR | US (Sprint 5G) | 18825       | 5             |

_projectname = android projectname defined by the vendor system props "ro.boot.project_name" or "ro.vendor.boot.project_name"_
_baseband = defined baseband by the vendor system prop "ro.boot.rf_version"_

Copyright 2019 - The AICP Project.

![OnePlus 7 Pro](https://fdn2.gsmarena.com/vv/pics/oneplus/oneplus-7-pro-4.jpg "OnePlus 7 Pro")

---

Additional notes for manually flashing Android firmware for guacamole:

If you are on an older firmware or NOT running the latest stock OOS 12, please update the firmware files and partitions that do NOT come with the ROM using a PC.

1. Download the needed firmware image files from e.g. `https://gitlab.com/the-muppets/proprietary_vendor_firmware/-/tree/lineage-20/guacamole` and store them in a directory on your PC.
2. Boot up to your recovery or boot to the phone's bootloader.
      2.1 Bootloader mode can be entered either from recovery or by pressing and holding
          Vol+ and Vol - and the power button at the same time. After that connect
          the device to your PC.
      2.2 Using the build-in LineageOS recovery or their recovery.img, boot to it and
          navigate to “Advanced” -> “Enter fastboot”
3. Execute following commands from the directory that the firmware files are all stored:

```
fastboot devices
fastboot flash --slot=all abl abl.img
fastboot flash --slot=all aop aop.img
fastboot flash --slot=all bluetooth bluetooth.img
fastboot flash --slot=all cmnlib64 cmnlib64.img
fastboot flash --slot=all cmnlib cmnlib.img
fastboot flash --slot=all devcfg devcfg.img
fastboot flash --slot=all dsp dsp.img
fastboot flash --slot=all hyp hyp.img
fastboot flash --slot=all keymaster keymaster.img
fastboot flash --slot=all LOGO LOGO.img
fastboot flash --slot=all modem modem.img
fastboot flash --slot=all oem_stanvbk oem_stanvbk.img
fastboot flash --slot=all qupfw qupfw.img
fastboot flash --slot=all storsec storsec.img
fastboot flash --slot=all tz tz.img
fastboot flash --slot=all xbl_config xbl_config.img
fastboot flash --slot=all xbl xbl.img
fastboot reboot
```

4. After doing so you can now use the firmware by flashing the AICP ROM with version 18.x from recovery to BOTH slots.
   *Keep in mind that an older ROM version (based on OOS 11) might not work anymore after the update!*
