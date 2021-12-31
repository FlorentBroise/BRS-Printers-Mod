![alt text](/image/print.png)
# How to print the BRS parts?

## 1. Which material?
Pretty much any common 3D printing material can be used.

I design it to print with PACF material such as Fibelogy PA12CF15 or Esun ePAHT

PA12 from Fiberlogy is very easy when the profile is fine tuned
ePAHT is a pain to get ok, spool must be dryed 12h @80°C, and parts annealed at 80-110°C for 3-6h, failure rate is higher that PA12CF and the pros to use ePAHT are non-existant in the context of the Vcore parts

I am currently running PA12CF15 for my own machine

## 2. Placing your parts in the slicer.
All STL files are already properly oriented for optimal print results and optimal layer orientation.  

## 3. Slicer Settings
In this section I will assume that you have some experience with 3D printing and that your printer is calibrated.
PACF dont bridge well, Supports and supports intefaces are needed, Make samples before going big, suppports could be unremovable otherwise

____________________________________________________________________________________  



### QUALITY


Section|Setting|Recommended Value|Comment
-------|-------|-----------------|-------
Quality|Layer Height|Between 0.16 and 0.22| No structural or precision gain by going lower than 0.16. 
Quality|Line Width|0.40 (for 0.4mm nozzle)| - 

______________________________________________________________________________  


### SHELL


Section|Setting|Recommended Value|Comment
-------|-------|-----------------|-------
Shell|Wall Line Count|3 to 4|-
Shell|Top/Bottom thickness|1.2mm|This means between 9 and 5 top and bottom layers, depending on your layer height. I use a 0.26mm first and last Layer width to get better finish 


### INFILL


Section|Setting|Recommended Value|Comment 
-------|-------|-----------------|-------
Infill|Infill Density|18-25%|Going higher will not add significant strength.
Infill|Infill Pattern|Gyroid|The advantages of gyroid: high shear strength, and low weight (so less filament needed) and less cross pattern, which reduce risks of shifting.

### SPEED

This parameter is free for you to decide

-For classic Ender type printer, 60-70mm/s is a nice spot. 
-For higher end machines (Vcore) I can crank to 200mm/s without any loss of quality and strenght



[Back to Main Page](/README.md)
