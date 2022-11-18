# Introduction
NH: NoaHimesaka1873 MK: mikroskeem NX: networkexception

NH: Hello, I'm Woohyun Cho. I maintain Arch Linux packages and ISOs for t2linux. I also run Linux mirror. 

*insert your introductions here*

# Your PC vs T2 Mac

*take MBP out*

Here's MacBook Pro. It has normal Intel CPU and AMD GPU. Just like a normal PC.

But it's not a normal PC. It has a very special chip inside. It's called Apple T2.

It controls almost everything of the Mac. Keyboard, trackpad, speaker, headphone jack, etc. You name it.

This chip is based on Apple A10 and it's completely proprietary with no official driver for Linux.

Do you know how we make Linux run on T2 Macs? Let's find it out.

# How we made it work, more like how we suffered from proprietaryness

The T2 chip is of course completely undocumented. There is Windows drivers to make Boot Camp work so we could reverse-engineer it. 

Earlier efforts started in 2019 like aunali1's linux-mbp-arch, roadrunner2's macbook12-spi-driver, and McMrARM's mbp2018-bridge-drv. In the same year, Linux incorporated T2-modified NVMe support into the kernel. Other modules didn't made it. These early out-of-tree modules provided much needed keyboard, trackpad, and Touch Bar support. But those modules were far from perfect. They didn't work reliably, and sometimes outright crashed. Of course, effort for better quality modules continued.

In 2020, t2linux was created. Finally a team dedicated to better support T2 Macs. Also this year, Project Sandcastle was released. It was a project to port Android to the iPhone. How is this relevant? Well, this finally provided working Wi-Fi and Bluetooth for T2 Macs. Those two things weren't supported before due to more modern Broadcom firmware requirement. It worked, but it was far from perfect. Some Wi-Fi chips didn't work despite this. For example, BCM4377.
