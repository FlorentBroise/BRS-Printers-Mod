##CURA 4.13.0 Tips

### RomRider Fast Gyroid Infill  
A script tweak allowing to drastically reduce infill time for Gyroid

https://github.com/RomRider/klipper-FastGyroidInfill


### BRS Cura Profile
Here some free profiles, Speeds here are not a the max capacity of the machine, you can tune it a bit, made on purpose to reach high quality and below +-0.03mm of variance on XYZ for professionnal activity. Made for the BRS-E Vcore3 edition with the Flathead V2 profile

Material|Objective|Filament Brand|cura-profile
-----------------|------|-----------------------------------| :---------------:
ABS/ASA | Hight quality/High accuracy| EmotionTech/3DJake| [Download](/cura/BRS-E-ABS-ASA.curaprofile)
PLA | Hight quality/High accuracy| EmotionTech/3DJake/EcoFil/Polyterra| [Download](/cura/BRS-E-PLA.curaprofile)


### CURA Material cost and power cost

You need to make a material profile, fill the density, net weight of the spool, and the price you've paid for it

![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/6c226510-7368-476c-aca2-fb6c6bc70060)

Then for the power cost, you need a Plugin name "Power Cost"

![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/4807b9c5-5213-4659-a676-2cdd24a0ca36)

Under Machine settings, there is now a power cost tab, implement the price per KWh and the average power drow of the machine (once printing is started, after the bed and heater at temperature)

![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/e1a22e3d-a8a6-46c7-bbe7-b28465eaabb2)

Now once the Slicing is made, you can see the costs for the part

![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/6ec691c1-9375-425d-8594-8151930d5f20)


### Flow Fine tunning

As Flow is the most important factor regarding to quality, bonding, and dimentionnal accuracy; I strongly advise to enable all factors in the settings.
This will allow you to achive perfect print on all aspect

![image](https://github.com/FlorentBroise/BRS-Printers-Mod/assets/93141411/7be388da-4310-4675-acf3-e5e7b6375943)

Remember that external wall flow can impact the dimentionnal accuracy. 
I'm personnally making the flow tuning before the rotation_distance tunning. This way I'm actually able to achieve 0.05-0.08mm precisions
I advise to make the rotation_distances tuning once a week, just measure the part, compare it to what was expected, and use the [conversion tool](https://docs.google.com/spreadsheets/d/12R55MfSqfu5xPplTaRvmbkXf2mHBpJ3Zlwajab_pi60/edit?usp=sharing) to fine tune overtime. This will make better part over the time, and maintain the dimentionnal accuracy accurate relative to Belt shrinkage over time, temperature variation, "wear" of the machine


## [Back to Main Page](/README.md)



