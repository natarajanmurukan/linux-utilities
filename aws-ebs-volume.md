# AWS Mount EBS Volume

Assume you have created EBS volume and attached to EC2 instance. The device_name used is /dev/xvdh then follow the below steps (Used Ubuntu 16 OS)
## Format Volume
>  mkfs -t=ext4 /dev/xvdh
## Create mount point
    mkdir /data
    mount /dev/xvdh /data
## Add entry to fstab to reload device on every reboot
> vi /etc/fstab

Add below line into it
 > /dev/xvdh /data defaults 0 0
