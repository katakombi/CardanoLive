# CardanoLive

Create the live image on a ubuntu oder debian machine.

First install some requirements
```
sudo apt-get install squashfs-tools genisoimage resolvconf
```

Then create the project from scratch

```
WORKDIR="$HOME/Project/CardanoLive"
mkdir -p $WORKDIR/{extract-cd,mnt} && cd $WORKDIR
wget -nc http://mirror.bauhuette.fh-aachen.de/linuxmint-cd/stable/20.1/linuxmint-20.1-mate-64bit.iso
# TODO verify iso
sudo mount -o loop linuxmint-20.1-mate-64bit.iso mnt
sudo rsync --exclude=/casper/filesystem.squashfs -a mnt/ extract-cd
sudo unsquashfs mnt/casper/filesystem.squashfs
sudo mv squashfs-root edit
sudo cp /etc/resolv.conf edit/etc/
sudo mount --bind /dev/ edit/dev
sudo chroot edit
mount -t proc none /proc && mount -t sysfs none /sys && mount -t devpts none /dev/pts
export HOME=/root && export LC_ALL=C 
cd /etc/skel
mkdir Desktop Documents Downloads Music Pictures Public Templates Videos
cd /
```
Your project is ready for modifications, make whatever changes you want like adding or removing software
```
TODO install daedalus yoroi etc
```

Now exit the chroot
```
apt-get clean
apt-get autoremove
rm -rf /tmp/* ~/.bash_history
umount /proc
umount /sys
umount /dev/pts
exit
sudo umount edit/dev
sudo umount mnt
```

The project is ready to build
```
sudo rm -f $WORKDIR/extract-cd/casper/filesystem.squashfs
cd $WORKDIR
sudo mksquashfs edit extract-cd/casper/filesystem.squashfs
sudo vim extract-cd/README.diskdefines
cd extract-cd && sudo rm MD5SUM
find -type f -print0 | sudo xargs -0 md5sum | grep -v isolinux/boot.cat | sudo tee MD5SUM && cd ..
sudo mkisofs -r -V "CardanoLinux" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o CardanoLinux.iso extract-cd && sudo chmod 777 CardanoLinux.iso
```

Ready!
