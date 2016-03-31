### Preventing uSD failure

This is an attempt to have all the filesystem mounted via the microSD to be set to **readonly** so that any power cut would not cause corruption.

#### Doing it for logs

Depending on the directory that you mounted your usbdrive on, the path might differ. For mine it will be `/mnt/usbdrive`

```sh
$ mkdir -p /mnt/usbdrive/system/var/log
$ cd /var/log
$ cp -ax * /mnt/usbdrive/system/var/log
```

#### Doing it for docker

```sh
$ sudo service docker stop
$ mkdir -p /mnt/usbdrive/system/var/lib/docker
$ cd /var/lib/docker #use sudo su if you cannot cd into the dir
$ cp -ax * /mnt/usbdrive/system/var/lib/docker
$ sudo nano /etc/default/docker
--> add in this line DOCKER_OPTS="-g /mnt/usbdrive/system/var/lib/docker"
```

#### remounting as rw in case of failure

```sh
sudo mount -o remount, rw / #remounts root dir to rw	
```
