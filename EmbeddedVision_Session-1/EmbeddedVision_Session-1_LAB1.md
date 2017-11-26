# Embedded Vision
## Session 1 LAB1
Version 1.0, 11/26/2017
(c) Dieter Kiermaier, Creative Commons BY-CN 3.0 license

**Downloading the Debian Installer**

*Refer to 96Boards Website and download the installer image*
```shell
dieter:> wget http://builds.96boards.org/releases/dragonboard410c/linaro/debian/latest/dragonboard410c_sdcard_install_debian-283.zip
…
dieter:> unzip ./dragonboard410c_sdcard_install_debian-283.zip
dieter:> ls
dragonboard410c_sdcard_install_debian-283.zip  EmbeddedVision_Session-1  README.md
```

*Unzip file:*


```shell
dieter:> unzip dragonboard410c_sdcard_install_debian-283.zip 
Archive:  dragonboard410c_sdcard_install_debian-283.zip
  inflating: db410c_sd_install_debian.img  
  inflating: LICENSE                 
```

**Find out the right SD-Card Device**
==Caution: If you chose the wrong device, you might delete your whole harddrive!==

Ensure that SD-Card is not inserted in your PC and run lsblk command:
```shell
dieter:> lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465,8G  0 disk 
├─sda1   8:1    0   450M  0 part 
├─sda2   8:2    0    99M  0 part /boot/efi
├─sda3   8:3    0    16M  0 part 
├─sda4   8:4    0 186,5G  0 part 
└─sda5   8:5    0 278,7G  0 part /
sr0     11:0    1  1024M  0 rom  
dieter:>
```

Now we insert the SD-Card in our PC and run lsblk command again.
Please note that internal SD-Card reader usuall can not be forwarded into a Virtual Machine!

```shell
dieter:> lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465,8G  0 disk 
├─sda1   8:1    0   450M  0 part 
├─sda2   8:2    0    99M  0 part /boot/efi
├─sda3   8:3    0    16M  0 part 
├─sda4   8:4    0 186,5G  0 part 
└─sda5   8:5    0 278,7G  0 part /
==sdc      8:32   1   7,4G  0 disk 
├─sdc1   8:33   1   512K  0 part 
├─sdc2   8:34   1   512K  0 part 
├─sdc3   8:35   1     1M  0 part 
├─sdc4   8:36   1   512K  0 part 
├─sdc5   8:37   1    16K  0 part 
└─sdc6   8:38   1     1M  0== part                                                                                                                                                
sr0     11:0    1  1024M  0 rom                                                                                                                                                 
dieter:>
```

We do see that **/dev/sdc** is the newly recognized device which is our SD-Card.

**Flashing the image**

To flash the image we need to be root - this can be achieved with sudo command:

```shell
dieter:> sudo dd if=./db410c_sd_install_debian.img of=/dev/sdc bs=4M oflag=sync
[sudo] Passwort für dieter: 
962+0 Datensätze ein
962+0 Datensätze aus
4034920448 Bytes (4,0 GB, 3,8 GiB) kopiert, 293,807 s, 13,7 MB/s
dieter:>
```

**Booting the DB4 from SD-Card**

*Assure the DB4 is powered off
Set S6 switch on DB4 to SD Boot
Set switch to 0-1-0-0
Insert the SD Card from the previous step into DB4
Connect HDMI and USB Keyboard / Mouse
Power on the DB4*




