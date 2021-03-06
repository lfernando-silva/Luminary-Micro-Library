#******************************************************************************
#
# Makefile - Rules for building the BLDC Motor Application.
#
# Copyright (c) 2008-2013 Texas Instruments Incorporated.  All rights reserved.
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
# This is part of revision 10636 of the RDK-BLDC Firmware Package.
#
#******************************************************************************

#
# Defines the part type that this project uses.
#
PART=LM3S8971

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
VPATH=../../../utils

#
# Where to find header files that do not live in the source directory.
#
IPATH=../../..

#
# The default rule, which causes the BLDC Motor Application to be built.
#
all: ${COMPILER}
all: ${COMPILER}/basic-bldc.axf

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
# Rules for building the BLDC Motor Application.
#
${COMPILER}/basic-bldc.axf: ${COMPILER}/adc_ctrl.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/brake.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/hall_ctrl.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/main.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/pwm_ctrl.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/sine.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/sinemod.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/speed_sense.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/startup_${COMPILER}.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/trapmod.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/ui.o
${COMPILER}/basic-bldc.axf: ${COMPILER}/ui_onboard.o
${COMPILER}/basic-bldc.axf: ${ROOT}/driverlib/${COMPILER}-cm3/libdriver-cm3.a
${COMPILER}/basic-bldc.axf: basic-bldc.ld
SCATTERgcc_basic-bldc=basic-bldc.ld
ENTRY_basic-bldc=ResetISR

#
# Include the automatically generated dependency files.
#
ifneq (${MAKECMDGOALS},clean)
-include ${wildcard ${COMPILER}/*.d} __dummy__
endif
