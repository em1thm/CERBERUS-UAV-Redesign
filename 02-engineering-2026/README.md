# CERBERUS — Engineering Development Log (2026)

## Returning to the project

When I revisited CERBERUS in 2026, I started by looking at the eight-rotor drone we had proposed during the NASA Space Apps Challenge in 2021.

The original presentation described how the aircraft could support search-and-rescue teams, but several engineering questions remained open. I wanted to understand how much thrust the aircraft would need, how its propulsion system would affect flight endurance, and whether the proposed sensing technology could operate under realistic conditions.

I decided to begin with the aircraft's basic mechanical and propulsion requirements before developing a new 3D model.

## 1. Starting with thrust requirements

My initial calculation used an assumed takeoff mass of **3.2 kg** and a target thrust-to-weight ratio of **2:1**.

For an eight-motor configuration, this gave approximately **400 gf of hover thrust per motor**, with a preliminary target of 800 gf maximum static thrust per motor.

The 3.2 kg figure was a starting assumption. I needed a component-level mass estimate to understand how realistic it was.

[Initial design requirements and calculations](01-design-requirements.md)

## 2. Comparing rotor configurations

The original CERBERUS illustration featured eight motors. I wanted to examine what advantages this arrangement might offer over a quadcopter or hexacopter.

I compared the three configurations using the same aircraft mass, air density and 10-inch propeller diameter.

Using ideal actuator-disk momentum theory, the estimated induced powers were:

| Configuration | Ideal induced power |
|---|---:|
| Quadcopter | 249.6 W |
| Hexacopter | 203.8 W |
| Octocopter | 176.5 W |

Under these assumptions, increasing the number of identical rotors increased total disk area and reduced the calculated induced power.

This result led me to consider rotor disk area alongside the additional weight and complexity of a larger propulsion system. A final comparison will require actual motor and propeller efficiency data, updated aircraft masses and structural design calculations.

For now, I am keeping the eight-rotor configuration as the reference for the redesign.

[Multirotor configuration comparison](02-multirotor-comparison.md)

## 3. Revisiting the aircraft mass

The next step was to estimate the weight of the components needed to build an octocopter.

I used published specifications for a T-MOTOR MN3110 KV700 motor, a reference propeller, a 4S LiPo battery and a flight controller. I then added preliminary estimates for the frame, landing gear, wiring and sensing equipment.

The resulting mass budget was approximately **3,535 g**, compared with my initial assumption of 3,200 g.

This increased the estimated hover thrust requirement to approximately **442 gf per motor**.

I also calculated a preliminary endurance estimate using a 4S 10 Ah battery, 80% usable nominal energy and an assumed average electrical load of 420 W. This produced an estimate of approximately **16.9 minutes**.

The mass budget combines published component data with estimated structural and payload masses. The endurance calculation is therefore a preliminary result that will be refined after the propulsion system and CAD model are developed.

[Mass and propulsion budget](03-mass-and-propulsion-budget.md)

## 4. The sensing question

The original CERBERUS concept proposed using ultrasonic waves to investigate the ground beneath earthquake debris.

I am now examining how acoustic waves behave when passing between materials such as air, concrete and soil. This will help determine the conditions under which ultrasonic sensing could provide useful information.

I also intend to examine radar, thermal imaging and 3D mapping technologies as potential sensing approaches for the redesigned aircraft.

The sensing architecture remains an open design decision.

## 5. Moving towards a 3D design

The next stage is to create a parametric octocopter model in Autodesk Fusion.

I plan to begin with the central frame, motor arms, propulsion units and battery placement. The model will allow me to estimate structural mass more accurately and examine how the different components fit together.

After modelling the aircraft, I will return to the propulsion and endurance calculations using the updated geometry and component requirements.

## Current progress — November 2026

The repository currently contains the original 2021 project materials, preliminary thrust calculations, a multirotor configuration comparison and an initial component-level mass budget.

The 2026 redesign is at the analytical design stage. CAD modelling, software implementation, simulation and experimental validation are the next stages of development.

[Return to the main CERBERUS project page](../README.md)
