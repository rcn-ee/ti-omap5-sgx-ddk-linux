# SGX Embedded Systems DDK for Linux kernel.

Copyright (C) Imagination Technologies Ltd. All rights reserved.


## About

This is the Imagination Technologies SGX DDK for the Linux kernel.


## License

You may use, distribute and copy this software under the terms of the MIT
license.  Details of this license can be found in the file "MIT-COPYING".

Alternatively, you may use, distribute and copy this software under the terms
of the GNU General Public License version 2.  The full GNU General Public
License version 2 can be found in the file "GPL-COPYING".


## Build and Install Instructions

For IMG details see the "INSTALL" file. The following instructions are tailored
to TI platforms.


### Linux


#### Environemnt variables

```bash
export KERNELDIR=<kernel directory>
export DISCIMAGE=<root of the target fs>
export ARCH=arm64
export CROSS_COMPILE=aarch64-linux-gnu-
export KERNEL_CROSS_COMPILE=aarch64-linux-gnu-
export WINDOW_SYSTEM=lws-generic
export PVR_BUILD_DIR=<ti654x_linux or other product>
```

If debug build is required:

```bash
export BUILD=debug
```


#### Building

Make sure that the kernel is built before building DDK KM.
```bash
make -j <number of build threads>
```

If a clean build is needed, run `make clean` or `make clobber` before `make`.


#### Installing

Make sure that kernel modules are installed in DISCIMAGE before installing KM.
This can be done as follows:

```bash
cd $KERNELDIR
sudo -E make INSTALL_MOD_PATH=$DISCIMAGE modules_install

cd $DDKROOT
sudo -E make install
```

### Android


#### Environemnt variables

```bash
export KERNELDIR=<kernel directory>
export ANDROID_ROOT=<android source directory>
export OUT_DIR=<android output directory>
export CROSS_COMPILE=${ANDROID_ROOT}/prebuilts/gcc/linux-x86/arm/arm-linux-androideabi-4.9/bin/arm-linux-androideabi-
export KERNEL_CROSS_COMPILE=${ANDROID_ROOT}/prebuilts/gcc/linux-x86/arm/arm-linux-androideabi-4.9/bin/arm-linux-androideabi-
export EXCLUDED_APIS="composerhal,camerahal,unittests,sensorhal"
export ARCH=arm
export PVR_BUILD_DIR=<am572x_linux or other product>
export JAVA_HOME=${ANDROID_ROOT}/prebuilts/jdk/jdk8/linux-x86
export PATH=${ANDROID_ROOT}/prebuilts/jdk/jdk8/linux-x86/bin:$PATH
export USER_DIR=${DDK_ROOT}/eurasia/eurasiacon/build/linux2/omap_android
export KERNEL_DIR=${DDK_ROOT}/eurasia_km/eurasiacon/build/linux2/omap_android
```

If debug build is required:

```bash
export BUILD=debug
```


#### Building

```bash
cd ${USER_DIR}
make -j <number of build threads>
```


#### Installing

Copy the generated KM into the Android vendor project for the platform:

```bash
cd ${DDK_ROOT}/eurasia_km/eurasiacon/binary2_${PVR_BUILD_DIR}_android_release/
cp target_armv7-a/kbuild/pvrsrvkm.ko ${ANDROID_ROOT}/vendor/ti/dra7xx/sgx_km/lib/modules/
```

Rebuild Android images to pick up this change.


## Contact information

Imagination Technologies Ltd. <gpl-support@imgtec.com>
Home Park Estate, Kings Langley, Herts, WD4 8LZ, UK
