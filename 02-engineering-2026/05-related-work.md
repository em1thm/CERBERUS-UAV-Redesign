# CERBERUS — Related Research and Open Questions

*Initial literature review | November 2026*

## Research context

The 2026 CERBERUS redesign investigates how a search-and-rescue UAV could use uncertain sensor observations to decide where to measure next while operating within a limited energy budget.

Before developing the algorithm, I am examining research in active perception, probabilistic target search, aerial thermal imaging and energy-aware path planning.

The studies below establish a starting point for the literature review. Their experimental methods, datasets and evaluation procedures will guide the development of CERBERUS.

## Information-driven search

**An Information-Motivated Exploration Agent to Locate Stationary Persons with Wireless Transmitters in Unknown Environments (2021)**

This study develops a Bayesian search algorithm that uses predicted information gain and observations from multiple sensors to locate stationary wireless transmitters in simulated environments.

It provides an important foundation for CERBERUS's proposed belief-map updates and adaptive observation decisions.

The search targets are wireless transmitters, while CERBERUS intends to examine visual and thermal evidence of people.

[Read paper — Sensors, 2021](https://doi.org/10.3390/s21227695)

## Thermal detection and sensor data

**HIT-UAV: A High-Altitude Infrared Thermal Dataset for UAV-Based Object Detection (2023)**

Suo and colleagues published a dataset containing 2,898 annotated thermal images from UAV flights. Its metadata include flight altitude, camera perspective and environmental conditions.

The dataset could support preliminary experiments on thermal human detection and the influence of viewing geometry.

It contains thermal imagery; paired RGB–thermal fusion would require additional appropriate data.

[Read paper — Scientific Data, 2023](https://doi.org/10.1038/s41597-023-02066-6)

## Energy-aware flight planning

**Energy-Aware Multi-UAV Coverage Mission Planning With Optimal Speed of Flight (2024)**

Datsko and colleagues investigate planning coverage missions while considering UAV energy consumption and flight speed.

The work is relevant to the physical energy model required for CERBERUS. A useful next step is to examine how the authors calculate flight energy and incorporate those costs into trajectory optimisation.

[Read paper — IEEE Robotics and Automation Letters, 2024](https://doi.org/10.1109/LRA.2024.3358581)

## Search under occlusion

**Enhancing UAV Search under Occlusion using Next Best View Planning (2025)**

Strand and colleagues investigate next-best-view planning for UAV searches in environments where objects may be obscured.

This is particularly relevant to CERBERUS because a target may become detectable from another observation angle.

The experimental setup and baseline methods should be examined before defining our own occlusion scenarios.

[Read paper — IEEE JSTARS, 2025](https://doi.org/10.1109/JSTARS.2025.3638881)

## Multimodal detection reliability

**Seeing Through Sparse Foliage: Quality–Occlusion-Guided RGB–Thermal Fusion for Drone-Based Person Detection (2026)**

Gui and colleagues examine RGB–thermal fusion for detecting partially obscured people. Their approach accounts for image quality and occlusion characteristics.

This work is relevant to estimating the reliability of observations from different sensors.

For CERBERUS, the next research question is how such reliability estimates might influence the decision to revisit an area.

[Read paper — Remote Sensing, 2026](https://doi.org/10.3390/rs18050774)

## Energy-constrained informative paths

**EA-IPP2n: Energy-Aware Informative Path Planning Algorithm for UAVs (2026)**

This paper evaluates informative UAV path planning with explicit time and energy constraints.

It provides a direct comparison point for CERBERUS's proposed information-gain-per-energy strategy.

The optimisation objective, constraints and baseline algorithms need closer examination to identify possible methodological differences.

[Read paper — IEEE Access, 2026](https://doi.org/10.1109/ACCESS.2026.3673288)

## Research question carried forward

The proposed CERBERUS investigation focuses on whether reliability-aware RGB–thermal observations, active reobservation and an energy-constrained decision policy can improve correctly verified target detection under an equal energy budget.

The first experimental comparison will include fixed coverage, probability-guided search, information-gain-based search and the proposed CERBERUS strategy.

A systematic comparison with existing publications is still required to establish the level of methodological originality.

## Work remaining

The next literature review stage will examine the mathematical models, available source code, experimental conditions and reported performance metrics of these papers.

Additional work will cover relevant patents, publicly available datasets and sensor limitations.

The results will be used to refine the CERBERUS algorithm and define a reproducible experimental protocol.
