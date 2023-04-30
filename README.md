# Xiaomi-4A-100M-R4AC-ImmortalWrt
A detailed guide on installing ImmortalWrt on Xiaomi 4A 100M International Version.

[ImmortalWRT](https://github.com/immortalwrt/immortalwrt) is fork of OpenWrt that offers better performance and compatibility.
## Step 1
Install the chinese version of the firmware ***2.18.58*** (if already installed you can skip this part). Use the files from [here](https://drive.google.com/drive/folders/1FVCrAYYcd9zHmXlEv1CZxXRrr1En4f0j?usp=share_link) and [this](https://www.youtube.com/watch?v=SLbkce-M2nE) video tutorial to flash the chinese firmware. Setup the router and note the password you have used.
## Step 2
* Head over [here](https://downloads.immortalwrt.org/releases/21.02.5/targets/ramips/mt76x8/immortalwrt-21.02.5-ramips-mt76x8-xiaomi_mi-router-4a-100m-squashfs-sysupgrade.bin) and download the ImmortalWrt snapshot firmware. Rename the file to firmware.bin for easier identification.
* Using a linux/GNU or Mac cli, clone the root shell exploit for the router using git clone https://github.com/acecilia/OpenWRTInvasion.git
* Then ***cd OpenWrtInvasion/***
* ***pip3 install -r requirements.txt***
* ***python3 remote_command_execution_vulnerability.py***
(The default router i.p is 192.168.31.1)
+ NB! **Do not close the terminal at this stage**
## Step 3
+ This step involves copying the firmware.bin into the router for installation.
+ Using filezilla ***(sudo apt install filezilla)***, or any alternative software, open and head over and type **192.168.31.1** in the host section.
+ The password is root and username is root
+ Scrool on the right-hand panel and locate /tmp and copy the firmware.bin to that location.
## Step 4
+ Back in the terminal/cli, type in ***telnet 192.168.31.1***
+ username is root and password is root
+ ***cd /tmp***
+ check sha using: ***./busybox sha256sum firmware.bin***
+ Install firmware using: ***mtd -e OS1 -r write firmware.bin OS1***
+ Wait for the process to complete uninterrupted until all led lights blue.
+ You can now access the ImmortalWrt interface via **192.168.1.1** 
