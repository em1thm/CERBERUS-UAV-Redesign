# CERBERUS — First UAV Sizing Calculations

*Engineering Redesign, 2026*

## Where I started

When I began revisiting CERBERUS, one of my first questions was how much thrust the aircraft would need to remain airborne.

Our original 2021 design featured eight rotors, but we had not calculated the propulsion requirements of that configuration in the available presentation.

I began with a simplified model to establish an initial reference for motor selection.

## 1. Initial assumptions

For this first calculation, I used the following values:

| Parameter | Value |
|---|---|
| Aircraft configuration | Octocopter |
| Number of motors | 8 |
| Assumed takeoff mass | 3.2 kg |
| Gravitational acceleration | 9.81 m/s² |
| Target maximum thrust-to-weight ratio | 2:1 |

The 3.2 kg takeoff mass was an initial assumption, chosen to explore the propulsion requirements before developing a detailed component list.

I used a 2:1 static thrust-to-weight ratio as a preliminary design target to provide thrust headroom for manoeuvring and control.

## 2. Calculating the required thrust

The total weight of the aircraft is:

**W = m × g**

W = 3.2 × 9.81

**W = 31.392 N**

For an octocopter, assuming equal thrust distribution across all eight motors:

**T_hover = W / 8**

T_hover = 31.392 / 8

**T_hover = 3.924 N per motor**

Converting this into gram-force:

3.924 / 0.00980665 ≈ 400 gf

Each motor would therefore need to produce approximately **400 gf of thrust** to maintain a stationary hover under these assumptions.

With the preliminary 2:1 thrust-to-weight target:

**T_max = 2 × 400 = 800 gf per motor**

This establishes an initial minimum target for the motor-propeller combination's maximum static thrust.

## 3. What this calculation helped me understand

The calculation gave me a starting point for evaluating possible propulsion systems.

It also raised another question: how accurately could I estimate the total mass of an aircraft that would need to carry eight motors, a battery, flight-control electronics and additional sensing equipment?

To investigate that question, I moved on to a comparison of multirotor configurations and a preliminary component-level mass budget.

## 4. Updating the initial assumption

After considering reference components and estimated structural masses, the preliminary octocopter mass budget increased to **3,535 g**.

At this revised mass, the estimated hover thrust becomes:

T_hover = 3535 / 8

**T_hover ≈ 442 gf per motor**

The revised estimate will be used as a starting point for the next stage of design.

The remaining uncertainties include frame mass, sensing payload mass, motor efficiency and actual flight power consumption.

## 5. Next calculations

The following documents continue this investigation:

- [Comparison of four-, six- and eight-rotor configurations](02-multirotor-comparison.md)
- [Component mass and propulsion budget](03-mass-and-propulsion-budget.md)

These results are preliminary analytical estimates. The aircraft's performance will need to be evaluated using component specifications, CAD-based mass estimates and simulation or experimental data.
