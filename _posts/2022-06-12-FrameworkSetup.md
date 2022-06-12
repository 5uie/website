---
layout: post
title:  "Setting up the framework laptop"
date:   2022-06-12 15:07:10 +0530
tags: framework repairability diy open sustainability linux slackware apple
blurb: This is not a review or a guide!
---

## Framework Laptop

In the [previous post]({% post_url 2022-06-05-FrameworkArrived %}), I had very quickly written about my need for a new laptop and the reasoning behind my choice to buy [Framework Laptop]( https://frame.work/). There are several posts and videos available online, please do check them if you’d like to know more about an unboxing experience, a detailed review, or choice of model for the laptop. In this post, I will only be attempting to document the process I followed in order to setup the computer. The post will cover,
- Choice hardware
  - Mainboard
  - SSD
  - RAM
  - Power adapter
- Setting up Linux
  - Choice of distribution
  - How-Tos
  - Gotchas
- Wrapping up
- Setting up a VM with Windows 11 (for the obligatory requirements all of us have)
## Choice of Hardware
Given the possibilities with the laptop, I decided to buy the DIY version of the Framework Laptop
1. Processer: At the time that I placed the order, DIY version of the laptop was only available in the 11th generation of Intel Processors. The two variants available that were of interest to me were the i5-1135G7 and i7-1165G7. While the i7 did have marginally better hardware specifications, the power efficiency of the i5 is much better. Due to my use case and that there was a USD 300 price difference, I decided to buy the i5 variant of the laptop.
2. SSD: I had four choices for RAM, Samsung Pro 980, WD Black 980, WD Black 770 and the SK Hynix P31 Gold (the SK Hynix P41 Platinum wasn’t released yet). As I was moving from an older NVME SSD (first generation), I was keen to see the differences in the newer generation of SSDs. I did finally choose the WD Black 850 as the SK Hynix P31 Gold wasn’t available in my geographic region due to shipping shortages.
3. RAM: Framework has a list of [compatible RAM]( https://knowledgebase.frame.work/what-memory-dram-parts-are-compatible-with-the-framework-laptop-ry_jbS8Ru) on their very useful knowledge base. The key is using non XMP modules that run natively at DDR403200 speed. I tried Samsung, Hynix and Corsair 16GBx2 dual ranked modules (for a total of 32GB) and unfortunately, none of these worked right from the non-native speeds, presence of a heat sink on the RAM and corrupted RAM modules. I eventually settled on a 32 GB (16GBx2) from Crucial that is in the list that Framework has provided.
4.  Power adapter: The DIY nature of this laptop also means that you can use any charger that you already have (as long as it is type-C) and is rated 65W and above. The Framework forum is filled with experiences from people who decided to buy much cheaper travel adapters and at this point it seems to a hit-and-a-miss experience. I was looking to buy a Lenovo or Asus 100W charger (I do not mind the additional weight of the brick and do not need multiple ports on it), as I can then not worry about under-charging or power-drain when I connect multiple accessories to the laptop. Once again, due to availability in my geographic region I have settled on the Asus 100W type-C charger.

## Setting up Linux

My original setup as planned was to be dual booting with UEFI enabled and secure boot disabled for Windows 11 and one Linux distribution. The challenge with this setup did mean that I would not be able to take advantage of the wake-up possibilities offered by Windows (details available as usual on [Arch Wiki]( https://wiki.archlinux.org/title/Dual_boot_with_Windows)). The [guides section]( https://guides.frame.work/c/Framework_Laptop#Section_How-to) by the Framework team documents the OOTB experience for Fedora, Manjaro, Pop!, Ubuntu and Windows 10 & 11. The [Linux section]( https://community.frame.work/c/framework-laptop/linux/91) on the community forum has users documenting their experiences with other distributions such as Arch, Linux Mint, Slackware, Elementary OS and the newly created NixOS among others. Given the new found power of RAM (I couldn’t run even a single DE based Linux on a VM on my MBP due to the limitations of available memory), I decided to abandon dual booting and use Linux as the daily driver. I could run Windows 11 on a VM for all the tasks that I require it for (limited statutory obligations that do not have Linux alternatives but do have MacOS alternatives). 

### Choice of distribution

So, it did boil down to which Linux distribution I would pick. The criteria for the choice of operating system were simple,
1. How well does it play with Framework Laptop? As it is with all laptops, the biggest challenge with any *nix-based system is the availability of drivers, support for video acceleration, encryption, tweaking BIOS and power tuning. In this case, all major distributions seem to work well with Framework based on the discussions in the community forum and the support provided by Framework themselves.
2. Stability vis-à-vis bleeding-edge: I have always erred on the side of stability if it has a fully functioning driver set for my working machine. While Arch seemed to have a thriving community for Framework, this did mean that I had my options as Debian based OSes, Fedora or Slackware.
3. Derivatives: I do appreciate the need for Manjaro, Ubuntu, PopOS, Mint, etc. and the communities they have built. But I prefer to stick to the original distributions as I do not need the additional layers or support provided by these distributions.
4. Package Management: I am a stickler for native running, I do not mind compiling from source or doing dependency checking myself or using dependency-checking scripts to help me. But do not appreciate the bloat provided by Flatpacks and Snaps now.
5. Systemd vs Init: As mentioned before, I was using to init-based systems the last time I was using Linux and am yet to read and understand system based on system. Due to familiarity with these possibilities, it did mean that I stick with init based systems.
6. Urgency: The MBP has a battery bulge that needs urgent attention, so I would need a system that has a decent enough OOTB experience, but I can use as a daily driver with all the tools that I need. Which would mean I need an experience that I am comfortable with and can setup to run quickly.

| **Linux**     | **Drivers** | **Stability** | **Derivative** | **Packages** | **systemd vs init** | **Happiness** |
|---------------|:-----------:|--------------|-----------------|---------------|---------------------|:-------------:|
| **Arch**      | High        | BE           | No              | XXX           | systemd             | Yes           |
| **Manjaro**   | High        | BE           | Yes             | XXX           | systemd             | No            |
| **Mint**      | High        | Stability    | Yes             | XX            | systemd             | No            |
| **Pop\!OS**   | High        | BE           | Yes             | XX            | systemd             | No            |
| **Ubuntu**    | High        | Stability    | Yes             | X             | systemd             | Yes           |
| **Debian**    | High        | Stability    | No              | XX            | systemd             | Yes           |
| **NixOS**     | High        | BE           | No              | X             | systemd             | No            |
| **Fedora**    | High        | Stability    | Not really      | XXX           | systemd             | Yes           |
| **Slackware** | High        | Stability    | No              | XXX           | init                | Yes           |

<br />
And the winner is (obviously, by biased ranking) is Slackware. The freshly released Slackware 15 to boot!

### How-Tos
The only setup guide that I could find for installing Slackware 15 on the Framework Laptop was by Ryan Northrup on his [website]( https://yellowapple.us/2022/02/07/slackware-on-framework.html). I decided to set it up as a simple EXT4 partition system for UEFI boot along with a 64GB swap space. The last time I used Linux I was at ext3, the addition of LUKS and other encryption seems fairly tempting, but I did not want to experiment with it now. I followed the guide and it worked well for me.

### Gotchas
1. Updating kernel: When you first update your kernel, please do make sure to you update initrd. If in case you miss this, you might get a “No kernel modules found for Linux X.X.XX”. In case you get this error, please follow the guide at [Slackware docs]( https://docs.slackware.com/howtos:slackware_admin:systemupgrade), and what worked for me was the details provided by users on [LinuxQestions]( https://www.linuxquestions.org/questions/slackware-14/upgrade-gone-wrong-no-kernel-modules-found-4175685660/#post6187920).
2. Enabling multilib: In case you need multilib support for Steam, Skype or VirtualBox, please do follow the wonderful guide at [Slackware Docs]( https://docs.slackware.com/slackware:multilib).
3. Wayland vs X11: Please note that Wayland is supported by default in Slackware (for KDE). However, a number of applications break and do not work well on Slackware. A consistent challenge for me was the overheating and power drain when I used video calling applications (Zoom, Discord, etc.). Most of these issues were resolved when I switched to xorg. 

## Wrapping up
What is currently working for me?
- Sleep: Setup “nvme.noacpi=1” kernel parameter for [greater performance](https://community.frame.work/t/linux-battery-life-tuning/6665/235)
- Fingerprint reader: Install frpintd from SBO
- Video and Audio: Hard cut off buttons while in calls
- Bluetooth: Works well without audio drop-off after tweaking pipewire a bit
- WiFi: Works well and connects to all networks, speed however is an issue (kernel 5.15.38)
- Audio jack: Works without any glitches and issues.

