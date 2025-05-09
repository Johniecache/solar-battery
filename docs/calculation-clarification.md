
## Booster Calculations
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
 * R2 is between the FB and the GND pin (assume this to be 100k&Omega;)

$$
R1 = R2 (\frac{V_{out}}{V_{ref}} - 1) \rightarrow 100k(\frac{5v}{1.2v} - 1) = 316.67k&Omega;
$$

 * With the assumption R1 is 100k&Omega; then the feedback resistor needs to be 316.67k&Omega;

Quick check:

$$
1.2v(1 + \frac{316.67k&Omega;}{100k&Omega;}) \approx 5.00v
$$

#### Optimizing for 316.67k&Omega; Resistor combination
DISCLAIMER: I re-worked the optimization of the resistors after uploading my calculation image. Below is not only what I used but the corrected optimized format. This new reworked math is in the "optimization rework" image file

$$
100k&Omega; + 100k&Omega; + 100k&Omega; = 300k&Omega;
$$

$$
10k&Omega; + 5k&Omega; = 15k&Omega;
$$

$$
R_{parallel} = ({\frac{1}{2k&Omega;} + \frac{1}{10k&Omega;}})^{-1} \approx 1.67k&Omega;
$$

$$
R_{eq} = 300k&Omega; + 10k&Omega; + 5k&Omega; + 1.67k&Omega; = 316.67k&Omega;
$$


 * (3x) 100k&Omega;
 * (2x) 10k&Omega;
 * (1x) 5k&Omega;
 * (1x) 2k&Omega;
 * Total: 7 Resistors, 4 unique resistors




## Power Calculations
Clarification on calculations for the power consumption and production as well as other misc. calculations label as needed.

#### Battery Capacity & Load
$$
E_{bat} = V * Ah \rightarrow (3.7v)(3Ah) = 11.1Wh
$$

$$
E_{usable} = E * &eta; \rightarrow (11.1Wh)(0.8) = 8.88Wh
$$

#### Solar Output
$$
P_{solar} = 6w (given)
$$

$$
E_{daily} = P * t * &eta; \rightarrow (6w)(5h)(0.8) = 24 \frac{Wh}{day} 
$$

$$
P_{recharge} = \frac{E_{daily}}{E_{usable}} \rightarrow \frac{24 \frac{Wh}{day}}{8.88Wh} = 2.703 \frac{full}{day}
$$

#### TP4056 Charge
$$
I_{charge} = C * Charge Rate \rightarrow (1A)(0.33C) = 0.33A
$$

$$
t_{charge} = \frac{Ah}{A}(k) \rightarrow \frac{3Ah}{1A}(1.2) = 3.6 hours
$$
 * where k is a constant variable at 1.2v for overhead

#### Boost Converter Load Limit
$$
P_{out} = V * A \rightarrow (5v)(0.5A) = 2.5W
$$

$$
P_{in} = \frac{P_{out}}{&eta;} \rightarrow \frac{2.5W}{0.8} = 3.125W
$$

$$
I_{in} = \frac{P_{in}}{V_{in}} \rightarrow \frac{3.125W}{3.7v} \approx 0.845A
$$
 * safe range for MT3608 amps

#### Voltage drop
Stipulatios: 22 AWG wire at 1A over 2ft round-trip

$$
V_{drop} = R_{wire} * L * I \rightarrow 0.0165 \frac{&ohm;}{ft} (2ft)(1A) = 0.033V
$$

* Within acceptable range

#### Thermal (TP4056)

$$
P_{diss} = (V_{in} - V_{batt}) * A \rightarrow (6v - 3.6v)(1A) = 2.4W
$$

 * Due to high wattage a heatsink, airflow or a combination maybe necessary on the TP4056, more testing will be done before a final verdict




