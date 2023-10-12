########################################################################### ###
#@Title         Root makefile for TI Linux.  Builds everything else.
#@Copyright     Copyright (c) Imagination Technologies Ltd. All Rights Reserved
#@License       Dual MIT/GPLv2
# 
# The contents of this file are subject to the MIT license as set out below.
# 
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# Alternatively, the contents of this file may be used under the terms of
# the GNU General Public License Version 2 ("GPL") in which case the provisions
# of GPL are applicable instead of those above.
# 
# If you wish to allow use of your version of this file only under the terms of
# GPL, and not to allow others to use your version of this file under the terms
# of the MIT license, indicate your decision by deleting the provisions above
# and replace them with the notice and other provisions required by GPL as set
# out in the file called "GPL-COPYING" included in this distribution. If you do
# not delete the provisions above, a recipient may use your version of this file
# under the terms of either the MIT license or GPL.
# 
# This License is also included in this distribution in the file called
# "MIT-COPYING".
# 
# EXCEPT AS OTHERWISE STATED IN A NEGOTIATED AGREEMENT: (A) THE SOFTWARE IS
# PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING
# BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
# PURPOSE AND NONINFRINGEMENT; AND (B) IN NO EVENT SHALL THE AUTHORS OR
# COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
# IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
# CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
### ###########################################################################

include ../config/window_system.mk

SGXCORE := 544
SGX_CORE_REV := 117
SGX_FEATURE_MP := 1
SGX_FEATURE_SYSTEM_CACHE := 1
SGX_FEATURE_MP_CORE_COUNT := 1

PVRSRV_NEED_PVR_DPF := 1
PVRSRV_NEW_PVR_DPF := 1
#PVRSRV_NEED_PVR_TRACE := 1

# Disable active power management
SUPPORT_ACTIVE_POWER_MANAGEMENT := 0

# Disable Device Class
SUPPORT_PVRSRV_DEVICE_CLASS := 0

# Enable SONAME
DONT_USE_SONAMES := 0

# Disable  GL_IMG_texture_stream extension in GLES1 and GLES2 to remove
# invalid unit tests
GLES1_EXTENSION_EGL_IMAGE_EXTERNAL := 1
GLES2_EXTENSION_EGL_IMAGE_EXTERNAL := 1

# Specify the output directories
BIN_DESTDIR := /usr/bin
SHARE_DESTDIR := /usr/bin

# Disable Buffer Class
PVR_LWS_NOBC := 1

PVR_NO_OMAP_TIMER := 1

PVR_SYSTEM := omap

KERNEL_COMPONENTS := srvkm

# Only enable active power management if passive power management is
# enabled, as indicated by LDM_PLATFORM being set to 1.  On OMAP,
# the system can suspend in the case where active power management is
# enabled in the SGX driver, but passive power management isn't. As
# passive power management isn't enabled, the driver won't see the
# system suspend/resume events, and so won't take appropriate action.
LDM_PLATFORM := 1
SUPPORT_LINUX_USING_WORKQUEUES := 1

# Compiler args for this platform
ARCH := arm64
SYS_CFLAGS := -march=armv8-a
SYS_CXXFLAGS := $(SYS_CFLAGS)
SYS_LDFLAGS := $(SYS_CFLAGS)

SGX_DYNAMIC_TIMING_INFO := 1
SYS_CUSTOM_POWERLOCK_WRAP := 1

include ../common/xorg_test.mk
include ../kernel_version.mk

XORG_EXPLICIT_PVR_SERVICES_LOAD := 1
SUPPORT_DRI_DRM := 1
PVR_LDM_DEVICE_TREE := 1
PVR_DRI_DRM_PLATFORM_DEV := 1
SUPPORT_DMABUF := 1

PVR_DRM_MODESET_DRIVER_NAME := tidss
PVR_DRM_MODESET_MODULE_NAME := dumb

# No display class driver.
DISPLAY_CONTROLLER_COMPONENT :=
DISPLAY_CONTROLLER :=

include ../config/core.mk
include ../common/xorg.mk
include ../common/dridrm.mk
include ../common/opencl.mk
include ../common/omap4.mk
