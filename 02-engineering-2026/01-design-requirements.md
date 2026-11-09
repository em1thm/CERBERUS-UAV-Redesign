
# CERBERUS 2026 — Preliminary Design Requirements

## 1. Design Objective

Develop a technically feasible search-and-rescue UAV based on the original 2021 CERBERUS concept.

The initial design investigation uses an eight-rotor configuration inspired by the original project.

## 2. Preliminary Design Assumptions

| Parameter | Initial Value |
|---|---|
| Configuration | Eight-rotor multirotor |
| Takeoff mass | 3.2 kg |
| Gravitational acceleration | 9.81 m/s² |
| Target thrust-to-weight ratio | 2.0 |
| Application | Disaster-area mapping and search support |

All numerical values are preliminary assumptions subject to component selection and validation.

## 3. Hover Thrust Calculation

Total weight:

W = m × g

W = 3.2 × 9.81 = 31.392 N

Hover thrust per motor:

T = W / 8 = 3.924 N

Equivalent thrust:

T = 400 gf per motor

Target maximum static thrust per motor:

T_max = 800 gf

## 4. Engineering Questions

1. Is an eight-rotor configuration justified by the payload requirements?
2. How does rotor count affect total system mass and efficiency?
3. What motor and propeller combinations meet the thrust requirement?
4. What battery capacity is required for the mission?
5. How should the sensing payload be mechanically integrated?
6. What level of flight and sensing autonomy is achievable?

## 5. Validation Status

Current stage: Preliminary analytical design.

The design has not yet been validated through physical testing.

Next step: Compare quadcopter, hexacopter and octocopter configurations.
