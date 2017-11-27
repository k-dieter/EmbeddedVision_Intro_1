 # Embedded Vision
## Session 2 LAB1
Version 1.0, 11/26/2017
(c) Dieter Kiermaier, Creative Commons BY-CN 3.0 license

**Downloading and install pylon for aarch64 on DB4**

```shell
Sadly we need to use the browser to download the pylon .deb file because we need to fill in some data:

1) Open the website:
https://www.baslerweb.com/en/support/downloads/software-downloads/pylon-5-0-11-linux-arm-64-bit-debian/
2) store the selected file in your project directory
3) install the debian package with following command:
dieter:> sudo dpkg --install xyz
```

Default installation dir is /opt/pylon

To ensure if the installation is working correct and to verify correct operation of the camera we do a quick test by starting pylon viewer and test if we can get images:

**Connect the camera to a free USB port of the DB4 and check the output of dmesg**
 
```shell
dieter:> dmesg | grep Basler

```
**Start pylonViewer**

```shell
dieter:> cd /opt/pylon/bin
dieter:> ./pylon-Viewer
```

The output needs to look as shown below:
![pylonViewer](./Images/Screenshot_20171127_233842.png  "pylonViewer")

**Setup pylonViewer**

To display images we need to select the camera and press the "aquire image" button:


