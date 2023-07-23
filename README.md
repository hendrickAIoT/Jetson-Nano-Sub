# Jetson-Nano-Sub
![output image](http://www.yahboom.net/public/upload/upload-html/1683343213/2023041100003.png))<br/><br/>

![output image](http://www.yahboom.net/public/upload/upload-html/1683343213/2023041100004.png))<br/><br/>
# The Yahboom Repository to download the Jetson Nano Sub 
https://drive.google.com/drive/folders/1Xpq4VjXGxQa8i_JgZJ-0PZxKQbthyef_

For the USB drive startup method, there are several points to note:

1. JetsonThe system version of the Nano core board should correspond to the system version of the USB flash drive.
   For example, if the USB flash drive has already burned version 4.5.1, then
   JetsonThe system version of the Nano core board must also be V4.5.1,
   and the "root=/dev/mmcblk0p1" in the boot/extLinux extlinx.conf file in the EMMC system must be changed to "root=/dev/sda1".
   Otherwise, it cannot be booted from a USB-U drive. Alternatively, follow the "3. Burn EMMC Boot" to burn the boot to ignore version and configuration file modification issues.
   

3. The idea of USB startup is to first start the system on the core board, and then boot the system from the core board onto a USB drive.
4. The system in the core board needs to use SDKManager to burn the system, and the system in the USB drive needs to use Win32DiskImager to burn the system.Reference image:

# 3. Burn EMMC boot
Burn EMMC boot

一、 Jetson Nano Connect Virtual Machine

    Prepare the Jetson nano motherboard, jumper cap, display screen, mouse and keyboard, etc.
    Put Jetson Nano into the system REC flash mode.

	Connect the jumper cap to the FC REC and GND pins, that is, to the second and third pins of the carrier board below the core board, as shown in the following figure:

![output image](http://www.yahboom.net/public/upload/upload-html/1683343250/2023041100001.png))<br/><br/>

Connect the line and connect the HDMI display screen, mouse, and keyboard to JetsonOn the Nano, connect the power supply again, and finally plug in the microUSB data cable. Due to the previous step of connecting the jumper cap to FCREC and GND pins, so after powering on and starting up, it will automatically enter the REC flash mode.

![output image](http://www.yahboom.net/public/upload/upload-html/1683343250/2023041100002.png))<br/><br/> 


Under normal circumstances, after inserting the microUSB data cable, the following window will pop up. Please note that when using a virtual machine, the device needs to be set to connect to the virtual machine.


![output image](http://www.yahboom.net/public/upload/upload-html/1683343250/2023041100003.png))<br/><br/> 



二、 Start burning

    Please include Jetson in the information_ Boot_ Transferring the USB.tar.gz file to Ubuntu18.04 system, and open the terminal to run the decompression command.

tar xzvf Jetson_Boot_USB.tar.gz




