### Setting up USB drive as blog storage

#### Create a folder to mount the USB drive

```sh
$ mkdir /mnt/usbdrive
```

#### setup automount for the USB drive

```sh
$ sudo blkid
```

This will give up the **UUID** of the USB drive. Example:

```sh
/dev/mmcblk0p1: SEC_TYPE="msdos" LABEL="BOOT" UUID="6E35-5356" TYPE="vfat"
/dev/mmcblk0p2: LABEL="trusty" UUID="e139ce78-9841-40fe-8823-96a304a09859" TYPE="ext4"
/dev/sda1: UUID="20e4884c-ee75-45ce-9a0b-355f3a627277" TYPE="ext4"
```

Next, we will update `/etc/fstab`

```sh
$ sudo nano /etc/fstab
```

Add in a new entry:

```sh
UUID=20e4884c-ee75-45ce-9a0b-355f3a627277 /mnt/usbdrive ext4 errors=remount-ro,noatime,nodiratime 0 0
```

#### reboot and check

We will now restart the system and see if everything is setup properly

```sh
$ sudo shutdown -r now
```

You should see the USB drive and all its content mounted!

```sh
$ cd /mnt/usbdrive
$ ls -l
```
