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
16. Superglue (or alternative attachment method, this is just what I did) the top of the USB-C on the TP4056 to the marked center of the battery holder.
17. In the end the wired connections should be as followed:
  * Solar Panel Vcc -> TP4056 Vin+ (16 AWG Insulated Tinned Wire w/ alligator clips)
  * Solar Panel gnd -> TP4056 Vin- (16 AWG Insulated Tinned Wire w/ alligator clips)
  * TP4056 B+ -> Battery & Case + (16 AWG 99.9% pure copper wire)
  * TP4056 B- -> Battery & Case - (16 AWG 99.9% pure copper wire)
  * TP4056 Vout+ -> MT3608 Vin+ (16 AWG Insulated Tinned Wire)
  * TP4056 Vout- -> common gnd (16 AWG Insulated Tinned Wire)
  * MT3608 Vin- -> common gnd (16 AWG Insulated Tinned Wire)
  * MT3608 Vout- -> common gnd (16 AWG Insulated Tinned Wire)
  * MT3608 Vout+ -> USB-A pin 4 (Vcc) (16 AWG Insulated Tinned Wire)
  * USB-A pin 1 (gnd) () -> common gnd (16 AWG Insulated Tinned Wire)
  * USB-A pin 2 (D-) () -> *resistor combo* (16 AWG 99.9% pure copper wire or just solder connections)
  * USB-A pin 3 (D+) () -> *resistor combo* (16 AWG 99.9% pure copper wire or just solder connections)


