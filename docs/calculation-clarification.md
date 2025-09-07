## Power Calculations
Clarification on calculations for the power consumption and production as well as other misc. calculations label as needed.

#### Battery Capacity & Load
$$
E_{bat} = V * Ah \rightarrow (3.7v)(5Ah) = 18.5Wh
$$

$$
E_{usable} = E_{bat} * &eta; \rightarrow (18.5Wh)(0.8) = 14.8Wh
$$

$$
E_{total} = E_{usable} * 4 = 59.2Wh
$$

#### Solar Output
$$
P_{solar} = 6w (given)
$$

$$
E_{daily} = P * t * &eta; \rightarrow (6w)(5h)(0.8) = 24 \frac{Wh}{day} 
$$

$$
P_{recharge} = \frac{E_{daily}}{E_{usable}} \rightarrow \frac{24 \frac{Wh}{day}}{59.2Wh} = 0.41 \frac{full}{day}
$$

#### TP4056 Charge
$$
I_{charge} = C * Charge Rate \rightarrow (1A)(0.33C) = 0.33A
$$

$$
t_{charge} = \frac{Ah}{A}(k) \rightarrow \frac{5Ah}{1A}(1.2) = 6 hours
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
Stipulations: 16 AWG 99.9% pure solid-core copper & 22 AWG copper wiring combinations at a total length of 

#### Resistor Combinations (USB-A)
* Due to Apple products declining to take power from a "dumb" charger it is necessary for resistor combinations to trick the iPhone into thinking its a "smart" USB-A charger via the data terminals
* Goal:
  * D- voltage = 1.50v
  * D+ voltage = 2.00v
 
$$
V_{D-} = 5.0v(\frac{4.3k &ohm;}{10k &ohm; + 4.3k &ohm;}) \approx 2.0v
$$

$$
V_{D+} = 5.0v(\frac{6.8k &ohm;}{10k &ohm; + 6.8k &ohm;}) \approx 1.5v
$$

$$
D-_{5v_rail} = 10k &ohm;
$$

$$
D-_{gnd_rail} = (\frac{1}{8200 &ohm;} + \frac{1}{8200 &ohm;})^{-1} + 100 &ohm; + 100 &ohm; \approx 4,300 &ohm;
$$

$$
D+_{5v_rail} = 10k &ohm;
$$

$$
D+_{gnd_rail} = (\frac{1}{7500 &ohm;} + \frac{1}{7500 &ohm;})^{-1} + 3000 &ohm; + 50 &ohm; \approx 6800 &ohm;
$$

* D- combination: 2x 8200 parallel + 2x 100 series
* D+ combination: 2x 7500 parallel + 1x 3000 series + 50 series


#### Thermal (TP4056)

$$
P_{diss} = (V_{in} - V_{batt}) * A \rightarrow (6v - 3.6v)(1A) = 2.4W
$$

 * Due to high wattage a heatsink, airflow or a combination maybe necessary on the TP4056, more testing will be done before a final verdict




