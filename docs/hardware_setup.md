# Hardware Setup Instructions
### Hardware needed:
* Soldering Iron
* Insulated Tinned Wire (22 AWG) - for lighter current connections
* Insulated Tinned Wire (16 AWG) - for higher current connections
* Pure (99.9%) Copper Wire (16 AWG) (Optional) - for higher efficiency power connections 
* 21700 50E battery & holder (4S recommended)
* TP4056 Li-ion charging module - for protection
* MT3608 boost converter module 
* Solar Panel (5-6v at minimum 1A)
* Rocker Switch - for power control 
* USB-A female port (with exposed pins or breakout board)
* alligator clips
* Kit of Resistors (Optional for voltage dividers for "smart" charger)

### Step-by-Step Instructions:

1. Download and print all .stl files located in the hardware folder
2. Setup your workstation. Ensure all parts needed are at your disposal.
3. Tin (solder) the battery pins on the back of the battery holder and ensure fusion.
4. Cut 2x ~3.5" of 99.9% pure 16 AWG copper wire and straighten it (I used two pliers on each end and pulled taught).
5. Line the straight copper wire to the outside of the pins and trim off any excess length.
6. Reline the cooper wire to the outside and tack solder one of the end pins to the wire.
7. Tack solder the other end.
8. Solder one of the middle pins to the copper wire well and ensure its flush connection.
9. Repeat 4-7 for the other side pins.
10. Using a ruler or some sort if measuring device find the center of the edge of the battery holder between the pin sets and mark it.
11. Cut 2x () 99.9% pure copper wire and straighten it like before.
12. Bend one of the ends on each straightened wire to a 90 degree curve roughly 4-5mm from the end.
13. Stick the shorter side into the Vin+ Vin- holes near the USB-C female port from the bottom.
14. Ensure the longer side of the copper wires are parallel with the TP4056 board and solder the shorter part sticking through the holes (reference pictures in images folder).
15. Using a measuring device (I used a ruler) find the center of the battery holder between the pins on the edge of the case.
16. Optional: put red heatshrink on the Vin+ and black heatshrink on the Vin- copper wires and torch them on for better indication on what each one is.
17. Superglue (or alternative attachment method, this is just what I did) the top of the USB-C on the TP4056 to the marked center of the battery holder.
18. Take the 3D printed raisers and stick them through the large holes in the MT3608 and glue them in.
19. Orientate the MT3608 so that the Vin+ and Vin- are facing the TP4056 Vout+ and Vout-
20. Glue the raisers to the back of the battery holder.
21. Solder the MT3608 Vin+ to TP4056 Vout+ using 16 AWG Insulated Tinned Wire.
22. Solder the MT3608 Vin- to TP4056 Vout- using 16 AWG Insulated Tinned Wire.
23. Setup and solder resistor combinations for "smart" charger:
  * D- = 2.0v
  * D+ = 1.5v
  * D- $\rightarrow$ 5v rail -> 10k&ohm; resistor
  * D- $\rightarrow$ gnd rail -> 2x 8200&ohm; resistors in parallel will be in series with 2x 100&ohm; resistors that are in series
    * +-- [8200&ohm; || 8200&ohm;] -- [100&ohm;] -- [100&ohm;] --+
  * D+ $\rightarrow$ 5v rail -> 10k&ohm; resistor
  * D- $\rightarrow$ gnd rail -> 2x 7500&ohm; resistors in parallel will be in series with 1x 3000&ohm; resistor in series with 1x 50&ohm; resistor
    * +-- [7500&ohm; || 7500&ohm;] -- [3000&ohm;] -- [50&ohm;] --+
24. Solder MT3608 Vout+ to pin 4 (Vcc) on the USB-A exposed pin (Optional: solder to USB-A vcc rail).
25. Solder MT3608 Vout- to pin 1 (gnd) on the USB-A exposed pin (Optional: solder to USB-A gnd rail).
26. Place the 3D lid over the circuit and adjust the copper wire from the TP4056.
27. With the lid on top and copper wire adjusted mark the openings for the Rocker switch and the USB-A outsides.
28. Remove the lid and super glue the Rocker Switch and USB-A between the marks you just made on the battery holder.
29. Measure out and mark locatiosn of the 3D printed lid raisers (MEASUREMENTS).
30. Measure out appropriate length of choice for desired distance between solar panel and battery pack (recommended: 1ft 16 AWG Insulated Tinned Copper wire).
31. Strip and solder one end of wire to the solar panel.
32. Ensure that the roxker switch is turned off.
33. Strip and solder the other end of the wire to the TP4056 (optional: solder to alligator clips).
34. If you soldered to alligator clips instead,then clip them to the TP4056.
35. Place one if the Samsung 21700 50E batteries into one of the holder slots.
36. Place the solar panel into direct sunlight or in high lumen environment.
37. Check to make sure a red LED on the TP4056 lights up (this indicates its recieving power from solar panel).
38. Flip the rocker switch on.
39. Using a multimeter check the MT3608 Vin+ and Vin- (should be ~3.7 if battery is between 20-80% but could be 2.5v if low or 4v if full).
40. Using a multimeter check the MT3608 Vout+ and Vout- (should be ~15-20v).
41. Using a flathead or coin turn the dial on the blue box until ~5v is reached (maximum 1 full turn and use multimeter again to check progress).
42. Using a multimeter check the voltage across the Vcc and gnd rails on the USB-A pins (should be same as between Mt3608 Vout+ and Vout-).
43. Plug in a USB-A male into the USB-A female port.
44. plug other end into phone or other decice to check for charge and power (I used my phonr which showed it was charging).
45. Unplug device and turn rocker switch off.
46. Place lid on top and screw it in (dont overscrew as the 3D printed screws are more fragile then metal screws).

### Wiring Overview
Wired connections should be as followed:
  * Solar Panel Vcc $\rightarrow$ TP4056 Vin+ (16 AWG Insulated Tinned Wire, Optional: w/ alligator clips)
  * Solar Panel gnd $\rightarrow$ TP4056 Vin- (16 AWG Insulated Tinned Wire, Optional: w/ alligator clips)
  * TP4056 B+ $\rightarrow$ Battery & Case + (16 AWG 99.9% pure copper wire)
  * TP4056 B- $\rightarrow$ Battery & Case - (16 AWG 99.9% pure copper wire)
  * TP4056 Vout+ $\rightarrow$ Rocker Switch (16 AWG Insulated Tinned Wire)
  * Rocker Switch $\rightarrow$ MT3608 Vin+ (16 AWG Insulated Tinned Wire)
  * TP4056 Vout- $\rightarrow$ common gnd (16 AWG Insulated Tinned Wire)
  * MT3608 Vin- $\rightarrow$ common gnd (16 AWG Insulated Tinned Wire)
  * MT3608 Vout- $\rightarrow$ common gnd (16 AWG Insulated Tinned Wire)
  * MT3608 Vout+ $\rightarrow$ USB-A pin 4 (Vcc) (16 AWG Insulated Tinned Wire)
  * USB-A pin 1 (gnd) () $\rightarrow$ common gnd (16 AWG Insulated Tinned Wire)
  * USB-A pin 2 (D-) () $\rightarrow$ *resistor combo* (16 AWG 99.9% pure copper wire or just solder connections)
  * USB-A pin 3 (D+) () $\rightarrow$ *resistor combo* (16 AWG 99.9% pure copper wire or just solder connections)


