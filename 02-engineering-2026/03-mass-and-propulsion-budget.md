
# CERBERUS 2026 — Mass and Propulsion Budget

## 1. Objective

Establish a preliminary mass budget and evaluate a real motor-propeller combination for the original eight-rotor CERBERUS architecture.

Status: Preliminary engineering analysis.

## 2. Reference Propulsion System

Motor: T-MOTOR MN3110 KV700
Propeller: T-MOTOR P12x4
Battery: 4S LiPo (14.8 V nominal)

Manufacturer motor data:
- Motor mass including cables: 99 g
- Motor diameter: 37.7 mm
- Motor height: 28.5 mm
- Measured thrust at 50% throttle: 420 gf
- Electrical power at this point: 47.36 W
- Maximum measured thrust with this configuration: 1290 gf

Source:
https://store.tmotor.com/product/mn3110-motor-navigator-type.html

## 3. Preliminary Mass Budget

| Component | Mass (g) | Basis |
|---|---:|---|
| 8 motors | 792 | Manufacturer |
| 8 propellers | 116 | Catalog; mass definition to verify |
| 8 ESCs | 54 | Manufacturer, rounded |
| 4S 10000 mAh battery | 921 | Product specification |
| Flight controller | 42 | Manufacturer, rounded |
| Frame and arms | 750 | Estimate |
| Landing gear | 180 | Estimate |
| Power distribution and wiring | 150 | Estimate |
| GPS and telemetry | 90 | Estimate |
| Camera and sensors | 240 | Estimate |
| Design allowance | 200 | Estimate |
| TOTAL | 3535 | Rounded mass budget |

The previous 3.2 kg design mass is superseded as a preliminary estimate.

## 4. Thrust Requirements

Takeoff mass = 3.536 kg

Hover thrust per motor:

3536 / 8 = 442 gf

Approximate measured maximum thrust:
8 x 1290 = 10320 gf

Approximate static thrust-to-weight ratio:
10320 / 3536 = 2.92

This does not establish flight performance or fault tolerance.

## 5. Preliminary Endurance

Battery nominal energy:
14.8 V x 10 Ah = 148 Wh

Assumed usable fraction = 80%

Estimated propulsion power = 400 W
Estimated auxiliary power = 20 W

Total estimated power = 420 W

Estimated endurance:
148 x 0.8 / 420 x 60 = 16.9 minutes

Actual endurance requires validation.

## 6. Preliminary Frame Geometry

Rotor configuration: Flat octocopter
Propeller diameter: 304.8 mm
Proposed motor-center radius: 450 mm

Approximate overall rotor envelope:
2 x 450 + 304.8 = 1204.8 mm

Adjacent rotor-disk clearance:
2 x 450 x sin(22.5 degrees) - 304.8
= approximately 39.6 mm

## 7. Open Engineering Questions

- Validate complete propeller assembly mass.
- Refine frame mass using Fusion 360.
- Evaluate motor and ESC thermal margins.
- Quantify payload power consumption.
- Assess vibration and structural loads.
- Establish practical flight reserve and mission duration.
- Compare the flat octocopter with alternative configurations.

## 8. Technical References

Motor:
https://store.tmotor.com/product/mn3110-motor-navigator-type.html

Propeller:
https://store.tmotor.com/product/polish-carbon-fiber-12x4-prop.html

Battery:
https://store.foxtech.com/tattu-g-tech-14-8v-4s-10000mah-25c-lipo-battery/

Flight controller:
https://holybro.com/products/pixhawk-6c-mini

ESC:
https://support.hobbywingdirect.com/hc/en-us/article_attachments/29229264608915
