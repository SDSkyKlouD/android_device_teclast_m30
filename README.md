TWRP for Teclast M30 (M4P7)
===========================
This repository contains device configuration files for building [TWRP](https://twrp.me/).  
Device configurations are based on **M4P7**. M4P8 compatibility is unknown.

Downloads
---------
All of pre-built recovery image files can be found in [Releases](https://github.com/SDSkyKlouD/android_device_teclast_m30/releases) page.

How To Install
--------------
### Get Android platform tools
Android platform tools is the combination of useful tools for debugging/developing Android devices.  
This contains **ADB** and **Fastboot**, which are required to continue this procedures.  

  1. **Download it from Android Developer document**. Navigate to [HERE](https://developer.android.com/studio/releases/platform-tools#downloads) and download platform tools for your operating system.
  2. **Unzip platform tools to somewhere**.

If you already have it, then you can skip this section.

### Unlock bootloader
**!!PRECAUTION!!** Unlocking bootloader will avoid warranty, and will cause the factory reset. Make sure your data are backed up before unlock!  
I am no responsibilities about your warranty/data loss. I warned.  

  1. **Enable developer options**. [Android Developer document](https://developer.android.com/studio/debug/dev-options) explains how to do it.
  2. **Enable OEM unlocking**. In Settings - Developer options, find a setting titled **"OEM unlocking"** and turn it on. This allows you unlock bootloader using fastboot.
  3. **Also enable USB debugging**. This allows you use ADB from your PC/Mac.
  4. **Connect your tablet to your PC/Mac via USB**.
  5. **Open a console(terminal) and change directory to where the platform tools unzipped**.
  6. **Reboot to bootloader using ADB**. Type command line `adb reboot bootloader` in your console and press enter.  
  The tablet can ask you to authorize the computer if you haven't authorize it before. Authorize it and eventually the device will shut down.
  7. **If you see small text `=> FASTBOOT mode...` on device screen, your device is now in fastboot mode**.
  8. **Unlock bootloader using fastboot**. Type command line `fastboot oem unlock` in your console and press enter.  
  You will see some long texts on your device screen, titled `Unlock bootloader?`. Read texts carefully, and if you are agree with it, press **VOLUME UP** button on your device.
  9. **If unlocking is successful, the device will return to fastboot mode in 3 seconds**. You now have an unlocked M30.

### Flash TWRP image
  1. **Download pre-built image from Releases page**. See [Downloads](#Downloads) section.
  2. **Flash recovery image**. Type command line `fastboot flash recovery C:\ABSOLUTE\PATH\OF\RECOVERYIMAGE.img`. Replace file path with downloaded recovery image path, in absolute way.
  3. **If you see OK on your console, it's done.**

### Boot into TWRP recovery
  1. **Reboot**. You can reset the power by pressing RST button, which is next in power button. You can use SIM slot ejector.  
  Or, while in fastboot mode, type command line `fastboot reboot`.
  2. **Keep pressing VOLUME UP button**. Keep pressing while rebooting until `Select Boot Mode` shows on device screen.
  3. **Point to `[Recovery   Mode]` using VOLUME UP button and press VOLUME DOWN button**. This will reboot your device into TWRP recovery.
  4. **Fingers crossed!** if you see TWRP screen.

How To Build
------------
TODO. Simply, I used [minimal-manifest-twrp](https://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni). **YOU SHOULD USE twrp-7.1 BRANCH!** 8.0 or above branch produces oversized recovery image.  
Put this device configurations in (REPO)/device/teclast/m30, envsetup, lunch omni_m30-eng, make recoveryimage.
