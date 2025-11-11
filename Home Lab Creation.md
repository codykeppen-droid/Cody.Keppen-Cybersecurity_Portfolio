  # Cybersecurity Home Lab Creation

## Project Goal
To create a home lab to experiment and learn different tools for cybersecurity. I had my old computer sitting around that I decided to use for this project. This is an in progress project that I started on 11/02/2025.

Main skillsets to build on:
* Linux
* Creating VM's
* SIEMs
* Sandboxing
* Attacking vulnerable systems

## Host Machine Setup
* Hardware:
  *  H110I Pro (MS-7995)
  *  i5-6500
  *  Radeon RX 470
  *  16GB Ram
  *  8TB HHD
  *  2TB SSD
  *  TP-Link Archer TX2OU NANO
* Host OS: Ubuntu 24.04 LTS
## Actions setting up Home Lab
### Installing Linux
* Downloaded Ubuntu 24.04 LTS ISO on different device.
* Created a bootable USB drive using Balena Etcher.
* Installed Ubuntu on home lab, wiping the disk for a clean install.
### Wi-Fi Issue
At installation, no internet device was found when prompted to setup internet. There was at a step to use internet connection to download updates. I was using a Wi-Fi adapter and realized that it was not working with Linux.
* Issue to resolve: TP-Link Wi-Fi adapter wasn't recognizeable
  * Consulted AI as to why new adapter wasn't working.
  * Issue discovered: TP-Link Wi-Fi Realtek drivers not included in Linux kernal.
  * Solution: Tether mobile phone to get internet, then download RealTek driver.
  * Steps taken:
    *  Used `lsusb` to list USB devices and find the chip used for my Wi-Fi adapter.
    *  Once I discovered the ID number for the device, I used AI to discover the chipset.
    *  Ran `sudo apt update && sudo apt install git dkms build-essential linux-headers-$(uname -r)`, to prepare for driver installation.
    *  Ran `wget https://github.com/morrownr/rtl8852bu-20240418/archive/refs/heads/main.zip` to download the driver.
    *  Extracted the zip file with, `unzip main.zip`.
    *  After switching to the downloadeded file `cd rtl8852bu-20240418-main`, ran the installation script, `sudo ./install-driver.sh`.
    *  Ran into an issue in which I need to install the wireless utility iw, `sudo apt install iw`.
    *  Then ran installer again, `sudo ./install-driver.sh`, this time successfully.
    *  Rebooted computer and had the ability to connect to my router.
*  Issue resolved: Internet connection established.

### Finish Full System Update and Enable Firewall
With internet established without tethering my phone, the next step is to finish the system update that didn't occur at installation. Ran `sudo apt update && sudo apt upgrade`. Then I enabled the firewall with `sudo ufw enable`.
  
