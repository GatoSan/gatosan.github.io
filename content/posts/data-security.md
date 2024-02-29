+++
title = "Data security"
date = "2024-02-29"
+++

## Format drive - everything done?

Unfortunately not. As it might seem on first glance that formatting solves the problem of removing data from a drive, it only creates a new partition whereas the data itself remains on the drive. There are many tools out in the field, that are able to recreate the original data from such kind of devices.

To overcome this topic, I will show how someone can delete the data in a save way by using different Linux tools.

## Preperation

Insert the new device (e.g. an USB stick) and check the device.

```bash
lsblk
```

TODO - add info here

```bash
sudo umount /dev/sda1
```

## Clean up the device

TODO - info

### Use the dd command

```bash
sudo dd if=/dev/zero of=/dev/sda bs=4096 status=progress
```
Info - enough for most use-cases. The more secure way comes here:

```bash
sudo dd if=/dev/urandom of=/dev/sda bs=4096 status=progress
```
In both cases -> *no space left on device* information

### Use the shred command

By default three different runs with random data.

```bash
# basic command
sudo shred -v /dev/sda

# overwrite the storage with zeros in the last run
sudo shred -v -z /dev/sda

# use random information and reduce the number of runs to 2
sudo shred -v -z --random-source=/dev/urandom -n2 /dev/sda
```

## Create a new partition

```bash
sudo fdisk -l
```
Select the device

```bash
sudo fdisk /dev/sda
```
TODO - show commands in detail

```bash
sudo mkfs.vfat -F 32 /dev/sda1
```

## Hiding data

TODO - information

```bash
# install the package
sudo apt update
sudo apt install steghide

# embed a file into an image
steghide embed -cf myimage.jpg -ef secretfile.txt

# get information from the prepared file without extraction
steghide info myimage.jpg

# extract the secret file
steghide extract -sf myimage.jpg
```
