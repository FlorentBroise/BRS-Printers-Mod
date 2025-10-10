![alt text](/image/calibration.png)
# CALIBRATION OF YOUR MACHINE

## 1. EXTRUDER Rotation_Distance
Objective|Setting|Comments|Link
-------|-------|-----------------|-------
Getting the good extrusion|Rotation_Distance|mark the filament at 120mm from your extruder, Extrude 100mm, make the calculation to retrieve the good number, TeachingTech webstite include the step/mm calculation, then use my table to get the conversion into Rotation_distance units|[Calculation](https://teachingtechyt.github.io/calibration.html#esteps) [Conversion Table](https://docs.google.com/spreadsheets/d/1FKyyWfHV8zdZKKFCmgh5MvTFCjXNV37kUfqWGvWRDxo/edit#gid=0)

  
## 2. Flow
Objective|Setting|Comments|Link
-------|-------|-----------------|-------
Getting the good width|Flow (Slicer)|Print a 30x30mm cube in vase mode, check the width of the layer |[Calculation](https://teachingtechyt.github.io/calibration.html#flow) [Conversion Table](https://docs.google.com/spreadsheets/d/1FKyyWfHV8zdZKKFCmgh5MvTFCjXNV37kUfqWGvWRDxo/edit#gid=0)
## 3. Adjusting belts tensions.
Section|Setting|Recommended Value|details|Calculation sheet
-------|-------|-----------------|------- |-------
Getting Equalize on the CoreXY principle|Rotation_Distance|Follow the [Instruction](/manuals/belt.pdf)|[Spectroid](https://play.google.com/store/apps/details?id=org.intoorbit.spectrum&hl=fr&gl=US) | [Download](/manuals/Belt_Tension_Calculations.ods)

## 4. Octogone Calibration for XY
Objective|Setting|Comments|Link
-------|-------|-----------------|-------
Getting Equalize on the CoreXY principle|Belt-tension+Print+Rotation_Distance|Print the [Octogon](/cad/octogon.stl) and follow the [Instruction](/manuals/calibration.pdf)|[Conversion Table](https://docs.google.com/spreadsheets/d/1PNDpxMo82B2Yi7_REPhKj44IOn1BJzk-KYgN7mVPe6Q/edit?usp=sharing)

## 5. Z Calibrations
Objective|Setting|Comments|Link
-------|-------|-----------------|-------
Getting the good Z Height|Rotation_Distance|Print a normal 30x30 cube, I personnaly use a raft to absorb the first layer thickness imprecision, mesure it and use the conversion table to find the good value| [Conversion Table](https://docs.google.com/spreadsheets/d/1FKyyWfHV8zdZKKFCmgh5MvTFCjXNV37kUfqWGvWRDxo/edit#gid=0)

## 5. Bed Mesh tips to master first layer
Objective|Advices
-------|-------
Master a perfect first layer|Use a Beacon or Cartographer probe type with 150; 150 scan points
------------------------
#|Steps|Link
-------|-------|-------
1|Implement you Probe settings with the correct offsets from the nozzle|
2|Add the Axis twist configuration to you machine|[Klipper Axis twist](https://www.klipper3d.org/Axis_Twist_Compensation.html)
3|Heat soak the bed to 80°C, Heat the nozzle to 200°C, HOME, Z-TILT, Axis twist procedure form the above link for X and Y, SAVE_CONFIG|
4|Heat soak the bed to 80°C, Heat the nozzle to 200°C, HOME, Z-TILT, Make you BED MESH calibration, SAVE_CONFIG|
5|Start a print, baby step the Z to match the perfect layer thickness. SAVE|

This would be the best procedure to get it work with precision

____________________________________________________________________________________  

Special Thanks to the helpfull content of Mickael from TeachingTech
