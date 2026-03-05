# Thermal Physics: From Parasitic Compute to Hardware Aging

The core thesis of the SDAG framework is that **software inefficiency is a physical stressor**. In hyperscale AI infrastructure, parasitic compute (Routing Entropy) is not just a line item on an energy bill; it is a catalyst for accelerated hardware degradation.

## 1. The Conversion of Entropy to Heat

In high-density GPU clusters (H100/B200), any compute cycle that does not contribute to productive output is dissipated as heat. 

**Dynamic Power Consumption ($P$):**

$$P \approx C \cdot V^2 \cdot f$$

Where:
* $C$ is capacitance
* $V$ is voltage
* $f$ is frequency

Parasitic loops maintain high $f$ and $V$ without increasing token utility, keeping the TDP (Thermal Design Power) at its limit even during non-productive cycles.

## 2. Arrhenius Law and MTBF

The reliability of semiconductor devices is governed by the **Arrhenius Equation**, which states that the rate of physical reactions (like electromigration) increases exponentially with temperature.

**Acceleration Factor ($AF$):**

$$AF = \exp \left( \frac{E_a}{k} \cdot \left( \frac{1}{T_{base}} - \frac{1}{T_{stress}} \right) \right)$$

Where:
* $E_a$ is the activation energy (typically 0.7 eV for silicon).
* $k$ is the Boltzmann constant.
* $T$ is the absolute temperature in Kelvin.

**Practical Implication:** A persistent increase in operating temperature of just **10°C** due to parasitic workload density can reduce the Mean Time Between Failures (**MTBF**) of a GPU cluster by **~50%**.

## 3. The "Silent" Degradation

While modern cooling systems manage surface temperatures, the **thermal density** at the HBM (High Bandwidth Memory) and interconnect level remains a critical risk:

* **Thermal Cycling:** Parasitic spikes cause micro-fluctuations in temperature, leading to mechanical stress on TSVs (Through-Silicon Vias).
* **Memory Pressure:** Continuous KV-cache swapping increases the duty cycle of memory controllers, accelerating wear-out mechanisms.

## Conclusion

Auditing infrastructure for SDAG-baseline inefficiency is not an "optimization" task — it is a **Capital Expenditure (CapEx) protection strategy**. Ignoring the 7.5% baseline is equivalent to ignoring a 15% acceleration in hardware depreciation.
