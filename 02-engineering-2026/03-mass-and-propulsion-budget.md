# Preliminary Mass and Propulsion Analysis

*CERBERUS Engineering Redesign — 2026*

## From thrust requirements to a component-level design

The initial sizing calculations established the thrust requirements for an eight-rotor CERBERUS aircraft using an assumed takeoff mass of 3.2 kg.

The next question was whether this mass estimate was realistic once the propulsion system, battery, flight controller, frame and sensing equipment were considered.

To investigate this, I began assembling a preliminary component list using published manufacturer specifications. The purpose was to establish a more realistic mass estimate and determine how it would affect motor selection, electrical power consumption and flight endurance.

The original eight-rotor configuration remains the reference geometry for this analysis.

## Reference propulsion components

The first propulsion configuration uses a T-MOTOR MN3110 KV700 brushless motor with a 12 × 4-inch carbon-fibre propeller and a 4S LiPo battery.

This combination was selected for initial investigation because T-MOTOR publishes static thrust, current and power measurements for the motor–propeller combination.

| Component | Reference model | Relevant specification |
|---|---|---|
| Motor | T-MOTOR MN3110 KV700 | 99 g including cables; 3–6S |
| Propeller | T-MOTOR P12×4 CF | 304.8 mm diameter |
| ESC | Hobbywing XRotor Micro 20A BLHeli | 20 A continuous; 2–4S; 6.8 g |
| Battery | Tattu G-TECH 4S 10000 mAh | 14.8 V nominal; 921 ± 15 g |
| Flight controller | Holybro Pixhawk 6C Mini, current Model A | 42.4 g |

These are reference components for the analytical design. Final selection will require confirmation of mechanical fit, electrical compatibility and system-level operating limits.

Manufacturer sources are listed at the end of this document.

## Preliminary aircraft mass budget

The first mass budget combines published component specifications with estimates for the parts that have not yet been modelled.

| Component | Estimated mass | Data basis |
|---|---:|---|
| Eight MN3110 motors | 792 g | Manufacturer |
| Eight P12×4 propellers | 116 g | Provisional interpretation of catalogue |
| Eight XRotor Micro ESCs | 54 g | Manufacturer, rounded |
| 4S 10000 mAh battery | 921 g | Manufacturer |
| Pixhawk 6C Mini | 42 g | Manufacturer, rounded |
| Frame and motor arms | 750 g | Design estimate |
| Landing gear | 180 g | Design estimate |
| Power distribution and wiring | 150 g | Design estimate |
| GPS and telemetry | 90 g | Design estimate |
| Camera and sensing equipment | 240 g | Placeholder payload allowance |
| Design allowance | 200 g | Preliminary mass reserve |
| **Total estimated takeoff mass** | **3,535 g** | Mixed-source estimate |

The resulting mass is approximately 10.47% higher than the initial 3.2 kg assumption.

The frame, landing gear, electrical integration and sensing payload remain important sources of uncertainty. Their mass estimates will be revised after the CAD model and sensor architecture are developed.

### Uncertainty in propeller mass

T-MOTOR describes the P12×4 propeller as a two-blade integrated design, while the published weight specification uses the expression "Weight (Single Blade): 14.5 g."

For this initial budget, 14.5 g was assigned to each complete propeller. The manufacturer or a physical measurement should confirm that interpretation.

If 14.5 g represents one blade and the complete two-blade propeller weighs approximately 29 g, the total propeller allowance would increase from 116 g to 232 g.

Under that alternative interpretation, the total aircraft mass would increase to approximately **3,651 g**, before considering any additional mounting hardware.

This uncertainty will be resolved before finalising the CAD-based mass budget.

## Motor performance at the revised takeoff mass

For the current estimated mass:

$$
m = 3.535\ \mathrm{kg}
$$

Using gravitational acceleration of 9.81 m/s²:

$$
W = mg = 34.678\ \mathrm{N}
$$

With eight equally loaded rotors:

$$
T_{\mathrm{hover}} = \frac{W}{8}
$$

The required hover thrust is approximately:

**442 gf per motor**

Using the preliminary static thrust-to-weight target of 2:1, the corresponding maximum thrust requirement is approximately **884 gf per motor**.

### Manufacturer test data

T-MOTOR publishes the following measurements for the MN3110 KV700 with a 12×4 CF propeller at a nominal test voltage of 14.8 V.

| Measured thrust | Current | Electrical power |
|---|---:|---:|
| 420 gf | 3.2 A | 47.36 W |
| 790 gf | 6.2 A | 91.76 W |
| 930 gf | 8.5 A | 125.80 W |
| 1,190 gf | 11.6 A | 171.68 W |
| 1,290 gf | 14.0 A | 207.20 W |

The expected hover operating point lies close to the first measured value.

Using linear interpolation between 420 gf and 790 gf:

$$
P(T) = P_1 +
\frac{T-T_1}{T_2-T_1}(P_2-P_1)
$$

At approximately 442 gf:

$$
P_{\mathrm{motor}} \approx 50.0\ \mathrm{W}
$$

For eight motors:

$$
P_{\mathrm{propulsion}} \approx 400\ \mathrm{W}
$$

This estimate uses interpolation between manufacturer measurements. The actual power curve may be nonlinear, and electrical losses associated with the complete installation require further assessment.

The manufacturer's highest listed static thrust for this combination is 1,290 gf per motor. Eight such units would provide a combined bench-test thrust of approximately 10,320 gf.

Relative to the provisional 3,535 g aircraft mass, this corresponds to a maximum static thrust-to-weight ratio of approximately **2.92:1**.

The result provides a first indication of available thrust headroom. Flight-control authority, sustained operating limits, thermal behaviour and propulsion-failure performance will require additional evaluation.

## Battery energy and estimated endurance

The reference battery is a Tattu 4S 10000 mAh LiPo with a nominal voltage of 14.8 V.

Its nominal energy is:

$$
E_{\mathrm{nominal}} = V C
$$

$$
E_{\mathrm{nominal}} = 14.8 \times 10 = 148\ \mathrm{Wh}
$$

For the initial calculation, I assumed that 80% of the nominal energy would be available for the mission.

$$
E_{\mathrm{usable}} = 148 \times 0.80 = 118.4\ \mathrm{Wh}
$$

Using the interpolated propulsion estimate of approximately 400 W and a provisional 20 W allowance for auxiliary electronics:

$$
P_{\mathrm{total}} \approx 420\ \mathrm{W}
$$

Estimated endurance at constant power:

$$
t = \frac{E_{\mathrm{usable}}}{P_{\mathrm{total}}}
$$

$$
t = \frac{118.4}{420}\times60
\approx 16.9\ \mathrm{minutes}
$$

### Sensitivity to electrical power demand

| Average electrical power | Estimated endurance |
|---|---:|
| 350 W | 20.3 minutes |
| 420 W | 16.9 minutes |
| 500 W | 14.2 minutes |

All three estimates use the same nominal battery energy and 80% usable-energy assumption.

These scenarios illustrate how endurance changes with total power demand. The 350 W and 500 W cases are sensitivity assumptions rather than measured operating points.

Real mission endurance will depend on battery voltage under load, temperature, manoeuvres, wind, sensor operation and the actual propulsion efficiency.

The 20 W auxiliary allowance also requires revision after the flight electronics and sensing payload have been selected.

Biczyski et al. (2020) describe a more detailed multirotor endurance estimation method that incorporates battery discharge characteristics and changing voltage. That approach provides a useful reference for the next iteration of this model.

## Electrical integration considerations

The reference XRotor Micro 20A ESC supports 2–4S LiPo operation and has a published mass of approximately 6.8 g.

The MN3110's highest listed current with the selected 12×4 propeller at 14.8 V is 14 A. This provides an initial basis for evaluating the ESC's current rating.

Thermal performance, installation cooling, control-signal compatibility and transient loads will need to be considered before selecting the final ESC.

The reference ESC does not include a battery eliminator circuit (BEC). The flight controller and auxiliary electronics will therefore require a suitable regulated power supply.

The power distribution system must also accommodate the combined current from all eight propulsion units. At the highest listed motor test point, the sum of motor currents would be approximately 112 A.

The current mass budget includes a general allowance for power distribution and wiring. Conductor sizing, connector selection, voltage drop and electrical protection remain to be developed.

## Implications for the mechanical layout

The propulsion configuration is beginning to establish useful geometric constraints for the new Fusion 360 model.

The selected P12×4 propeller has a diameter of 304.8 mm.

For a flat octocopter with motors positioned at 45-degree intervals, a proposed motor-centre radius of 450 mm produces the following adjacent motor spacing:

$$
s = 2R\sin(22.5^\circ)
$$

$$
s \approx 344.4\ \mathrm{mm}
$$

The nominal clearance between neighbouring propeller disks is therefore:

$$
c = s-D \approx 39.6\ \mathrm{mm}
$$

The overall propeller envelope is approximately:

$$
D_{\mathrm{overall}}=2R+D
$$

**Overall diameter ≈ 1,204.8 mm**

These values provide starting constraints for rotor placement. The final model must accommodate propeller deflection, installation tolerances, mechanical vibration and the selected motor mounts.

### Battery packaging

The Tattu battery's published dimensions are 174 × 66 × 44 mm.

An earlier CAD planning assumption used a central body diameter of 180 mm and a height of 45 mm.

The rectangular footprint of the battery has a diagonal of approximately:

$$
d = \sqrt{174^2+66^2}=186.1\ \mathrm{mm}
$$

This exceeds the proposed 180 mm circular body diameter.

The battery's 44 mm height also leaves very little space within the initial 45 mm body height for mounting and clearance.

The central body geometry will therefore need revision. A diameter of approximately **220 mm** and a larger vertical packaging allowance are reasonable starting parameters to investigate in Fusion 360.

The final dimensions will depend on the internal support structure, battery retention mechanism, controller placement and wiring.

## Design decisions carried forward

The current component-based estimate places the reference octocopter at approximately 3.54 kg, with a hover requirement of 442 gf per motor.

The MN3110 KV700 and P12×4 combination provides a useful initial propulsion reference because its published performance data cover the calculated operating point.

The estimated endurance of 16.9 minutes provides a baseline for examining the aircraft's mission requirements. Further work will establish whether that duration is sufficient for transit, mapping, data transmission and safe return.

For the next design iteration, the main priorities are:

- Establishing the geometry and mass of the central frame and motor arms
- Resolving the complete propeller assembly mass
- Determining the sensing payload and its electrical demand
- Refining propulsion and battery behaviour using measured operating curves
- Evaluating structural loads and available thrust margins

These results will guide the first parametric CAD assembly and subsequent propulsion-system analysis.

## References

[1] T-MOTOR. *MN3110 Navigator Series Motor: Specifications and Propulsion Test Data.*  
https://store.tmotor.com/product/mn3110-motor-navigator-type.html

[2] T-MOTOR. *P12×4 Carbon-Fibre Propeller: Technical Specifications.*  
https://store.tmotor.com/product/polish-carbon-fiber-12x4-prop.html

[3] Hobbywing. *XRotor Micro 20A/30A/35A BLHeli: Specifications.*  
https://www.hobbywing.com/en/products/xrotor-micro-20a30a35a-blheli190.html

[4] Tattu / Foxtech. *G-TECH 14.8 V 4S 10000 mAh 25C LiPo Battery.*  
https://store.foxtech.com/tattu-g-tech-14-8v-4s-10000mah-25c-lipo-battery/

[5] Holybro. *Pixhawk 6C Mini Technical Specifications.*  
https://docs.holybro.com/autopilot/pixhawk-6c-mini/technical-specification

[6] Biczyski, M., Sehab, R., Whidborne, J. F., Krebs, G., & Luk, P. (2020). *Multirotor Sizing Methodology with Flight Time Estimation*. Journal of Advanced Transportation.  
https://doi.org/10.1155/2020/9689604

---

[Initial UAV Sizing and Thrust Requirements](01-design-requirements.md)

[Multirotor Configuration Analysis](02-multirotor-comparison.md)
