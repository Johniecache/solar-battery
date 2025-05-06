# Images
All images of the processes, finished project and testing of the solar battery bank
## Overview
Calculations - shows all my work to get the values I did for the boost converter (more details below).
Hand Diagram - just like the one from the main README.md just put here for orginization

## Calculations
My handwriting is sloppy so this is for clarification on the math below:

#### Inductor ripple current:
$$
V_{out} = \frac{V_{in}}{1 - D} \rightarrow D = 1 - \frac{V_{in}}{V_{out}} \rightarrow 1 - \frac{3.7v}{5v} \approx 0.26
$$

With the MT3608 operating at roughly 1.2 MHz

$$
&Delta;IL = \frac{V_{in} * D}{L * f} \rightarrow \frac{(3.7v)(0.26)}{(33 * 10^{-6}H)(1.2 * 10^{6}Hz)} = 24.3mA
$$

 * if 10&mu;H then Higher current ripples, more output noise, worse efficiency
 * if 100&mu;H then smaller rupples but with slower response & higher resistance

#### Capacitor (10&mu;F)
$$
C_{in} = \frac{I_{in} * D}{&Delta;V_{in} * f} \rightarrow \frac{(1A)(0.26)}{(0.1v)(1.2*10^{6}Hz)} \approx 2.17&mu;F
$$
 * 0.1v is chosen because it is one of the more efficient values for a stable, high preformance, and long lasting maximum input ripple
 * The reason for a 10&mu;F is because it allows for headroom for the transient and takes into account aging under voltage. The true value of this is more of roughly 6&mu;F

#### Capacitor (100&mu;F)
$$
C_{out} = \frac{I_{out} * D}{f * &Delta;V_{out}} \rightarrow \frac{(0.5A)(0.26)}{(1.2*10^{6}Hz)(0.1v)} = 1.08&mu;F
$$
 * 100&mu;F chosen because:
   * Compensates for Equivalen Series Resistance (ESR) and provide margin
   * Avoid brownout incase of sudden plug-ins
   * MT3608 expects roughly 10-22&mu;F so taking a 100&mu;F improves stability without risking oscillation
   * Cheap and very common
   * Keeps ripples below or at 100mA at 0.5 - 1 A loads

$$
&Delta;V = \frac{I_{out} * D}{C_{out} * f} \rightarrow \frac{(1A)(0.26)}{(100 * 10^{-6}F)(1.2 * 10^{6})} = 2.17v
$$
 * This equation assumes worse case which is why the rupple voltage seems so high
 * If rippling needs to be cut down more then add more 100&mu;F in parallel

#### Resistors
$$
V_{out} = V_{ref}(1 + \frac{R1}{R2})
$$
 * R1 is between the $V_{out}$ pin and the FB pin
 * R2 is between the FB and the GND pin (assume this to be 100,000&Omega;)

$$
R1 = R2 (\frac{V_{out}}{V_{ref}} - 1) \rightarrow 100,000(\frac{5v}{1.2v} - 1) = 316,666.667&Omega;
$$

 * With the assumption R1 is 100k&Omega; then the feedback resistor needs to be 316.67k&Omega;

Quick check:

$$
1.2v(1 + \frac{316,666.667&Omega;}{100,000&Omega;}) \approx 5.00v
$$

#### Optimizing for 316,666.667&Omega; Resistor combination
DISCLAIMER: I re-worked the optimization of the resistors after uploading my calculation image. Below is not only what I used but the corrected optimized format. This new reworked math is in the "optimization rework" image file

$$
100,000&Omega; + 100,000&Omega; + 100,000&Omega; = 300,000&Omega;
$$

$$
R_{parallel} = ({\frac{1}{10,000&Omega;} + \frac{1}{10,000&Omega;}})^{-1} = 5,000&Omega;
$$

$$
R_{parallel} = ({\frac{1}{2,000&Omega;} + \frac{1}{10,000&Omega;}})^{-1} \approx 1,666.67&Omega;
$$


 * (3x) 100,000&Omega;
 * (3x) 10,000&Omega;
 * (1x) 2,000&Omega;
 * Total: 7 Resistors

