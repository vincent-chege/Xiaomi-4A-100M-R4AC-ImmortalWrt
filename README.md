# Xiaomi-4A-100M-R4AC ImmortalWrt Installation Guide

![Xiaomi 4A 100M](https://i02.appmifile.com/943_operator_sg/24/05/2021/169e85c0188f0c2eadea0f2142f7f71d.png)

## Introduction

Welcome to the Xiaomi 4A 100M ImmortalWrt installation guide! This step-by-step tutorial will walk you through the process of installing ImmortalWrt, a powerful and performance-enhanced fork of OpenWrt, on your Xiaomi 4A 100M International Version router. ImmortalWrt offers improved compatibility and a host of additional features, making it an excellent choice for customizing your router's firmware.

## Disclaimer

Please note that installing third-party firmware on your router carries inherent risks. Proceed with caution, and be aware that improper installation or mistakes during the process may potentially result in bricking your device. Follow the instructions carefully and at your own risk.

## Step 1: Prepare the Chinese Stock Firmware

If your router does not already have the Chinese stock firmware version **2.18.58**, you'll need to flash it first. Don't worry; we've got you covered with a helpful video tutorial and the necessary files. Follow these steps:

1. Use the files provided in [this Google Drive folder](https://drive.google.com/drive/folders/1FVCrAYYcd9zHmXlEv1CZxXRrr1En4f0j?usp=share_link) and the [video tutorial](https://www.youtube.com/watch?v=SLbkce-M2nE) to flash the Chinese firmware onto your router.
2. Complete the setup process and take note of the password you've used during the installation.

## Step 2: Download and Prepare ImmortalWrt Firmware

Now, let's get ImmortalWrt ready for installation. Follow these steps:

1. Head over to the ImmortalWrt download page: [ImmortalWrt Download](https://downloads.immortalwrt.org/releases/21.02.5/targets/ramips/mt76x8/immortalwrt-21.02.5-ramips-mt76x8-xiaomi_mi-router-4a-100m-squashfs-sysupgrade.bin).
2. Alternatively, you can use the [Firmware Selector](https://firmware-selector.immortalwrt.org/) to get the latest version specifically for your Xiaomi Mi Router 4A 100M Edition. Rename the downloaded file to `firmware.bin` for easier identification.
3. Next, use a Linux/GNU or Mac command-line interface (CLI) and clone the root shell exploit for the router using the command: `git clone https://github.com/acecilia/OpenWRTInvasion.git`.
4. Change directory to the cloned repository: `cd OpenWrtInvasion/`.
5. Install the required dependencies: `pip3 install -r requirements.txt`.
6. Execute the remote command execution vulnerability script: `python3 remote_command_execution_vulnerability.py` (The default router IP is 192.168.31.1).
   - **NB!** Do not close the terminal at this stage, as we'll need it later.

## Step 3: Copy ImmortalWrt Firmware to the Router

With the necessary preparations completed, it's time to copy the ImmortalWrt firmware to your router. Follow these instructions:

1. Use FileZilla (or any alternative software) to connect to your router's IP address `192.168.31.1` (Install FileZilla with `sudo apt install filezilla` if needed).
2. Use the username and password as follows: Username: `root` Password: `root`.
3. Navigate to the right-hand panel and locate `/tmp`, then copy the `firmware.bin` file to this location.

## Step 4: Install ImmortalWrt Firmware

It's installation time! We'll now install the ImmortalWrt firmware on your Xiaomi 4A 100M router. Follow these steps:

1. Go back to the terminal or CLI and access your router via Telnet: `telnet 192.168.31.1`.
2. Use the username and password as before: Username: `root` Password: `root`.
3. Change directory to `/tmp`: `cd /tmp`.
4. Check the SHA256 hash of the firmware.bin file: `./busybox sha256sum firmware.bin`.
5. Install the firmware with the following command: `mtd -e OS1 -r write firmware.bin OS1`.
6. Wait for the installation process to complete without interruption until all LED lights turn blue.
7. Once the installation is successful, you can access the ImmortalWrt interface by going to `192.168.1.1` in your web browser.

## Wrapping Up

Congratulations! You've successfully installed ImmortalWrt on your Xiaomi 4A 100M router. With ImmortalWrt's enhanced performance and compatibility, you can now explore and enjoy the vast possibilities of customizing your router to suit your specific needs.

If you encounter any issues or have questions, feel free to explore the ImmortalWrt community and forums for support. Happy networking and exploring with ImmortalWrt!
