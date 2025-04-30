---
layout: post
title:  "Alternative, safe way to jailbreak iOS 6.1.6 – answer"
categories: apple
tags: [tech, apple, jailbreak, boot, legacy]
weight: 2
---

## Legacy Jailbreak Procedure

1. Get a physical desktop/laptop running older Windows, ideally 32-bit (not 64-bit), to ensure driver interoperability with older iTunes and jailbreaking tools. The jailbreaking tools rely on iTunes metadata, which is saved in the registry, but information gets misinterpreted on 64-bit OS.
	
	* Tip: Avoid VirtualBox. For some reason (at least for me), VirtualBox USB passthrough really struggles with an iPhone (as per VirtualBox 6.1).

2. Fresh install iTunes either [v11.4 on archive.org](https://archive.org/details/i-tunes-setup-11.4.0.18-32-bit) or [v12.0.1](https://discussions.apple.com/thread/6835364). This is because from iTunes 12.**1**, some internal logic within iTunes was changed just enough to make jailbreaking tools malfunction

3. Download precisely [iOS version 6.0 flash file](https://ipsw.me/6.0) for your device. It will come in handy later.

4. [Optional] Get [f0recast](https://ih8sn0w.com/index.php/products/view/f0recast.snow). The tool can come in handy if things go wrong.

5. Follow this [long guide](http://www.iphonehacks.com/2014/03/jailbreak-ios-6-1-6-redsn0w-p0sixspwn.html). Important points,
    * All jailbreak tools should be run with **Administrator rights** and in **Windows XP SP3 compatibility mode**
    * If you want to software-unlock your iPhone, make sure to downgrade the baseband when prompted
    * Use the flash file from step 3 within redsn0w. (Experimental) If it asks about Bootloader version and manufacturing date, say "Yes"
    * If you get an error like "Could not find file `profile.mylist`" –  the firmware was not attached in step 3
    * Sometimes, the restarting jailbreak part ("Extras" → "Just boot") may take several attempts (it likes to get stuck on "Waiting for reboot), Although feel free to retry, ALWAYS make sure the flash file is attached (no need to reattach)

6. To avoid any issues due to dated preset packages: once you can run Cydia, update all Essential packages. Then update all packages. Then redeploy Cydia via "Just run" just like before.

7. After hacked reboot, search for the package called "p0sixpwn" and install it. It should be on Cydia/Telesphoreo. This package will untether the jailbreak. And... the task is finally complete.

### A few extra tips,

* One of the most important tweaks for the old iPhones – "Speed Intensifier". Although designed for iOS, it can help our old iPhone really shine. Surprisingly, it works flawlessly on iOS 6.

* AppSync (install any IPA files), as per version 72.0 still supports iOS 6. You can get it on `http://cydia.angelxwind.net` or `http://repo.hackyouriphone.org`

* ultrasn0w (unlock from all carriers) is no longer readily available. The last public version is 1.8.5, and it is still available on odd websites online and [Momentum-Dev Cydia Repository](https://mtmdev.org/).
