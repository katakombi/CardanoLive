# Project Plan

## Intended Usage

* User prepares the USB stick using HOWTO/script
* User copies ISO file/shasum/signature on the USB stick
  * ISO file release downloaded from github and to be verified by 3rd-party GPG signature
  * optionally: Create own CardanoLinux ISO file using reproducible build
* User connects USB stick on PC/notebook and boots from USB into CardanoLinux
* User is asked to run an initial setup
  * encryption password for /home
  * install 3rd party GPG key under /home for continuous genuineness check
  * run an initial guided Yoroi/Daedalus installation
  * setup wallets and downloads blockchain
* User can stake/unstake/redelegate/receive/send Ada
* After usage power down the PC
* If multiple sticks are desired it can be duplicated by cloning the system partition on a stick with a similar size

## Tasks

* Performance experiments on IO-speeds wrt running Daedalus
* Create a live user /home template
* Create a linux system based on an official LTS release secured and stripped down to the bare minimum
* Create a HOWTO/script for a reproducible build of the bootable CardanoLinux live system iso file based on a LTS release
* Ask a trustworthy third party (e.g. IOHK) to run the reproducible build
* Create an ISO file released + sha512 checksum signed with the GPG key of the trustworthy third party
  * with system in ramdisk - all changes being lost when restarted
* Design and implement a secure genuineness check during boot up
* Create a HOWTO/script to produce the bootable usb stick using a bootable live linux ISO
  * with password encryption
  * with separate /home partition - persistent data
  * with verified CardanoLive ISO image

## Concepts

* Design and document a CardanoLive ISO upgrade procedure
* Design and propose a sustainability model for ensuring continuous upgrades
* Design how data can be exchanged between CardanoLinux and an external system. Which data is ok to share?

## Use Cases

* create Ada wallet in Daedalus/Yoroi
* send Ada from exchange to Daedalus/Yoroi
* send Ada from Daedalus/Yoroi to exchange
* stake Ada wallet
* unstake Ada wallet
* export Staking Rewards
* send Ada to a contact
* hand out an receiving address to a contact
* Exchange data (ADA addresses/csv/pubkey) between Cardano Linux and other systems (WinPC,IOS,Android)

Create a documentation for the most important of these use cases.

## Ideas how to enhance security

* Remove software/services that are not needed for use cases
* Restrict internet to certain applications / websites
* Firefox+Yoroi without cookies/http/ads/js.. as far as possible
* Blocking most internet traffic by firewall except https/dns/ntp and what else will be needed
* AppArmor? FF
* noexec for /tmp and /home - think of the exceptions: Daedalus/Yoroi/FF extensions?

## To investigate further
https://www.ventoy.net/en/doc_start.html


# Catalyst Proposal Calculation - TODO 
 * explain expenses of requested 2500USD
 * what exactly will be funded
