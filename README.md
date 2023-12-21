
# NCAR - Android Automotive Project

The project is based on the AOSP version, which is specified in the corresponding manifest filename `android-X.X.X_rX.xml`.

## Supported Devices
* `ncar_x86` - emulator for x86 architecture
* `ncar_hikey960` - for [HiKey960 board](https://www.96boards.org/product/hikey960)

## Additionally supported SW
### Third Party Native libraries:
* [boost-1.72.0](https://github.com/boostorg/)
* [vsomeip 3.1.20.3](https://github.com/COVESA/vsomeip)
* CommonAPI via SOMEIP runtime libraries:
    * [capicxx-core-runtime 3.2.0](https://github.com/COVESA/capicxx-core-runtime)
    * [capicxx-someip-runtime 3.2.0 + patches](https://github.com/COVESA/capicxx-someip-runtime)

### Tools, Utils and Example projects
* [CommonAPI example](https://github.com/nkh-lab/genivi-capi-someip-examples) - setups and tests communication between two native daemons
* [Vendor nkh-lab VHAL](https://github.com/nkh-lab/aosp-ncar-vehicle-hal) - implements VHAL and extends [vehicle/2.0/types.hal::VehicleProperty](https://cs.android.com/android/platform/superproject/+/master:hardware/interfaces/automotive/vehicle/2.0/types.hal;drc=0e6c4ce8731b3cead9966506b08eb69277926f08;l=153) with [custom vendor properties](https://github.com/nkh-lab/aosp-ncar-vehicle-hal/blob/master/1.0/types.hal)
* [CAR API usage example](https://github.com/nkh-lab/car-api-hello-world)
* [Share AVD](https://github.com/nkh-lab/aosp-share-avd) - tool project for sharing Emulator for others to use with Android Studio
* [\<device\>.mk parser](https://github.com/nkh-lab/aosp-devicemk-parser) - tool project for parsing AOSP device mk file dependencies to PlantUML format
* [nkhlablogger](https://github.com/nkh-lab/logger) - utility library for source code tracing and debugging

## Requirements to host PC
[Link to HW and SW requirements from Google.](https://source.android.com/setup/build/requirements)

## Download source tree
```
mkdir ncar && cd ncar
repo init -u https://github.com/nkh-lab/aosp-ncar-manifest.git
repo sync -c -d
```
Or, if you want to use a specific release of AOSP (check supported releases in the branch list), specify it via the branch name:
```
repo init -u https://github.com/nkh-lab/aosp-ncar-manifest.git -b android-11.0.0_r48
```

## Build and Run Emulator
**Build:**
```
. ./build/envsetup.sh
lunch ncar_x86-userdebug
make
```
**Run:**
```
emulator
```

## Build and Flash HiKey960
**Build:**
```
. ./build/envsetup.sh
lunch ncar_hikey960-userdebug
make
```
If you're building for the first time, you'll be asked during lunch about downloading the Linaro binaries:
```
device/linaro/hikey/device-common.mk:36: warning: Missing Linaro Vendor Package!
device/linaro/hikey/device-common.mk:37: warning: Please download new binaries here:
device/linaro/hikey/device-common.mk:38: warning: https://releases.linaro.org/android/aosp-linaro-vendor-package/extract-linaro_devices-20220210.tgz
device/linaro/hikey/device-common.mk:39: warning: And extract in the ANDROID_TOP_DIR
device/linaro/hikey/device-common.mk:41: warning: EXPECTED_LINARO_VENDOR_VERSION=20220210
```
**Flash:**
```
adb reboot bootloader
./device/linaro/hikey/installer/hikey960/flash-all.sh
```
___
See also [Known Issues](./KnownIssues.md)
