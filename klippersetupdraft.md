#Installation

These instructions assume the software will run on a Raspberry Pi computer. It is recommended that a Raspberry Pi 2 (or later) be used as the host machine.Pi 4 and 5 are recommended to achieve good performance. CM4 modules with EMMC >=16Go is a good option for specific MCU boards too.
This page is dedicated to a full Klipper Mainsail installation from the start, as a pure instalation. A KIAUH installation is possible too
I'm making this page as I'm making my own machines this way

#Prepping an OS image
Start by downloading Rasberry Pi image ([here](https://www.raspberrypi.com/software/)), Then follow the steps
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/7a6e2d4e-57f4-476c-90f1-0b1a9b7910b9)
By clicking we go to Mainsail OS, a package with Klipper and Mainsail already pre-installed. We can follow this route:
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/06661aa5-ad4e-4931-b113-b39af9f4b9c5)
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/3ac89d11-8cbd-4a7f-8c25-237cd42af760)
"Enable SSH" and then click "Save", there are other functions that can be set in this interface, please modify them according to your needs.

Since we have selected the most recent version of Mainsail OS, we can select the SD card and configure the wifi. For this we have these options:
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/9a6ae523-e65e-486c-bc6d-84884c027837)
It is important to choose a quality and fast micro SD card, since a slow card can hinder the performance of the device.
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/d07d61ae-db19-46b0-aeca-d7a5432f7cf9)
Wait for the process to complete.

#Building and flashing the micro-controller
Use PUTTY to connect you controller, I use Advanced IP scanner to check the IP adress
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/55b3a969-b058-4593-ba08-64090f3b8c07)

To compile the micro-controller code, start by running these commands on the Raspberry Pi:

```
cd ~/klipper/
make menuconfig
```
Follow you motherboard manual to get the correct settings to apply
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/271b0ba4-99d9-47ca-8e9d-170b106a556b)
exemple
Once done you can quit
The comments at the top of the printer configuration file should describe the settings that need to be set during "make menuconfig". Open the file in a web browser or text editor and look for these instructions near the top of the file. Once the appropriate "menuconfig" settings have been configured, press "Q" to exit, and then "Y" to save. Then run:
```
make
```
After the make command is executed, the klipper.bin firmware we need will be generated in the device's home/pi/klipper/out folder. You can download it directly to your computer with WINSCP
According to you board model (her BTT), Rename `klipper.bin` to "firmware.bin", copy it to the root directory of the SD card, insert the SD card into the MCU SD card slot, press the reset button or power on again, and the firmware will be automatically updated.
After the update is complete, the "firmware.bin" in the SD card will be renamed to "FIRMWARE.CUR".

In PUTTY, enter
```
ls /dev/serial/by-id/*
```
It should report something similar to the following:
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/15cd600e-9f1f-4950-809c-25a88bab5499)

It's common for each printer to have its own unique serial port name. This unique name will be used when flashing the micro-controller. It's possible there may be multiple lines in the above output - if so, choose the line corresponding to the micro-controller (see the FAQ for more information).

For common micro-controllers, the code can be flashed with something similar to:

sudo service klipper stop
make flash FLASH_DEVICE=/dev/serial/by-id/usb-1a86_USB2.0-Serial-if00-port0
sudo service klipper start
Be sure to update the FLASH_DEVICE with the printer's unique serial port name.

When flashing for the first time, make sure that OctoPrint is not connected directly to the printer (from the OctoPrint web page, under the "Connection" section, click "Disconnect").
