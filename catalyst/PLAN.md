# Project Plan

## Intended Usage

* User prepares the USB stick using HOWTO/script
* User
  * downloads ISO file release and verifies the GPG signature
  * optionally: User runs reproducible build to produce CardanoLinux ISO file
* User copies ISO file on the USB stick
* User connects USB stick on PC/notebook
* User boots from USB into CardanoLinux
* User is asked to run an initial setup
  * set an encryption password for /home
  * install GPG key and shasum under /home for continuous genuineness check
  * run an initial guided Yoroi/Daedalus installation
  * setup wallets and downloads blockchain
* User can stake/unstake/redelegate/receive/send Ada
* After usage power down the PC

## Tasks

* Create a live user /home template
* Create a stripped down linux system based on an official LTS release
* Create a HOWTO/script for a reproducible build of the bootable CardanoLinux live system iso file based on a LTS release
* Ask a trustworthy third party (e.g. IOHK) to run the reproducible build
* Create an ISO file released + sha512 checksum signed with the GPG key of the trustworthy third party
  * with system in ramdisk - all changes being lost when restarted
* Create a HOWTO/script to produce the bootable usb stick using a bootable live linux ISO
  * with password encryption
  * with separate /home partition - persistent data
  * with verified CardanoLive ISO image

