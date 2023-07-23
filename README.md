# Jetson-Nano-Sub
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

 
