# WASI USB

A proposed [WebAssembly System Interface](https://github.com/WebAssembly/WASI) API.

### Current Phase

WASI USB is currently in Phase 1

### Champions

<!---
Please limit to one champion per company or organization
-->
- Merlijn Sebrechts
- (Wouter Hennen)
- (Warre Dujardin)

### Portability Criteria

TODO before entering Phase 2.

## Table of Contents [if the explainer is longer than one printed page]

- [Introduction](#introduction)
- [Goals [or Motivating Use Cases, or Scenarios]](#goals-or-motivating-use-cases-or-scenarios)
- [Non-goals](#non-goals)
- [API walk-through](#api-walk-through)
  - [Use case 1](#use-case-1)
  - [Use case 2](#use-case-2)
- [Detailed design discussion](#detailed-design-discussion)
  - [[Tricky design choice 1]](#tricky-design-choice-1)
  - [[Tricky design choice 2]](#tricky-design-choice-2)
- [Considered alternatives](#considered-alternatives)
  - [[Alternative 1]](#alternative-1)
  - [[Alternative 2]](#alternative-2)
- [Stakeholder Interest & Feedback](#stakeholder-interest--feedback)
- [References & acknowledgements](#references--acknowledgements)

### Introduction

The WASI USB proposal adds an API for controlling USB devices. The API is meant to be used to with any kind of USB device, and is more low-level than, for example, accessing USb devices through the filesystem. The API design is based on the [libusb](https://libusb.info/) library, which is an often-used library for accessing USB devices in native programs. Just like libusb, this API aims to be a thin wrapper around the USB standard and Operating System APIs, with improved ergonomics where necessary. Access control can be applied to limit the devices a component can access.

### Goals [or Motivating Use Cases, or Scenarios]

The goal of the proposal is to offer an API to control USB devices on a low level.

### Non-goals

Support in web browsers is currently not considered. Research was done to evaluate the feasibility, but the conclusion was that while possible, the API would have too much limitations (based on the current support for USB devices in web browsers). See [alternatives](#support-in-web-browsers-with-webusb) for more information.

### API walk-through

The full API documentation can be found [here](wasi-proposal-template.md).

[Walk through of how someone would use this API.]

#### [Use case 1]

[Provide example code snippets and diagrams explaining how the API would be used to solve the given problem]

#### [Use case 2]

[etc.]

### Detailed design discussion

[This section should mostly refer to the .wit.md file that specifies the API. This section is for any discussion of the choices made in the API which don't make sense to document in the spec file itself.]

#### [Tricky design choice #1]

[Talk through the tradeoffs in coming to the specific design point you want to make.]

```
// Illustrated with example code.
```

[This may be an open question, in which case you should link to any active discussion threads.]

#### [Tricky design choice 2]

[etc.]

### Considered alternatives

#### Support in web browsers with WebUSB
Being able to use the API in web browsers would be a nice thing to have, but after experimenting with this idea, it deemed not useful enough. Some points why:
- The implementation would be a wrapper around WebUSB. WebUSB is currently only available on Chromium-based browsers and is not standardized. As a result, a large portion of users would not be able to use the feature, and would be forced to switch to a Chromium-based browser.
- WebUSB is an abstraction over the complete USB API and does not expose everything. For example, it cannot detach kernel drivers, or you cannot read the `bMaxPower` property of the configuration descriptor.
- WebUSB can only be used on non-standard USB devices, limiting the usability of the API. For example, using the WebUSB API is not allowed for accessing mass storage devices or serial devices, like an Arduino

#### [Alternative 1]

[Describe an alternative which was considered, and why you decided against it.]

#### [Alternative 2]

[etc.]

### Stakeholder Interest & Feedback

TODO before entering Phase 3.

[This should include a list of implementers who have expressed interest in implementing the proposal]

### References & acknowledgements

Many thanks for valuable feedback and advice from:

- [Person 1]
- [Person 2]
- [etc.]
