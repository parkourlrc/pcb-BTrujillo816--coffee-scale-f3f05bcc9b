# Load Cell + HX711 Design Decisions

## Calculations

### Load Cell

#### Voltage Output

$$V_{OUT}=V_{S}\times V_{E}$$

- $V_{OUT}$: Output from Load Cell
- $V_S$: Voltage Sensitivity
- $V_E$ = Excitation Voltage

### HX711

#### Full Scale Input Differential Voltage (FSR)

- Gain of 128: $\pm 20mV$ (Channel A)
- Gain of 64: $\pm 40mV$ (Channel A)
- Gain of 32: $\pm 80mV$ (Channel B)

#### ADC Step Size

The data output from the ADC is a 24-bit 2's complement value.

ADC Step Size $= \frac{FSR\times2}{2^{24}}$

#### Gain Selection/Saturation

Given a 5 kg Load Cell with $V_{S}=20 \space mV/V$ sensitivity and an excitation voltage of $V_E=3.3 \space V$

Max Output Voltage: 

$V_{OUT}=20\space mV/V\times3.3 \space V=66\space mV$

If an object weighs 2500 g, then the output voltage (input into HX711) would be

$V_{OUT}=\frac{2500}{5000}\times66=33\space mV$

If the input signal into the HX711 were to exceed these the Full Scale Input Differential Voltage, the output from the HX711 would be saturated.

$33 \space mV$ is well above $\pm 20mV$; which leaves Channel A's $\pm 40mV$ and Channel B's $\pm 80mV$. 

This project uses Channel A with a Gain of 64.





