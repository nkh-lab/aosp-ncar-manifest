
# NCAR - Android Automotive Emulator Project

The project is based on latest 11 AOSP release (`android-11.0.0_r48`) because latest 12 AOSP releases (up to r15) have problem with `aosp_car_x86` emulator startup.

## Additionally supports
### Native libraries:
* [boost-1.72.0](https://github.com/boostorg/)
* [vsomeip 3.1.20.3](https://github.com/COVESA/vsomeip)
* CommonAPI via SOMEIP runtime libraries:
    * [capicxx-core-runtime 3.2.0](https://github.com/COVESA/capicxx-core-runtime)
    * [capicxx-someip-runtime 3.2.0 + patches](https://github.com/COVESA/capicxx-someip-runtime)

### Tools and Example projects
* [CommonAPI example project](https://github.com/nkh-lab/genivi-capi-someip-examples) - setups and tests communication between two native daemons
* [Vendor nkh-lab VHAL project](https://github.com/nkh-lab/aosp-ncar-vehicle-hal)

## Requirements to host PC
[Link to HW and SW requirements from Google.](https://source.android.com/setup/build/requirements)

## Setup and sync project
```
$ mkdir ncar && cd ncar
$ repo init -u git@github.com:nkh-lab/aosp-ncar-manifest.git
$ repo sync -c -d
```

## Build
```
$ . ./build/envsetup.sh
$ lunch ncar_x86-userdebug
$ make
```

## Run
```
$ emulator
```
