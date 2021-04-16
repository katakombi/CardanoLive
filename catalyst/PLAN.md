# Project Plan

## Intended Usage

* User prepares the USB stick using HOWTO/script. This has to be as easy as possible.
* User copies ISO file/shasum/signature on the USB stick
  * ISO file release downloaded from github and to be verified by 3rd-party GPG signature
  * optionally: Create own CardanoLinux ISO file
* User connects USB stick on PC/notebook and boots from USB into CardanoLinux
* User is asked to run an initial setup
  * encryption password for /home
  * run an initial guided Yoroi/Daedalus installation
  * setup wallets and downloads blockchain
* User can stake/unstake/redelegate/receive/send Ada
* After usage power down the PC
* If multiple sticks are desired it can be duplicated by cloning the system partition on a stick with a similar size

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
* Update Daedalus/Yoroi and resync Blockhain

Create a documentation for the most important of these use cases.

## Security & Encryption

## Generally speaking
* system can be securely updated from within

### /home encrypted
* system is considered safe to use as long as the user does not hand out the USB stick
* when others get hold on the USB stick they could replace the system with a malicious one

### fully encrypted
* impossible for others to replace the system with a malicious one
* makes the initial setup probably too complicated for newbies - no easy way known as of now!

## Concepts

* Design a procedure to derive CardanoLive from a trusted LTS image with maximum transparency in mind so that a 3rd party can provide or sign an image
* Design and document a CardanoLive ISO upgrade procedure
* Design and propose a sustainability model for ensuring continuous upgrades
* Design how data can be exchanged between CardanoLinux and an external system. Which data is ok to share?

## Tasks

* Establish contacts in discord/ ask for feedback
* Performance experiments on IO-speeds wrt running Daedalus
* Create a live user /home template
* Create a linux system based on an official LTS release secured and stripped down to the bare minimum
* Create a HOWTO/script for a reproducible build of the bootable CardanoLinux live system iso file based on a LTS release
* Ask a trustworthy third party (e.g. IOHK) to sign the image in addition - HOW can this be achieved?
* Create an ISO file released + sha512 checksum signed with both own GPG key and the GPG key of the trustworthy third party
  * with system in ramdisk - all temporary changes being lost after reboot
* Design and implement a secure genuineness check during boot up? is this even possible?
* Create a HOWTO/script to produce the bootable usb stick using a bootable live linux ISO
  * with password encryption
  * with separate /home partition - persistent data
  * with verified CardanoLive ISO image

## Ideas to investigate further

 * For creation of USB stick: https://www.ventoy.net/en/doc_start.html
 * Remove software/services that are not needed for use cases
 * Restrict internet to certain applications / websites
 * Firefox+Yoroi without cookies/http/ads/js.. as far as possible
 * Blocking most internet traffic by firewall except https/dns/ntp and what else will be needed
 * AppArmor? FF
 * noexec for /tmp and /home - think of the exceptions: Daedalus/Yoroi/FF extensions? 

# Catalyst Proposal Calculation - TODO 
 * what exactly will the requested 2500USD be spend for?
 * illustrate expenses in detail
