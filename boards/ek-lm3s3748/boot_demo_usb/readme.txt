USB Boot Loader Example

This example application is used in conjunction with the USB boot loader
(boot_usb) and turns the evaluation board into a composite device
supporting the Human Interface Device mouse and Device Firmware Upgrade
classes.  Presses on the navigation control on the evaluation board are
translated into mouse movement and button press messages in HID reports
sent to the USB host allowing the evaluation board to control the mouse
pointer on the host system.

Since the device also publishes a DFU interface, host software such as the
dfuprog tool can determine that the device is capable of receiving software
updates over USB.  The runtime DFU protocol allows such tools to signal the
device to switch into DFU mode and prepare to receive a new software image.

Runtime DFU functionality requires only that the device listen for a
particular request (DETACH) from the host and, when this is received,
transfer control to the USB boot loader via the normal means to reenumerate
as a pure DFU device capable of uploading and downloading firmware images.

Windows device drivers for both the runtime and DFU mode of operation can
be found in <tt>C:/StellarisWare/windows_drivers</tt> assuming you
installed StellarisWare in the default directory.

To illustrate runtime DFU capability, use the <tt>dfuprog</tt> tool which
is part of the Stellaris Windows USB Examples package (SW-USB-win-xxxx.msi)
Assuming this package is installed in the default location, the
<tt>dfuprog</tt> executable can be found in the
<tt>C:/Program Files/Texas Instruments/Stellaris/usb_examples</tt>
directory.

With the device connected to your PC and the device driver installed, enter
the following command to enumerate DFU devices:

<tt>dfuprog -e</tt>

This will list all DFU-capable devices found and you should see that you
have one device available which is in ``Runtime'' mode.  Entering the
following command will switch this device into DFU mode and leave it ready
to receive a new firmware image:

<tt>dfuprog -m</tt>

After entering this command, you should notice that the device disconnects
from the USB bus and reconnects again. Running ``<tt>dfuprog -e</tt>'' a
second time will show that the device is now in DFU mode and ready to
receive downloads.  At this point, either LM Flash Programmer or dfuprog
may be used to send a new application binary to the device.

-------------------------------------------------------------------------------

Copyright (c) 2010-2013 Texas Instruments Incorporated.  All rights reserved.
Software License Agreement

Texas Instruments (TI) is supplying this software for use solely and
exclusively on TI's microcontroller products. The software is owned by
TI and/or its suppliers, and is protected under applicable copyright
laws. You may not combine this software with "viral" open-source
software in order to form a larger program.

THIS SOFTWARE IS PROVIDED "AS IS" AND WITH ALL FAULTS.
NO WARRANTIES, WHETHER EXPRESS, IMPLIED OR STATUTORY, INCLUDING, BUT
NOT LIMITED TO, IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
A PARTICULAR PURPOSE APPLY TO THIS SOFTWARE. TI SHALL NOT, UNDER ANY
CIRCUMSTANCES, BE LIABLE FOR SPECIAL, INCIDENTAL, OR CONSEQUENTIAL
DAMAGES, FOR ANY REASON WHATSOEVER.

This is part of revision 10636 of the EK-LM3S3748 Firmware Package.
