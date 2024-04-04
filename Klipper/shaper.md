# INPUT SHAPER

Make sure your ADXL based module is configured correctly
The way this one is attached to the toolhead will matter a lot, a loosy fixation a placment will result a bad shaping
The best place is in the nozzle (the BTT ADXL V2 is the best option IMO). You will use it only on this occasion and then removed it after use

Keep in mind that getting a not perfect shaper is not the end of the world, it is here to counterbalance thos issues.
Only the print result count at the end of the day

First check the acceleromete fonction nwith ```ACCELEROMETER_QUERY``` in the printer CLI
you should get something like this
```
Recv: // adxl345 values (x, y, z): 470.719200, 941.438400, 9728.196800
```
Then run 
```
TEST_RESONANCES AXIS=X
```
```
TEST_RESONANCES AXIS=Y
```

and finally those lines in the  Putty instance
```
~/klipper/scripts/calibrate_shaper.py /tmp/resonances_x_*.csv -o /tmp/shaper_calibrate_x.png
```
```
~/klipper/scripts/calibrate_shaper.py /tmp/resonances_y_*.csv -o /tmp/shaper_calibrate_y.png
```

you can now grab the PNGs of the shaper and make you analysis


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
