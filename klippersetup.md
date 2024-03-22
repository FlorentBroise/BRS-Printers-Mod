Disclaimer: This page is still under construction, I'm implementing content I will found legit to make a Pure straightforward Klipper/Mainsail setup, this is exactly the way I'm making my machines. It is not a complete guide, it is here to guide you for the main setup. You must build the printer cfg according the pinout layout and your specific hardware. you must be sure that the cables are correctly set to be fonctionnal too, this guid is not a wiring guide.

# Installation

These instructions assume the software will run on a Raspberry Pi computer. It is recommended that a Raspberry Pi 2 (or later) be used as the host machine.Pi 4 and 5 are recommended to achieve good performance. CM4 modules with EMMC >=16Go is a good option for specific MCU boards too.
This page is dedicated to a full Klipper Mainsail installation from the start, as a pure instalation. A KIAUH installation is possible too
I'm making this page as I'm making my own machines this way

# Prepping an OS image

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

# Building and flashing the micro-controller

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

It's common for each printer to have its own unique serial port name. This unique name will be used when flashing the micro-controller. It's possible there may be multiple lines in the above output - if so, choose the line corresponding to the micro-controller.
Copy this ID for later

# First Connection

You can now Access the WEBUI of the machine via any Browser. The machine will report ERRORS, that is normal, we dont have any cfg installed.
We will make the updates to be as fresh as we can.
Check the Config Tab and make the according update if available
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/6f96d18f-2a33-4da7-878e-170e64b77270)

# UPDATE and disclaimer

AT THIS POINT I STRONGLY SUGGEST TO NEVER DO ANY UPDATE TO KEEP A WORKING MACHINE FONCTIONNAL
Update can wreck you system and take time to solve and remake. If a machine works fine, DON'T DO ANY UPDATES
Update are relevent if a major add on or support is added for new hardware or new fonctionnality, please consider the balance between benefits and risks of such an thing.

# Host MCU (RPi)

In many case scenarios, the RPi will be used as a secondary MCU (GPIO pins, etc). It is a good idea to flash it as a secondary MCU if you want to ad Fans, Servo, custom modules, relays...

Open a PUTTY instance to install the RC script:
```
cd ~/klipper/
sudo cp ./scripts/klipper-mcu.service /etc/systemd/system/
sudo systemctl enable klipper-mcu.service
```
Then we build the MCU code
```
cd ~/klipper/
make menuconfig
```
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/bf1df19a-ce18-4dda-bba3-9136d549a486)
![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/3d1c15be-4abc-4511-b759-0b3372faf336)


select "linux process", quit the menu
Then we flash it
```
sudo service klipper stop
make flash
sudo service klipper start
```
If klippy.log reports a "Permission denied" error when attempting to connect to /tmp/klipper_host_mcu then you need to add your user to the tty group. The following command will add the "pi" user to the tty group:
```
sudo usermod -a -G tty pi
```
Optionnally you can enable SPI and GPIOCHIP

Make sure the Linux SPI driver is enabled by running
```
sudo raspi-config 
```
and enabling SPI under the "Interfacing options" menu.

For GPIO tools:
```
sudo apt-get install gpiod
```
```
gpiodetect
```
```
gpioinfo
```
To call a PIN as a fonction, by exemple a CPAP PWM signal modulation, you need to adress the FAN pin as

![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/3003566b-1230-4d9c-a310-ee9c5ddb7e05)

Meaning you will use the pin on the GPIOpin 20 here. To check GPIO pin availability, run the upper commands (gpiodetect, gpioinfo)


# Printer.CFG

The Printer.cfg is the config file containing all the settings linked to the machine
You must build you own depending you MCU PIN layout, Machine architecture, and custom hardware, [Here a file used in the last VUCLAIN 600 v1.3](printer.cfg)
In this file must be mentionned the ID of the MCU(s) identified previously via the command

I personnaly don't like to make too much INCLUDES, calling different CFGs. RatOS by exemple use an insanely high count of that, making the adjustement and the cfg readings quite difficult and hard to remember in my opinion. As RatOS is meant for versatility it is understandable, but here we are making a quite straightforward config, sometime keeping it simple is the way. 
I prefer using a complete printer.cfg, and if I need to, includes some specific auxilliary CFGs, like a macros.cfg (only for MACROS), a Toolhead.cfg (for CanBus toolheads) and eventually some exotic hardware like Euclid probes settings

```
ls /dev/serial/by-id/*
```
Like this

![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/093fb5b5-01cc-4cde-a556-954205b8ac5b)

To add the RPi MCU previously prepare, you must include 

![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/792ca751-99b1-4a3f-b84a-fb3c83b26cfc)




