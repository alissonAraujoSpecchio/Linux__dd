# Linux__dd
How to boot a pendrive using dd command


## Umount partition

Find usb partition with df -m, it can be identified by the size.

```
[alisson-araujo@localhost ISOs]$ df -m
Sist. Arq.     Blocos de 1M  Usado Disponível Uso% Montado em
devtmpfs               3920      0       3920   0% /dev
tmpfs                  3938     56       3883   2% /dev/shm
tmpfs                  3938      2       3937   1% /run
/dev/sda2            468606 155905     312701  34% /
tmpfs                  3938      1       3938   1% /tmp
/dev/sda1               470    218        253  47% /boot
tmpfs                   788     14        774   2% /run/user/1002
/dev/sdb1              7679   3809       3871  50% /run/media/alisson-araujo/MULTIBOOT
```

It’s important to find the correct partition, because an error here can be very harmfull for the machine (in this case its the /dev/sdb1).
Once it was found, there are two important points to know, the "Sist. Arq." and the "Montado em"
First take notes or remember the path that is in "Sist. Arq.", later umount the media passing the path that is in "Montado em":

```
umount /run/media/alisson-araujo/MULTIBOOT
```

## Format pendrive

After that, go to the folder where the ISO is and run the command dd passing the following parameters:

if: input file, put the Iso name(path) here;

of: output file, put the path that was in "Sist. Arq." whithout the number;

Example: if the path was /dev/sdb1, just put /dev/sdb in the dd comand.

The other parameters just do like the example:

```
cd path_to_iso

sudo dd if=ubuntu-20.04.2.0-desktop-amd64.iso of=/dev/sdb bs=1M conv=sync status=progress
```
