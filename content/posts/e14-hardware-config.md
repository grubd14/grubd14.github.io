---
title: "Hardware configs for Thinkapd E14 Gen4 in linux"
date: 2024-06-28T20:57:17+05:45
categories: ["system-config"]
author: "Sushil"
description: "some system configuration for thinkpad e14 for linux"
showToc: true
canonicalURL: "https://canonical.url/to/page"
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowCodeCopyButtons: true
editPost:
    URL: "https://github.com/grubd14/grubd14.github.io/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
## configs
Some of the changes in my linux distro to make my hardware work in linux

## Wifi Issue
Some of the major hurdles I faced after installing linux on my Thinkpad e14 was of WiFi.
It randomly disconnected after few minutes of use and would again connect if I restarted.
So after hours of searching through the forums and reddit, I landed on one of the fixes that acts like a bandage for a while.
I hope it will be fixed with the newer BIOS update or kernel update.

I passed some kernel parameters by putting the file in modprobe.d folder in /etc .
My config looked like this 

```
options rtw89_pci disable_clkreq=y disable_aspm_l1=y disable_aspm_l1ss=y
```
## ABM feature for display
AMD introduced a new feature for system with intergrated graphics called *Adaptive Backlight Management*. This feature reduced the contrast of display in poweer
saving mode in exchange for lower power consumption by the panel. Since KDE has no GUI that supports disabling the feature off. I passed some kernel parameters 
that disabled this feature.
config situated in /etc/modprobe.d/ 
```
options amdgpu abmlevel=0
```
