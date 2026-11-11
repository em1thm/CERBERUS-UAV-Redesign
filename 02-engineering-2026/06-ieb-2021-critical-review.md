# Literature Review 01 — Information-Motivated UAV Search

*CERBERUS Research Notes · November 2026*

**Paper:** Barry, D., Willig, A., & Woodward, G. (2021). *An Information-Motivated Exploration Agent to Locate Stationary Persons with Wireless Transmitters in Unknown Environments*. Sensors, 21(22), 7695.

https://doi.org/10.3390/s21227695

## The problem investigated

Barry and colleagues developed Information Exploration Behaviour (IEB), a search algorithm for locating an unknown number of stationary radio transmitters in an unfamiliar environment.

Their UAV model combines a downward-facing target confirmation sensor, a neighbouring-obstacle sensor and an omnidirectional radio receiver. The aircraft uses received signals to narrow the search area before inspecting individual locations.

This is particularly relevant to CERBERUS because the algorithm treats searching as a sequence of decisions made under uncertainty.

## How the algorithm works

The environment is divided into discrete cells. Each cell stores a belief value indicating the possible presence of a transmitter.

IEB operates in two phases:

**Search:** Generate candidate paths and select the one with the greatest predicted reduction in uncertainty.

**Discovery:** Once a transmitter is suspected nearby, search the surrounding area more systematically to locate it.

The paper measures model uncertainty with an entropy-like expression:

\[
H(M)=-\sum_{x,y}M_{x,y}\log M_{x,y}
\]

Candidate paths are evaluated using:

\[
I(A)=H(M)-H(M'\mid A)
\]

The authors explicitly note that their entropy measure operates on a belief vector and is not conventional probability entropy.

For planning, visited cells are assumed to have been investigated successfully. This simplifies the predicted information gain and is important when considering how the method might behave with imperfect sensors.

## Experimental evidence

The reported simulation uses a 500 × 500-cell environment with 2 m cells, a vehicle speed of 0.5 m/s and a 10-step look-ahead horizon.

Up to 5,000 candidate paths are sampled during planning. The authors report 1,000 replications per experimental data point.

The algorithm is compared against random walking and a predefined lawnmower search.

Under favourable baseline conditions, IEB locates the simulated transmitters approximately one order of magnitude faster than lawnmower search. Its advantage decreases when radio signals become less reliable.

The experiments demonstrate the value of information-guided exploration under the paper's assumptions. The simulations also assume highly reliable local target confirmation and do not explicitly optimise aircraft energy consumption.

## Relevance to CERBERUS

The original CERBERUS idea involved scanning an earthquake-affected area and marking locations requiring attention.

The 2026 redesign introduces a more specific question: can the aircraft choose which location deserves an additional measurement when its observations may be incorrect?

I intend to investigate this using RGB and thermal sensors whose detection probabilities vary with viewing conditions.

For each map cell, a Bernoulli probability can represent whether a target is present. Its uncertainty can be measured using binary entropy:

\[
h(p)=-p\log_2p-(1-p)\log_2(1-p)
\]

For an observation action \(a\), expected information gain can be defined as:

\[
IG(a)=H(b)-\sum_z P(z\mid a,b)H(b'\mid z,a)
\]

Here, \(b\) is the current belief state, \(z\) a possible measurement, and \(b'\) the belief state after incorporating that measurement.

Unlike the simplified path prediction in IEB, this formulation explicitly considers the probabilities of different sensor outcomes.

### A small illustrative example

Suppose the prior probability of a target in one cell is 0.10.

For a hypothetical sensor with a true positive rate of 0.85 and false positive rate of 0.10, a positive observation updates the probability to approximately 0.486. A negative observation updates it to approximately 0.018.

The expected reduction in binary entropy is approximately **0.186 bits**.

These numbers are illustrative sensor assumptions, not measured CERBERUS performance.

## Introducing an energy constraint

An initial CERBERUS action-selection candidate is:

\[
a^*=\arg\max_a\frac{IG(a)}{E(a)}
\]

The energy cost should account for aircraft movement, observation time, sensor operation and onboard processing.

Actions must also satisfy:

\[
E_{\mathrm{remaining}}-E(a)
\ge E_{\mathrm{return}}(a)+E_{\mathrm{reserve}}
\]

The information-gain-per-energy objective is a proposed starting model. Its practical behaviour, including possible preference for short low-cost observations, will be examined experimentally.

## Implications for our experiments

The most important methodological decision is to give the competing search strategies access to the same sensor information and energy model. This will allow us to measure the contribution of the planning strategy more fairly.

The first simulation will compare fixed coverage, probability-based search, information-gain search and the proposed energy-constrained CERBERUS strategy.

The experiments should vary occlusion, sensor errors, target prevalence and available battery energy. We will report correct target detections, false confirmations, energy consumption and probability calibration.

The 2021 IEB paper establishes an important precedent for adaptive information-driven search. CERBERUS's potential contribution will need to be evaluated against this and more recent work before any originality claim is made.
