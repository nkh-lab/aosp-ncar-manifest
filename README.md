
# NCAR - Android Automotive Emulator Project

The project is based on the AOSP version, which is specified in the corresponding manifest filename `android-X.X.X_rX.xml`.

## Additionally supports
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

## Setup and sync project
```
$ mkdir ncar && cd ncar
$ repo init -u https://github.com/nkh-lab/aosp-ncar-manifest.git
$ repo sync -c -d
```
Or, if you want to use a specific release of AOSP (check supported releases in the branch list), specify it via the branch name:
```
$ repo init -u https://github.com/nkh-lab/aosp-ncar-manifest.git -b android-11.0.0_r48
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
