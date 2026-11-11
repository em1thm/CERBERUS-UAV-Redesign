# CERBERUS — Research Direction (2026)

*Working Research Note | November 2026*

## Revisiting the original idea

Our 2021 CERBERUS project proposed using an ultrasonic-equipped drone to investigate earthquake debris and communicate locations of interest to rescue teams.

As I began revisiting the design in 2026, I realised that choosing the aircraft and its sensors would require a clearer understanding of the information we wanted to obtain.

This led to a new question: how could a drone decide where to investigate next when its sensor measurements are uncertain and its available energy is limited?

## Research question

Can a search-and-rescue UAV use uncertain observations from multiple sensors to select its next measurement location and obtain more verified target information per unit of energy than a fixed search pattern?

## Proposed approach

I plan to investigate an adaptive search strategy that combines three factors:

- **Sensor uncertainty:** How reliable is each observation?
- **Expected information gain:** How much could another measurement reduce uncertainty?
- **Energy consumption:** How much energy would the drone need to reach and observe the selected location?

The aircraft would maintain a map containing target probabilities and observation confidence. After each measurement, the map would be updated and a new observation location selected.

The decision process would also consider the energy required for a safe return.

## First experimental comparison

The initial experiment will use a controlled simulation with known target positions, visual obstructions and possible false detections.

Four search approaches will be evaluated under the same conditions:

1. Fixed coverage search
2. Probability-guided search
3. Information-gain-based search
4. CERBERUS uncertainty- and energy-aware search

The evaluation will measure correctly confirmed targets under a fixed energy budget, target recall, false confirmations, localization error, detection time and probability calibration.

Confirmation thresholds and ground-truth evaluation rules will be established before testing.

## Initial sensing architecture

RGB and thermal imaging are the first sensing candidates. Three-dimensional mapping will support spatial localization and navigation.

LiDAR, acoustic sensing and radar remain under investigation. Their inclusion will depend on physical feasibility, power requirements, payload mass and experimental evidence.

The final aircraft configuration will be selected after the sensing requirements are established.

## Current research status

The repository currently contains the original 2021 presentation and preliminary aircraft sizing, multirotor comparison and propulsion calculations.

The adaptive search algorithm and sensing architecture are proposed research developments. Comparative experiments, simulation results and hardware validation have yet to be completed.

The next stage will focus on defining the probabilistic sensor models, energy constraints and evaluation protocol.

The originality of the proposed method will be assessed through a review of related scientific publications, datasets and patents from 2021 to 2026.
