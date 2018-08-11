# Vagrant

How to set centos7 with virtual box Guest Additions

Why you need Guest Additions?

– To mount host system (local) hard drive to vm

– Copy and paste between host and vm



There are images which has Centos 7 and Guest Additions installed. 

Either you can use those images or you can build your own with this Vagrant File. This will let you create your image using official Centos VM with Guest Additions.

Instructions:

1. Download VagrantFile
2. cd path/to/VagrantFile
3. Start the new VM

```vagrant up``` 
4. ssh to a newly created VM.

```vagrant ssh```

5. Once you are in the VM, run below commands to install Guest Additions

```
#!/bin/bash

# install virtualbox guest addition on centos VM

sudo yum -y update
sudo yum -y install wget kernel-headers-$(uname -r) kernel-devel gcc* 
cd /opt
sudo wget -c http://download.virtualbox.org/virtualbox/4.3.40/VBoxGuestAdditions_4.3.40.iso -O VBoxGuestAdditions_4.3.40.iso

cd /opt
sudo mount VBoxGuestAdditions_4.3.40.iso -o loop /mnt
cd /mnt
sudo sh VBoxLinuxAdditions.run --nox11


sudo reboot
```
