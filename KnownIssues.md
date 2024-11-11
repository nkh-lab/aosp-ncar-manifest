## Known Issues
* **android-12-1.0_r5, android-12-1.0_r27**: Android doesn't boot on HiKey960, gets stuck on welcome screen (rotating dots), no ADB.

## libncurses.so.5 and libtinfo.so.5 packages missing from Ubuntu 23.10+
1. Add links to prebuilts:
```
cd <path to AOSP NCAR>/ncar/prebuilts/clang/host/linux-x86
git apply <path to this project>/patches/libncurses_so_5_and_libtinfo_so_5.patch
```
2. Add links to `/usr/lib`
```
sudo ln -s <path to AOSP NCAR>/ncar/prebuilts/gcc/linux-x86/host/x86_64-linux-glibc2.17-4.8/sysroot/usr/lib/libncurses.so.5 /usr/lib/libncurses.so.5
sudo ln -s <path to AOSP NCAR>/ncar/prebuilts/gcc/linux-x86/host/x86_64-linux-glibc2.17-4.8/sysroot/usr/lib/libtinfo.so.5 /usr/lib/libtinfo.so.5
```