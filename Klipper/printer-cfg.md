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

# BELT TENSION RESONNANCE
```
TEST_RESONANCES AXIS=1,1 OUTPUT=raw_data
```
```
TEST_RESONANCES AXIS=1,-1 OUTPUT=raw_data
```

Then run this line in PUTTY the instance:
```
~/klipper/scripts/graph_accelerometer.py -c /tmp/raw_data_axis*.csv -o /tmp/resonances.png
```
