#******************************************************************************
#
# Makefile - Rules for building the USB device audio example.
#
# Copyright (c) 2009-2012 Texas Instruments Incorporated.  All rights reserved.
# Software License Agreement
# 
# Texas Instruments (TI) is supplying this software for use solely and
# exclusively on TI's microcontroller products. The software is owned by
# TI and/or its suppliers, and is protected under applicable copyright
# laws. You may not combine this software with "viral" open-source
# software in order to form a larger program.
# 
# THIS SOFTWARE IS PROVIDED "AS IS" AND WITH ALL FAULTS.
# NO WARRANTIES, WHETHER EXPRESS, IMPLIED OR STATUTORY, INCLUDING, BUT
# NOT LIMITED TO, IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE APPLY TO THIS SOFTWARE. TI SHALL NOT, UNDER ANY
# CIRCUMSTANCES, BE LIABLE FOR SPECIAL, INCIDENTAL, OR CONSEQUENTIAL
# DAMAGES, FOR ANY REASON WHATSOEVER.
# 
# This is part of revision 9107 of the DK-LM3S9B96 Firmware Package.
#
#******************************************************************************

#
# Defines the part type that this project uses.
#
PART=LM3S9B96

#
# Set the processor variant.
#
VARIANT=cm3

#
# The base directory for StellarisWare.
#
ROOT=../../..

#
# Include the common make definitions.
#
include ${ROOT}/makedefs

#
# Where to find source files that do not live in this directory.
#
VPATH=../drivers
VPATH+=../../../utils

#
# Where to find header files that do not live in the source directory.
#
IPATH=..
IPATH+=../../..

#
# The default rule, which causes the USB device audio example to be built.
#
all: ${COMPILER}
all: ${COMPILER}/usb_dev_audio.axf

#
# The rule to clean out all the build products.
#
clean:
	@rm -rf ${COMPILER} ${wildcard *~}

#
# The rule to create the target directory.
#
${COMPILER}:
	@mkdir -p ${COMPILER}

#
# Rules for building the USB device audio example.
#
${COMPILER}/usb_dev_audio.axf: ${COMPILER}/kitronix320x240x16_ssd2119_8bit.o
${COMPILER}/usb_dev_audio.axf: ${COMPILER}/set_pinout.o
${COMPILER}/usb_dev_audio.axf: ${COMPILER}/sound.o
${COMPILER}/usb_dev_audio.axf: ${COMPILER}/startup_${COMPILER}.o
${COMPILER}/usb_dev_audio.axf: ${COMPILER}/tlv320aic23b.o
${COMPILER}/usb_dev_audio.axf: ${COMPILER}/touch.o
${COMPILER}/usb_dev_audio.axf: ${COMPILER}/usb_audio_structs.o
${COMPILER}/usb_dev_audio.axf: ${COMPILER}/usb_dev_audio.o
${COMPILER}/usb_dev_audio.axf: ${COMPILER}/ustdlib.o
${COMPILER}/usb_dev_audio.axf: ${ROOT}/usblib/${COMPILER}-cm3/libusb-cm3.a
${COMPILER}/usb_dev_audio.axf: ${ROOT}/grlib/${COMPILER}-cm3/libgr-cm3.a
${COMPILER}/usb_dev_audio.axf: ${ROOT}/driverlib/${COMPILER}-cm3/libdriver-cm3.a
${COMPILER}/usb_dev_audio.axf: usb_dev_audio.ld
SCATTERgcc_usb_dev_audio=usb_dev_audio.ld
ENTRY_usb_dev_audio=ResetISR
CFLAGSgcc=-DTARGET_IS_TEMPEST_RB1

#
# Include the automatically generated dependency files.
#
ifneq (${MAKECMDGOALS},clean)
-include ${wildcard ${COMPILER}/*.d} __dummy__
endif
