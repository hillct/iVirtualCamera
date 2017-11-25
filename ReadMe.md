# iVCam - A virtual camera for macOS

By the present of CoreMediaIO framework, we can create virtual camera for some purposes. Many applications use virtual camera to handle camera video stream such as **ManyCam**, **CamTwist**, **CamMask** and etc.

## How to make it work:

* Download and compile the project. You may need keep your XCode updated.
* Move **\*.plugin to /Library/CoreMediaIO/Plug-Ins/DAL/**, move **\*.kext to /System/Library/Extensions/**.
* Load the kernel extension manually using following commands:

```
$ sudo chown -R root:wheel IOVideoSample.kext      
$ sudo kextunload IOVideoSample.kext
$ sudo kextload IOVideoSample.kext

```
* Open **OBS Studio** or other client application to preview virtual camera.
NOTE: After installation, you should wait for a while before the virtual camera driver loaded. If everything goes well, you will see the following placeholder image:

![](https://raw.githubusercontent.com/csuft/iVCam/master/Screenshots/Snip20171125_1.png)  

![](https://raw.githubusercontent.com/csuft/iVCam/master/Screenshots/Snip20171125_2.png)  
Right, the driver supports only one resolution `1472x828` with YUV format. Of course, you can change it as you wish. But first you have to dive into the implementation.

NOTE AGAIN: If you want to redistribute your own version, you have to apply certificates from Apple([view](https://developer.apple.com/developer-id/))  
![](https://raw.githubusercontent.com/csuft/iVCam/master/Screenshots/Snip20171125_3.png)

## What is CoreMediaIO:

The CoreMediaIO Device Abstraction Layer (DAL) is analogous to CoreAudio’s Hardware Abstraction Layer (HAL). Just as the HAL deals with audio streams from audio hardware, the DAL handles video (and muxed) streams from video devices.
This SDK will demonstrate how to create a user-level DAL plugIn, a user-level “assistant” server process that allows the device to vend its video data to several processes at once, and a kernel extension (KEXT) for manipulating the device’s hardware.

## Copyright
Copyright (C) 2012 Apple Inc. All rights reserved.
