Here the BRSVS Air module.

![alt text](/image/BRSVS1.png)

WHAT-WHY-HOW:

0/ BRSVS?
This is a dual auxiliary fan cooling part system, deported from the head to the sides, to loose weight, and bring tons of CFM.

1/ The objective
Bring a high volume of laminar flux of air to the nozzle space to be able to reach high speed motions for PLA, in other things, and remove the fan cooling system from the head.
(It can be used with both)

 -The mod is made by 2 parts:
 1-the base part (fixed), housing fans and the first channel stage duct.
 2-the hose part, which can be modded to achieve different compression, angles, and output designs.
 
2/ Mounting points
 The base part can be mounted in 2 ways:
 -1 On the side pannel (tpu join seal for dampening vibration advertised)
 -2 on a 30x30 vertical extrusion 
 
3/ Hose part
The hose parts in the pack is adapted to a standard Vcore laterial clearance for movement and Z-Tilt
But it can be modified to fit larger models, or a different channeling design

3/ Fans:
Fans needed are quite easy to source, it hase be based on the San-Ace Denky 40m counter ratating module. Those are Server fan for 1u server most of the time.
I chose them because the use to fit the lateral space on the Vcore, and are able to a very high output at a very high static pressure.
At 100% they are very noisy but in my tests, a 30% value still send a enormous amount of air volume at a very acceptable noise. Closing the printer can helps too.

WARNING: Each fan is made by two fans, counter rotating, you will need to rewire them in order to simplify them

4/Power
Those 8 fans (16) draw 12w at 100% each. That mean you have to power it correctly. 
CHECK YOUR PSU CAPACITY TO HANDLE IT

They are 12V, which mean you need to get a 12V auxiliary PSU(100W mini) or a more classical 24v 360W PSU paired with a 24-12v 10-20A step down module (https://www.amazon.fr/gp/product/B07ZV76NLC/ref=ppx_yo_dt_b_asin_title_o05_s00?ie=UTF8&psc=1).
The control of those fan is made by a MOSFET (https://www.amazon.fr/gp/product/B074L1CMYB/ref=ppx_yo_dt_b_asin_title_o04_s00?ie=UTF8&psc=1), directly linked to a GPIO of you Pi

[Wirings(simplified)](https://github.com/FlorentBroise/RatRig-Upgrades/raw/main/image/BRSVSwirings.png)

[STEP SOON](https://github.com/FlorentBroise/RatRig-Upgrades/raw/main/cad/BRSVS1_2b.zip)

DISCLAIMER: The mod in under pre-release state, some tiny changes could occur.  
