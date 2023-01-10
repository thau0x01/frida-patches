# Patches for Stronger Frida
Build stealth frida binaries without any "frida" keyword strings.

# Setup
```bash
# install build  dependencies
sudo apt-get update && DEBIAN_FRONTEND=noninteractive sudo apt-get install build-essential tree ninja-build gcc-multilib g++-multilib lib32stdc++-9-dev flex bison xz-utils ruby ruby-dev python3-requests python3-setuptools python3-dev python3-pip libc6-dev libc6-dev-i386 -y
sudo gem install fpm -v 1.11.0 --no-document
python3 -m pip install lief

# clone repositories
git clone https://github.com/thau0x01/frida-patches.git
git clone --recurse-submodules https://github.com/frida/frida.git

# apply patch
cd frida/frida-core
git am ../../frida-patches/thau0x01-patches/*.patch
cd ..
make core-android-x86_64
make core-android-arm
make core-android-arm64
```

## Note
You also need Android Studio's NDK installed and `$ANDROID_NDK_ROOT` envvar set (ex: `/home/user/Android/Sdk/ndk/25.1.8937393`).

# Thanks
This repository is based on @hluwa's ["Patchs" repository](https://github.com/hluwa/Patchs).
