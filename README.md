# TWRP device tree for Samsung S10 aka beyond1lte
## Modification from original TWRP
The encryption of userdata will not be turned off as with orignal TWRP. TWRP can't access Android 12 encrypted data, but if you install original TWRP the Userdata will get lost. Either the system does not boot anymore and you can only recover when you factory reset the device or the data will be silently cleared on next boot.\
Since encrypted Userdata can not be accessed by TWRP, an option to backup Userdata, Keydata, Keyrefuge, and Keystorage in image mode was added.\
When the operating system is loaded from a boot.img without ramdisk (such as One UI) a variant is added that is patched by Magisk 26.1 so that the recovery acts as a boot helper.
##
##
## Kernel source 
Available at https://github.com/corsicanu/android_kernel_samsung_universal9820

## How to build
This was tested and it's fully compatible with [minimal manifest twrp](https://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni).
1. Set up the build environment following instructions from [here](https://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni/blob/twrp-9.0/README.md#getting-started)
2. In the root folder of cloned repo you need to clone the device tree:
```bash
git clone -b android-9.0 https://github.com/teamwin/android_device_samsung_beyond1lte.git device/samsung/beyond1lte
```
3. To build:
```bash
export ALLOW_MISSING_DEPENDENCIES=true && . build/envsetup.sh && lunch omni_beyond1lte-eng && mka recoveryimage -j128
```

