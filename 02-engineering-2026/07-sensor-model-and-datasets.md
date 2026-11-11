# CERBERUS — Sensor Reliability and Dataset Selection

*Research Note 02 · November 2026*

## Why sensor reliability matters

The proposed CERBERUS search algorithm will decide which areas deserve another observation based on the information already collected.

For this decision to be useful, the system needs to estimate how likely each sensor is to detect a person under different viewing conditions.

An RGB camera and a thermal camera may provide complementary observations, but their reliability varies with distance, viewing angle, illumination, occlusion and environmental conditions.

The first task is to develop a measurable sensor model that can eventually support the active search algorithm.

## Available datasets

### HIT-UAV — Suo et al. (2023)

HIT-UAV contains 2,898 thermal images captured from UAVs. The dataset provides annotations for people and several vehicle categories, together with flight altitude and camera perspective information.

The recorded altitudes range from 60 to 130 metres, while camera perspectives range from 30 to 90 degrees.

This dataset is suitable for investigating how thermal person detection changes with imaging geometry and day/night conditions.

It contains infrared imagery and therefore supports a thermal-only detection baseline.

Paper: https://doi.org/10.1038/s41597-023-02066-6

Dataset: https://zenodo.org/records/7633134

### RGBTDronePerson — Zhang et al. (2023)

RGBTDronePerson contains 6,125 pairs of visible and thermal UAV images, with 70,880 annotated instances reported by the authors.

The dataset includes challenging small targets, differences in modality quality and spatial misalignment between RGB and thermal imagery.

It provides a suitable starting point for examining how the two sensing modalities behave individually and together.

Paper: *Drone-based RGBT Tiny Person Detection*, ISPRS Journal of Photogrammetry and Remote Sensing, 204, 61–76.

Dataset information: https://nnnnerd.github.io/RGBTDronePerson/

### AIResQ — Büttner et al. (2026)

AIResQ includes 9,788 thermal images of people in different environments and body positions, with resolutions up to 2048 × 1536 pixels.

The authors also developed a separate benchmark containing 1,988 thermal images from search-and-rescue-related drone operations and exercises.

The benchmark provides an opportunity to investigate the performance of thermal detectors in more realistic search scenarios.

Access permissions and dataset licensing must be checked before downloading and redistributing material.

Paper: https://doi.org/10.1038/s41597-026-07663-9

Benchmark: https://zenodo.org/records/17405074

## Proposed probabilistic model

For each search-map cell, let:

\[
H_i\in\{0,1\}
\]

represent the presence or absence of a person.

Sensor observations depend on imaging conditions:

\[
q=(h,\theta,l,o)
\]

where the variables describe altitude, viewing angle, lighting and occlusion.

The first parameters to estimate are the true positive and false positive rates:

\[
TPR(q)=P(z^+\mid H=1,q)
\]

\[
FPR(q)=P(z^+\mid H=0,q)
\]

These values will be estimated from detector outputs matched against annotated ground truth.

For a single binary observation, the target probability can be updated using Bayes' rule.

For example:

\[
P(H\mid z^+)=
\frac{TPR\cdot P(H)}
{TPR\cdot P(H)+FPR\cdot(1-P(H))}
\]

A preliminary illustration using a target prior of 0.10, a true positive rate of 0.85 and a false positive rate of 0.10 gives:

\[
P(H\mid z^+)\approx0.486
\]

The expected information gain for this illustrative binary observation is approximately 0.186 bits.

These parameters are hypothetical and will be replaced with experimentally estimated values.

## RGB–thermal dependence

RGB and thermal observations may be correlated because both sensors view the same target, environment and occluding objects.

The combined model should therefore consider:

\[
P(z_{RGB},z_T\mid H,q)
\]

Conditional independence may be used as an explicitly labelled baseline in early simulations. A more realistic model will need to estimate joint observation behaviour from paired data.

## Calibration and evaluation

The initial evaluation will compare observed detection outcomes against annotated targets.

Measurements will include true positive rate, false positive rate, precision, recall and probability calibration.

A detection must first be matched to the annotated target using a predefined localization criterion.

Performance will be examined across available imaging conditions. Image-level object detection scores will be calibrated before they are interpreted as probabilities.

Where sequence information is available, training and testing data should be separated by recording or scene to reduce the risk of nearly identical frames appearing in both sets.

Dataset limitations and changes in operating conditions will be documented.

## Connection to active search

The calibrated observation model will provide likelihood estimates for the CERBERUS belief map.

The search planner will use these estimates to calculate expected information gain for candidate observations.

The planned action-selection problem is:

\[
a^*=\arg\max_a \frac{\mathbb{E}[IG(a)]}{E(a)}
\]

subject to a safe-return energy constraint.

Information gain is a planning quantity. The actual success of the system will be measured using correct target confirmations, false alarms, detection time and energy consumption.

The model's ability to generalize from existing datasets to the intended CERBERUS operating environment will require separate validation.

## Current status

The datasets and relevant publications have been identified and reviewed at the documentation level.

No detector has yet been trained, calibrated or evaluated as part of the CERBERUS redesign.

The next stage is to inspect the available annotation formats and establish a reproducible baseline evaluation protocol.
