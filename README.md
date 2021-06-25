Exar USB Serial Driver
======================
Upstream source:
https://www.maxlinear.com/support/design-tools/software-drivers


#### Version 1C-BH  2021/6/12
* Fix errors in code.   
* Update to support kernel 5.x
* Add udev rules to load correct module/unload cdc_acm

#### Version 1C  2017/1/11
* Add the 9-bit mode support.
* Disbale the debug messages.

#### Version 1B, 11/6/2015
* Fixed Bug: The conditional logic to support kernel 3.9 was incorrect(line 396 in xr_usb_serial_common.c). 

#### Version 1A, 1/9/2015

### This driver will work with any USB UART function in these Exar devices:
* XR21V1410/1412/1414
* XR21B1411
* XR21B1420/1422/1424
* XR22801/802/804

The source code has been tested on various Linux kernels from 3.6.x to 3.17.x.  
This may also work with newer kernels as well.  


Installation
------------

1) Compile and install the common usb serial driver module
* make
* make modules_install

2) Copy udev rules from folder udev_rules, see  README in that subfolder
3)  Plug the device into the USB host.  You should see up to four devices created,
  typically /dev/ttyXRUSB[0-3].


Tips for Debugging
------------------

1) Check that the USB UART is detected by the system
* lsusb

2) Check that the CDC-ACM driver was not installed for the Exar USB UART
* ls /dev/tty*
To remove the CDC-ACM driver and install the driver:

* rmmod cdc-acm
* modprobe -r usbserial
* modprobe usbserial
* insmod ./xr_usb_serial_common.ko


Technical Support
-----------------
Send any technical questions/issues to uarttechsupport@exar.com. 

