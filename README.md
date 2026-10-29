# Open-Loop Buck Converter in LTspice

An LTspice simulation of a DC-DC step-down converter. The circuit uses a MOSFET switch, Schottky freewheel diode, inductor, output capacitor, and resistive load. It is an open-loop design driven by a fixed-duty-cycle pulse source, not a closed-loop regulated supply.

## Circuit settings

| Parameter | Value |
| --- | ---: |
| Input voltage | 12 V DC |
| PWM drive | 0 to 10 V, 100 kHz, 50% duty cycle |
| Inductor | 100 µH |
| Output capacitor | 100 µF |
| Load | 6 Ω |
| Transient analysis | 10 ms, maximum step 100 ns |

The ideal continuous-conduction estimate is `Vout ≈ D × Vin = 0.5 × 12 V = 6 V`. In the supplied transient plot, the output overshoots to roughly 10 V at startup, oscillates as the LC filter settles, and reaches roughly 5.8 V. This is a simulated result under the specific component models and load shown, not a measured hardware result. The startup overshoot is a reason to add feedback, soft-start, and load-step testing in a later revision.

## Files

- `Buck_converter.asc`: editable LTspice schematic.
- `images/startup-waveform.png`: supplied circuit and output-voltage waveform screenshot.

## Run

Open `Buck_converter.asc` in LTspice and click **Run**. Plot `V(out)` to reproduce the transient response. The schematic includes `.tran 0 10m 0 100n`.

## Next steps

- Add voltage feedback and assess output regulation as the input and load change.
- Measure peak-to-peak ripple, switch/diode stresses, and input/output power in a steady-state window.
- Compare startup behavior with a soft-start implementation.
