# Multirotor Configuration Analysis

*CERBERUS Engineering Redesign — November 2026*

## Why reconsider the original octocopter?

The drone we designed for CERBERUS in 2021 had eight rotors. When I returned to the project, I wanted to examine whether this configuration offered practical advantages for a search-and-rescue aircraft carrying additional sensing equipment.

The number of rotors influences several aspects of an aircraft's design, including thrust distribution, available rotor disk area, structural mass, electrical complexity and the ability to respond to propulsion failures.

I began by comparing quadcopter, hexacopter and octocopter configurations under identical reference conditions.

## Thrust distribution

For the initial comparison, I used a total takeoff mass of 3.2 kg, an air density of 1.225 kg/m³ and identical 10-inch propellers.

The target static thrust-to-weight ratio was set at 2:1, consistent with the preliminary sizing analysis.

The aircraft's weight is:

$$
W = mg = 3.2 \times 9.81 = 31.392\ \mathrm{N}
$$

In stationary hover, assuming equal thrust distribution:

$$
T_{\mathrm{rotor}} = \frac{W}{N}
$$

where \(N\) is the number of rotors.

| Configuration | Hover thrust per rotor | Target maximum thrust per rotor |
|---|---:|---:|
| Quadcopter (4) | 800 gf | 1,600 gf |
| Hexacopter (6) | 533 gf | 1,067 gf |
| Octocopter (8) | 400 gf | 800 gf |

At equal aircraft mass, increasing the number of rotors distributes the required lifting force across more propulsion units.

For CERBERUS, this is relevant because the aircraft must accommodate a battery, flight-control electronics and sensing equipment. The additional motors also contribute to the total mass, so their effect must be evaluated as part of the complete aircraft.

## Rotor disk area and induced power

The next question was how rotor count might influence the power required to maintain hover.

According to actuator-disk momentum theory, a rotor generates thrust by accelerating air downwards. The ideal induced power depends on the required thrust, air density and the area through which the rotor accelerates the airflow.

For a system of identical, non-overlapping rotors with equal thrust distribution:

$$
A_{\mathrm{total}} = N\pi\left(\frac{D}{2}\right)^2
$$

where \(D\) is the propeller diameter.

The ideal induced power is:

$$
P_{\mathrm{ideal}} =
\frac{(mg)^{3/2}}
{\sqrt{2\rho A_{\mathrm{total}}}}
$$

This relationship is derived from momentum theory and is used in rotorcraft and eVTOL aircraft performance analysis [1, 2].

Using the initial 3.2 kg reference mass and 10-inch (0.254 m) propellers:

| Configuration | Total rotor disk area | Disk loading | Ideal induced power |
|---|---:|---:|---:|
| Quadcopter | 0.2027 m² | 154.9 N/m² | 249.6 W |
| Hexacopter | 0.3040 m² | 103.3 N/m² | 203.8 W |
| Octocopter | 0.4054 m² | 77.4 N/m² | 176.5 W |

The octocopter produces the lowest theoretical induced power in this comparison. With eight identical propellers, its total rotor disk area is twice that of the quadcopter.

### What happens if total rotor disk area remains constant?

I also considered a second comparison to examine the effect of rotor count independently of total disk area.

Keeping the combined rotor disk area at approximately 0.4054 m² requires different propeller diameters:

| Configuration | Propeller diameter | Ideal induced power |
|---|---:|---:|
| Quadcopter | 14.14 inches | 176.5 W |
| Hexacopter | 11.55 inches | 176.5 W |
| Octocopter | 10.00 inches | 176.5 W |

Under the ideal actuator-disk assumptions, equal aircraft weight and equal total rotor disk area produce the same induced power.

This result helped clarify the earlier comparison. The reduction in theoretical power with eight 10-inch rotors comes from the greater combined disk area.

The choice of rotor count therefore needs to consider the available frame dimensions, propeller clearance, propulsion efficiency and additional structural mass.

Real propellers also experience aerodynamic profile losses. Rotor interference, motor efficiency, electrical losses and operating conditions must be included when estimating actual battery power.

## Structural and electrical considerations

Each configuration introduces different mechanical requirements.

A quadcopter uses four propulsion units and generally requires fewer motor mounts, ESCs and associated electrical connections. Larger individual thrust requirements may lead to different motor and propeller choices.

A hexacopter distributes the lifting load across six rotors, providing an intermediate configuration in terms of component count and mechanical complexity.

An octocopter uses eight propulsion units. For CERBERUS, this configuration offers additional flexibility in thrust distribution and potentially useful redundancy. Its design also requires more motor mounts, wiring, electronic speed controllers and structural connections.

These differences will affect the final takeoff mass and the amount of electrical energy required during operation.

Biczyski et al. (2020) propose a multirotor sizing methodology based on selecting compatible propeller, motor, ESC and battery components and evaluating their operating characteristics [2].

This approach is relevant to the next stage of CERBERUS because the propulsion system should be assessed as a complete assembly.

## Motor failure and control allocation

Reliability is particularly important for an aircraft intended to operate near damaged structures.

With additional propulsion units, a multirotor can potentially redistribute thrust following a motor failure. The outcome depends on the aircraft geometry, remaining thrust capacity and flight-control strategy.

Wen et al. (2021) investigated motor failures in hexacopters and demonstrated that controllability depends on the arrangement of the failed motors and the redistribution of control forces [3].

More recently, Yao and Yang (2024) investigated fault-tolerant control allocation for octocopters, using a nonlinear optimisation approach to redistribute actuator commands following faults. Their reported validation was based on simulations [4].

These findings suggest that the eight-rotor CERBERUS architecture is worth investigating for fault tolerance.

A future analysis should examine the forces and moments that the remaining motors can generate after a failure, including whether the aircraft can maintain sufficient control for an emergency landing.

## Revisiting the comparison with the updated mass estimate

The initial comparison used the same 3.2 kg reference mass for all three configurations.

A subsequent component-level estimate for the octocopter produced a mass of approximately 3.535 kg.

At this revised mass, the eight-rotor aircraft requires:

- Hover thrust: approximately 442 gf per motor
- Maximum static thrust target at 2:1: approximately 884 gf per motor
- Ideal induced hover power with eight 10-inch rotors: approximately 204.9 W

The updated estimate accounts for the increased assumed aircraft weight. It will be refined further using the selected propulsion components and the structural model.

The quadcopter and hexacopter alternatives will also require individual mass budgets before a complete system-level comparison can be made.

## Current design direction

For the next stage of CERBERUS, I will retain the original flat octocopter arrangement as the reference configuration.

This allows the new CAD design to remain connected to our 2021 concept while providing a basis for evaluating rotor spacing, structural layout and payload integration.

The final configuration will depend on the results of component-level propulsion analysis, structural mass estimation, electrical power requirements and fault-tolerance evaluation.

The next engineering task is to develop the aircraft geometry and refine the mass and propulsion budget using the selected motor–propeller combination.

## References

[1] Ugwueze, O., Statheros, T., Horri, N., Bromfield, M. A., & Simo, J. (2023). *An Efficient and Robust Sizing Method for eVTOL Aircraft Configurations in Conceptual Design*. Aerospace, 10(3), 311. https://doi.org/10.3390/aerospace10030311

[2] Biczyski, M., Sehab, R., Whidborne, J. F., Krebs, G., & Luk, P. (2020). *Multirotor Sizing Methodology with Flight Time Estimation*. Journal of Advanced Transportation. https://doi.org/10.1155/2020/9689604

[3] Wen, F.-H., Hsiao, F.-Y., & Shiau, J.-K. (2021). *Analysis and Management of Motor Failures of Hexacopter in Hover*. Actuators, 10(3), 48. https://doi.org/10.3390/act10030048

[4] Yao, J., & Yang, Y. (2024). *Fault-tolerant control allocation for octocopter UAV*. 39th Youth Academic Annual Conference of Chinese Association of Automation (YAC). https://doi.org/10.1109/YAC63405.2024.10598762

---

[Initial UAV Sizing and Thrust Requirements](01-design-requirements.md)

[Mass and Propulsion Budget](03-mass-and-propulsion-budget.md)
