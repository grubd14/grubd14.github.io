---
title: "Setting up and managing btrfs filesystem"
date: 2023-12-26
categories: ["system-tools"]
author: "Sushil"
showToc: true
description: "snapshots using btrfs"
canonicalURL: "https://canonical.url/to/page"
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowCodeCopyButtons: true

editPost:
    URL: "https://github.com/grubd14/grubd14.github.io/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link

---
![btrfs](/images/btrfs.png#center)

# BTRFS
BTRFS is also computer storage format among the sea's of formats available in the linux world.
It is prnounced as better FS or buttter FS as I would like to pronounce it.
It has its advantages over the traditional ext4 system that everbody uses snapshots.
I will only be taling about snapshots in this blog because I myself doesn't know about BTRFS much and 
here we will be trying out the snaphot capabilities of BTRFS.

## prerequisites
The snapshot tools that are going to be mentioned and the methods only pertains to arch linux. This tools and 
method absolutely can be used in any distro's until and unless you know what you are doing.
I have already setup a clean arch install with btrfs sub-volumes mounted with the help of archinstaller.

### setup some tools before starting
```sh
snapper
snap-pac
grub-btrfs
```
*Note*: grub is absolutely necessary since systemd-boot does't allow booting into mounted snapshots

*Note*: most of the commands are sraight up copied from the arch wiki. So, it would be better to look for answers there.

### unmount snapshots
```sh
unmount /.snapshots

```
and remove the snapshots directory since it will be created later in again when using snapper

```sh
rm -r /.snapshots/ 
```
### configuring snapper 

To create a snapper config one should have a BTRFS subvloume already exisiting.

to create a snapper config for the root and home sub-volumes here are the commands

```sh
snapper -c config create-config /path/to/subvolume
```
```sh
sudo snapper -c root create-config /
sudo snapper -c home create-config /home 
```

### snapshots limits
The deafult settings provided by snapper might be a lot . So feel free to edit timely snapshots limits in config file.
by going to `/etc/snapper/configs/config` and also go to [arch-wiki](https://wiki.archlinux.org/title/snapper)
on this subject .

### btrfs subvolumes 

```sh 
sudo btrfs subvolume list / 
```
```sh
sudo btrfs subvolume dellete /.snapshots 
sudo mkdir /.snapshots 
```
now we need to mount the /.snapshots 

so first check the disk 
```sh
lsblk 
cat /etc/fstab 
sudo mount -a 
lsblk 
```

### booting into snapper snapshots 
```sh 
sudo btrfs subvol get-default / 
sudo btrfs subvol list / 
```

```sh
sudp btrfs subvol set-default 256 /
sudo btrfs subvol get-default / 
```

### finishing the configuration
remember we installed snap-pac in the first method as a pre-requirements. It's use comes now. 
Try installing a program and you would see a message like pre and post snap when using pacman. This program is specifically useful to 
roll back to previous state or version of program in bleeding edge arch distro.

### steps to roll back 
```sh 
sudo snapper ls 
```
look at the number given to the command that you used to install program and enter the number from that command to next number till the program was installed
and undo the changes
```sh 
sudo snapper undochange 4..5 
```

This much for now and I will be updating the blog latter on with pictures 
