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

1. Please include Jetson in the information_ Boot_ Transferring the USB.tar.gz file to Ubuntu18.04 system, and open the terminal to run the decompression     command.

```bash
tar xzvf Jetson_Boot_USB.tar.gz
```


![output image](http://www.yahboom.net/public/upload/upload-html/1683343250/2023041100004.png))<br/><br/> 

2. After decompression, enter Jetson from_ Boot_ USB folder, and then

```bash
   cd Jetson_Boot_USB/
   ls
   ```
	

![output image](http://www.yahboom.net/public/upload/upload-html/1683343250/2023041100005.png))<br/><br/> 
	

   
3. Run the command to burn the EMMC boot file.
   
```bash
sudo ./flash.sh -r jetson-nano-devkit-emmc mmcblk0p1
   ```
![output image](http://www.yahboom.net/public/upload/upload-html/1683343250/2023041100006.png))<br/><br/> 

4. Finally, wait for the file to be burned and enter the EMMC. If successful, a prompt will appear

"The target t210ref has been flashed successfully. Reset the board to boot from internal eMMC."

![output image](http://www.yahboom.net/public/upload/upload-html/1683343250/2023041100007.png))<br/><br/> 

If an error message appears, please confirm if the Jetson Nano is connected properly and enter the flash mode. Follow the first step to reconnect.

After the burning is completed, please remove the jumper cap from the Jetson Nnao, insert the USB flash drive, and then power on and turn on the computer again.

Note: If using the virtual machine provided in the Yabo Intelligent Materials, it already includes Jetson_ Boot_ USB files do not need to be passed back into the system.Virtual machine username: yahroomPassword: yahboom

# Programming U disk system
Burn USB drive system
The system in the USB flash drive requires the use of Win32DiskImager to burn the system.

1.Preparing for installation
The process of burning a USB drive system is the same as that of burning a TF card system.

1. Prepare a Win10 system computer and a USB drive (32GB or larger recommended). Jetson Nano is not required to participate in the process of burning the USB drive.
2. Download the image (it is recommended to download a system with Yahboom configured environment)Due to the need to modify the configuration information of the system in the USB drive, please download the USB drive system image provided by yahboot.Please do not download the official NVIDIA image as it may not boot due to configuration issues.

The default username for the system configured by yahroom is Jetson, and the password is yahroom

3.     Format SD card

Using SDFormatter to format a USB drive, be careful not to select the wrong drive, otherwise it may cause unnecessary trouble. If the USB drive has already been burned to the system, there may be an error during the first formatting. Just execute it again

![output image](http://www.yahboom.net/public/upload/upload-html/1683343267/2023041100001.png))<br/><br/> 

2.Burn USB drive system
1. Unzip the downloaded system compressed file to obtain the IMG image file
2. Insert the USB drive into the computer's USB port
3. Decompress and run the Win32DiskImager tool
4. Select the img (image) file in the software, select the drive letter of the USB drive under "Device", then select "Write" and start burning the system. Depending on the speed of your USB drive, the burning process may vary.

![output image](http://www.yahboom.net/public/upload/upload-html/1683343267/2023041100002.png))<br/><br/> 

5. After the burning is completed, a completion dialog box will pop up, indicating that the installation is complete. If it is not successful, please close software such as firewall and reinsert the USB drive for burning. Please note that after installation, the USB drive is divided into multiple partitions and cannot be clicked to enter under Windows system. This is a normal phenomenon because the disk partition under Windows cannot be seen!

At this point, Jetson Nano was successfully burned and written. After successful burning, the system may prompt to format the partition because it cannot be recognized. Do not format at this time! Do not format! Do not format! Click Cancel, then pop up the USB drive, and finally insert it into the USB port on the Jetson Nano motherboard.

3.If the burning USB drive system fails to start, the solution is

1.Insert the USB drive into the virtual machine, open the USB drive on the virtual machine, open the terminal on the USB drive interface, and enter the following command

```bash
cd boot/extlinux 
   ```
```bash
sudo gedit extlinux.conf
   ```

grasp“root=/dev/mmcblk0p1”Modify to“root=/dev/sda1”

![output image](http://www.yahboom.net/public/upload/upload-html/1683343267/2023041100003.png))<br/><br/> 


mmcblk0p1：SD card startup

sda1:USB drive startup

Save and exit, insert the USB drive into the Jetson nano, and then turn it on

If the above methods have not been resolved yet:

Reference link:https://blog.csdn.net/propor/article/details/127966228



