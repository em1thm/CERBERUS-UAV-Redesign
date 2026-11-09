
# CERBERUS 2026 — Multirotor Configuration Comparison

## Objective

Evaluate quadcopter, hexacopter and octocopter configurations for a search-and-rescue UAV.

The original CERBERUS concept featured an eight-motor design.

## Preliminary Assumptions

- Takeoff mass: 3.2 kg
- Gravity: 9.81 m/s²
- Air density: 1.225 kg/m³
- Propeller diameter: 10 inches
- Target thrust-to-weight ratio: 2.0

These values are preliminary engineering assumptions.

## 1. Thrust Requirements

Total weight:

W = 3.2 × 9.81 = 31.392 N

| Configuration | Hover Thrust / Motor | Target Maximum Thrust / Motor |
|---|---:|---:|
| Quadcopter | 800 gf | 1600 gf |
| Hexacopter | 533 gf | 1067 gf |
| Octocopter | 400 gf | 800 gf |

## 2. Ideal Induced Power

Using actuator-disk momentum theory:

P = (m × g)^1.5 / sqrt(2 × rho × A)

A = N × pi × (D/2)^2

| Configuration | Total Disk Area | Ideal Induced Power |
|---|---:|---:|
| Quadcopter | 0.2027 m² | 249.6 W |
| Hexacopter | 0.3040 m² | 203.8 W |
| Octocopter | 0.4054 m² | 176.5 W |

These values represent ideal induced power, not actual electrical power consumption.

## 3. Design Trade-offs

### Quadcopter
- Fewer propulsion components
- Lower mechanical complexity
- Limited conventional single-motor failure tolerance

### Hexacopter
- Intermediate propulsion complexity
- Additional control allocation possibilities
- Potential motor-failure tolerance depending on design

### Octocopter
- Greater number of propulsion units
- Lower thrust demand per motor at equal total mass
- Potential redundancy advantages
- Increased component count and structural complexity

## 4. Limitations

The comparison assumes equal total aircraft mass and identical propeller diameters.

Actual aircraft masses, motor efficiencies, rotor interference, structural loads and battery requirements remain unverified.

## 5. Preliminary Conclusion

The original eight-motor CERBERUS architecture will remain the reference configuration.

Final architecture selection requires component-level mass budgeting, propulsion data and mission-performance analysis.

Status: Preliminary analytical comparison.
