# WASI USB

A proposed [WebAssembly System Interface](https://github.com/WebAssembly/WASI) API.

### Current Phase

WASI USB is currently in Phase 1.

### Champions

<!---
Please limit to one champion per company or organization
-->
- Merlijn Sebrechts
- Wouter Hennen
- Warre Dujardin

### Introduction

The WASI USB proposal adds an API for controlling USB devices. The API is meant to be used to with any kind of USB device, and is more low-level than, for example, accessing USb devices through the filesystem. The API design is based on the [libusb](https://libusb.info/) library, which is an often-used library for accessing USB devices in native programs. Just like libusb, this API aims to be a thin wrapper around the USB standard and Operating System APIs, with improved ergonomics where necessary. Access control can be applied to limit the devices a component can access.

A reference implementation can be found [here](https://github.com/Wouter01/USB_WASI).

### Goals [or Motivating Use Cases, or Scenarios]

The goal of the proposal is to offer an API to control USB devices on a low level.

### Non-goals

Support in web browsers is currently not considered. Research was done to evaluate the feasibility, but the conclusion was that while possible, the API would have too much limitations (based on the current support for USB devices in web browsers). See [alternatives](#support-in-web-browsers-with-webusb) for more information.

### API walk-through

The full API documentation can be found [here](wasi-proposal-template.md).

[Walk through of how someone would use this API.]

### Considered alternatives

#### Support in web browsers with WebUSB

Being able to use the API in web browsers would be a nice thing to have, but after experimenting with this idea, it deemed not useful enough. Some points why:
- The implementation would be a wrapper around WebUSB. WebUSB is currently only available on Chromium-based browsers and is not standardized. As a result, a large portion of users would not be able to use the feature, and would be forced to switch to a Chromium-based browser.
- WebUSB is an abstraction over the complete USB API and does not expose everything. For example, it cannot detach kernel drivers, or you cannot read the `bMaxPower` property of the configuration descriptor.
- WebUSB can only be used on non-standard USB devices, limiting the usability of the API. For example, using the WebUSB API is not allowed for accessing mass storage devices or serial devices, like an Arduino

### References & acknowledgements

Many thanks for valuable feedback and advice from:

- Warre Dujardin
- Wouter Hennen

This work has been partially supported by the ELASTIC project, which received funding from the Smart Networks and Services Joint Undertaking (SNS JU) under the European Union’s Horizon Europe research and innovation programme under Grant Agreement No 101139067. Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union. Neither the European Union nor the granting authority can be held responsible for them. This funding supported individual contributor organisations, not the W3C or this community group as a whole.
