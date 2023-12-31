# raspberrypi

## Init rasberrypi

```sh
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg2 software-properties-common vim fail2ban ntfs-3g
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
echo "deb [arch=armhf] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
sudo apt-get update && sudo apt-get install -y docker-ce docker-compose
sudo usermod -a -G docker alexpi
``` 

## format disk
```sh
# list devices
sudo fdisk -l
```

## manager partition table
```sh
sudo fdisk /dev/sda
```

## format partition
```sh
sudo mkfs.ext4 /dev/sda1
```

## mount partition
```sh
sudo mkdir /media/external
sudo mount /dev/sda1 /media/external -t ext4
```

## unmount partition
```sh
unmount mount /media/external
```

# set automount
```sh
sudo blkid # get PARTUUID for the partition
sudo nano /etc/fstab

# add a line with this and set PARTUUID
# PARTUUID=ed25f1e6-01 /media/external ext4 defaults,auto,users,rw,nofail,noatime 0 0
```