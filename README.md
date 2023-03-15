# Implementations

According to the protocol, USB/IP has two roles:

* USB/IP Server: Providing USB Devices, usually implementing USB Device Controller (UDC) and device functions
* USB/IP Client: Using USB Devices, usually implementing USB Host Controller Interface (HCI)

## USB/IP Server

There are quite a few USB/IP Server implementations, with different layers of abstraction implemented.

* usbip-host.ko: Linux Kernel USB device driver, not implementing UDC or device function
* usbip-vudc.ko: Linux Kernel virtual UDC device driver, implementing UDC, device function attached using Linux USB Gadget
* [usbip\_windows](https://sourceforge.net/projects/usbip/files/usbip_windows/): Windows USB device driver, ten years ago from USB/IP homepage, signed driver (signed by ReactOS)
* [dorssel/usbipd-win](https://github.com/dorssel/usbipd-win): Windows USB device driver, not implementing UDC and device function, driver from VBox, signed driver
* [cezanne/usbip-win (usbip\_stub)](https://github.com/cezanne/usbip-win): Windows USB driver, driver self written and self signed
* [jiegec/usbip](https://github.com/jiegec/usbip): written in Rust
  + libusb backend: as if it is a USB driver in libusb compatible platform (e.g. MacOS, BSD, Android, Haiku, Solaris)
  + device: hid keyboard
  + device: cdc acm serial
* [Sawchord/usbip-device](https://github.com/Sawchord/usbip-device): written in Rust
  + device: serial echo
  + device: twitching mouse
* [ellerh/softfido](https://github.com/ellerh/softfido): written in Rust
  + device: FIDO2/U2F authenticator
* [MarkOstis/USBIP-Virtual-USB-Device](https://github.com/MarkOstis/USBIP-Virtual-USB-Device): wrriten in Python
  + device: keyboard
  + device: mouse
* [Gnuk](http://www.fsij.org/doc-gnuk/index.html): using [Chopstx](https://salsa.debian.org/gnuk-team/chopstx/chopstx), which can emulate a whole MCU
  + device: OpenPGP Card V2.0
* [canokeys/canokey-usbip](github.com/canokeys/canokey-usbip): written in C
  + device: U2F / FIDO2 with ed25519 and HMAC-secret
  + device: OpenPGP Card V3.4, [Supported Algorithm List](https://docs.canokeys.org/userguide/openpgp/#supported-algorithm)
  + device: PIV (NIST SP 800-73-4)
  + device: HOTP / TOTP
* [chegewara/esp32-usbip-poc](https://github.com/chegewara/esp32-usbip-poc): written in C++
  + usbip client can access it via a Wifi named "esp32"
  + device: simple usb device (like serial) attached to the ESP32S2/S3 SoC (acting as a USB host)
* [Sawchord/usbip-device](https://github.com/Sawchord/usbip-device), [trussed-dev/pc-usbip-runner](https://github.com/trussed-dev/pc-usbip-runner) and [Nitrokey/nitrokey-3-firmware](https://github.com/Nitrokey/nitrokey-3-firmware): written in Rust
  + device: FIDO
  + device: CCID (OpenPGP, HTOP/TOTP)

## USB/IP Client

* vhci-hcd.ko: Linux Kernel virtual HCI driver
* [cezanne/usbip-win (usbip\_vhci)](https://github.com/cezanne/usbip-win): Windows virtual HCI driver, driver self written and self signed 
* [forensix/libusbip](https://github.com/forensix/libusbip): C library on top of libusb

<!--
Potential implementation ideas:
* libusb with usbip-client
* qemu with usbip-client
-->

## User space tools

* [usbip/usbipd inside Linux source tree](https://github.com/torvalds/linux/tree/master/tools/usb/usbip): get info and manipulate usbip kernel module
* [alunux/usbip-service-discovery](https://github.com/alunux/usbip-service-discovery): GUI
* [USBIPManager](m-antonov/USBIPManager): GUI
