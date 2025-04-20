---
layout: post
title:  "iMac 12,1 (mid 2011) - Wi-Fi module becomes slow and unstable after sleep on Windows 10 – answer"
date:   2024-12-01 13:51:00 +0100
categories: apple
weight: 2
tags: [tech, apple, mac, bootcamp, wifi]
---

### iMac 12,1 (mid 2011) – Wi-Fi module becomes slow and unstable after sleep on Windows 10 – fix

Through trial and error, I discovered that official drivers offered by Apple (as part of all-in-one driver packages), Microsoft (through Windows Update), and old vendor drivers by Acer, Asus and MSI do demonstrate this issue.

However, there are several known drivers produced by [Honeywell](https://en.wikipedia.org/wiki/Honeywell), produced as late as 2019. At the time of writing, these driver packages are only available on the third-party resources.

* [Package v10.1.7.4 for Windows 7](http://server05.driveridentifier.com/web_upload/uploads/2024-Jan/50123048-012_VM3_Win_7_Milestone_7_10.01.07.0004.zip) ([web.archive.org](https://web.archive.org/web/20241201122234/http://server05.driveridentifier.com/web_upload/uploads/2024-Jan/50123048-012_VM3_Win_7_Milestone_7_10.01.07.0004.zip)) *(the package is also compatible with Windows 10 through compatibility settings)*
* [Package v10.1.10.5 for Windows 10](http://server05.driveridentifier.com/web_upload/uploads/2024-Jan/Win10_x64_Milestone4_10.01.10.0005.zip) ([web.archive.org](https://web.archive.org/web/20241201122601/http://server05.driveridentifier.com/web_upload/uploads/2024-Jan/Win10_x64_Milestone4_10.01.10.0005.zip))

Personally, I found `Package v10.1.7.4 for Windows 7` to be very stable on Windows 10, while `Package v10.1.10.5 for Windows 10` is newer and seems to offer better Honeywell WCU debugging capabilities.

### Installation steps

1. Unzip the .zip file (for example, using 7-zip)
2. [Only if package is not intended for your OS] In the extracted folder, right-click on `Setup.exe` and apply compatibility settings: access "Compatibility" → Run this program in compatibility mode for: "Windows 7" (e.g., for Package v10.1.7.4). You may refer to [the screenshot](https://imgur.com/2KcWze9)
3. In the extracted folder, run `Setup.exe`, and follow the installation steps. This will install Honeywell Wireless Configuration Utilities (WCU) alongside Honeywell wireless drivers compatible iMac 12,1

	<ins>Note</ins>: it should be possible to install these drivers using raw .inf files, too. Honeywell WCU utilities seem to enable wireless debugging, which may come in handy.

4. (Optional) Run `devmgmt.msc`. Access "Network adapters" → "Qualcomm Atheros AR938x Wireless Network Adapter". Select "Driver" tab and observe updated drivers. You should see driver information similar to that in the screenshots below, 

	![10.1.7.4](https://i.imgur.com/o5jTgWt.png) | ![10.1.10.5](https://i.imgur.com/M5oPuvD.png)
	---- | ----
	Package v10.1.7.4 for Windows 7 | Package v10.1.10.5 for Windows 10

At this point, the the Wi-Fi issues are rectified.
