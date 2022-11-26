# Introduction
NH: NoaHimesaka1873 MV: mikroskeem NX: networkexception

NH: Hello, I'm Woohyun Cho. I maintain Arch Linux packages and ISOs for t2linux. I also run Linux mirror.  
MV: Hi, I'm Mark - I founded T2Linux Discord community, and was one of the initial testers of Paul Pawlowski (MCMrARM)'s Apple BCE driver. I also maintained NixOS for T2 macs for some time, and still occassionally help people out when needed.  
NX: Well hello, my name is networkException. I've started and maintain the wiki to document everything a user needs to get their t2 system up and running with Linux.  

# Your PC vs a T2 Mac

*take MBP out*

Here's a T2 MacBook Pro. It has an Intel CPU and an AMD GPU, just like a normal PC.

But it's not a normal PC. It has a special chip inside: the T2 chip.

Apple says that it's a security chip. Sure, it does encrypt the internal SSD and it also provides secure boot and the SEP for encryption of important data and Touch ID.

But in reality it controls almost everything in the Mac: the keyboard, trackpad, speakers, headphone jack, etc. You name it.

This chip is based on the Apple A10 and it's completely proprietary with no official driver for Linux.

Do you know how we got Linux to run on T2 Macs? Let's find out.

# How we made it work, more like how we suffered from proprietaryness

Attempts to get Linux running on these machines started on 2018 and the first major advancement was Paul Pawlowski (MCMrARM) getting the internal SSD working. After that, he started reverse engineering the macOS and Windows BootCamp drivers in order to write a Linux driver for communicating with the T2 chip, for which there was no documentation at all.

As many important peripherals are connected to the T2 chip, Paul's driver plays a key role in these Macs. Similar to the macOS and Windows drivers, Paul's driver exposes the peripherals connected to the T2 as virtual USB devices which means that the existing drivers for them work with little modifications.

For other devices, more changes to the drivers were needed. In the case of Wi-Fi, Aun-Ali Zaidi (aunali1) did some work to improve the situation but the driver still needed changes to support using firmware from Big Sur, to read information from the OTP ROM, to select the correct firmware files and to work with newer chips. The state of Wi-Fi improved when Corellium released a linux kernel tree with added support for BCM4378 chips, which are similar to the BCM4377 chips found in some T2 Macs. These patches later got superceded by patches from the Asahi Linux project that supported proper firmware selection and Bluetooth on BCMC4377 chips.

Currently, we are working on improving the quality of the touchbar and T2 bridge drivers. GPU switching without rebooting on dual GPU Macs is also being worked on and we have made a lot of progress. Quirks for secure boot, the built-in NVMe and the GPUs; device IDs for the built-in camera, keyboard backlight support for some models and miscellaneous keyboard bug fixes have been upstreamed by us and the Asahi Linux project has managed to get the BCMC4377 Bluetooth driver accepted. Our goal is to eventually get everything mainlined.

# Demo

Well, now it's time to see this Mac run Linux! Since this is Ubucon, we'll show it run Ubuntu!

*plug Ubuntu stick in, boot to it*

*demonstrate*

# Done?
