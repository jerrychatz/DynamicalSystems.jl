# Contents
The _module_ `DynamicalSystems` re-exports all following functionality, grouped into different packages.

## `DynamicalSystemsBase`
* Intuitive, consistent APIs for the definition of general dynamical systems under a unified struct [`DynamicalSystem`](@ref). The following combinations are possible:
  * Continuous or Discrete systems. Continuous systems use [DifferentialEquations.jl](https://diffeq.sciml.ai/latest/) for solving the ODE problem.
  * In-place or out-of-place (large versus small systems).
  * Auto-differentiated or not (for the Jacobian function).


* Automatic "completion" of the dynamics of the system with numerically computed Jacobians, in case they are not provided by the user.
* Robust implementations of all kinds of integrators, that evolve the system, many states of the system, or even deviation vectors. See the [Advanced documentation](@ref) for this.
* Library of [Predefined Dynamical Systems](@ref) that have been used extensively in scientific research.

## `DelayEmbeddings`
Is a package for performing delay coordinate embeddings and finding optimal parameters for doing so.
* Unified & dedicated interface for numerical data: [`Dataset`](@ref).
* Flexible, super-efficient and abstracted [Delay Coordinates Embedding](@ref) interface.
    * Supports multiple dimensions and multiple timescales.

* Methods that estimate optimal embedding parameters: the delay time ([`estimate_delay`](@ref)) and the number of temporal neighbors  ([`estimate_dimension`](@ref)).
* [Unified approach](@ref) of finding optimal embeddings (advanced algorithms).
* Fast calculation of mutual information: [`mutualinformation`](@ref).

## `ChaosTools`
Is a package that has many algorithms for chaotic dynamical systems. All algorithms are independent of each other but they are also not expansive enough to be a standalone package.


### [Orbit Diagrams & PSOS](@ref)

1. Orbit diagrams (aka bifurcation diagrams) of maps: [`orbitdiagram`](@ref).
2. Poincaré surfaces of section for continuous systems: [`poincaresos`](@ref).
3. Automated production of orbit diagrams for continuous systems: [`produce_orbitdiagram`](@ref).

### [Lyapunov Exponents](@ref)

The following treat systems where the equations of motion are known:

1. Maximum Lyapunov exponent for both discrete and continuous systems: [`lyapunov`](@ref).
2. Lyapunov *spectrum* for both discrete and continuous systems: [`lyapunovs`](@ref).

### [Detecting & Categorizing Chaos](@ref)

1. The Generalized Alignment Index: $\text{GALI}_k$ : [`gali`](@ref).
    * Implemented for both discrete and continuous systems.
2. A test to categorize strong chaos, partially predictable chaos and regular behavior: [`predictability`](@ref).
    * Implemented for both discrete and continuous systems.
1. The 0-1 test for chaos: [`testchaos01`](@ref)
1. The expansion entropy: [`expansionentropy`](@ref).

### [Entropies and Dimensions](@ref)

1. Generalized (Renyi) entropy: [`genentropy`](@ref).
2. Permutation entropy: [`permentropy`](@ref).
2. Fast and cheap (memory-wise) method for computing entropies of large datasets.
3. Generalized dimensions (e.g. capacity dimension, information dimension, etc.): [`generalized_dim`](@ref).
3. Kaplan-Yorke dimension: [`kaplanyorke_dim`](@ref).

And, in order to automatically deduce dimensions, we also offer methods for:

* Partitioning a function $y(x)$ vs. $x$ into regions where it is approximated by a straight line, using a flexible algorithm with a lot of control over the outcome. See [`linear_regions`](@ref).
* Detection of largest linear region of a function $y(x)$ vs. $x$ and extraction of the slope of this region.

### [Nonlinear Timeseries Analysis](@ref)

1. Broomhead-King coordinates: [`broomhead_king`](@ref).
3. Numerically determining the maximum Lyapunov exponent of a (e.g. experimentally) measured timeseries: [`numericallyapunov`](@ref).

### [Periodicity & Ergodicity](@ref)

1. Numerical method to find unstable and stable fixed points of *any order* $n$ of a discrete map (of any dimensionality): [`periodicorbits`](@ref).
    * Convenience functions for defining and realizing all possible combinations of $\mathbf{\Lambda}_k$ matrices required in the above method.
2. Estimating the period of a timeseries: [`estimate_period`](@ref).
3. Return and transit time statistics for a subset of the state space: [`transit_time_statistics`](@ref).

## `RecurrenceAnalysis`
`RecurrenceAnalysis` offers tools to compute and analyze [Recurrence Plots](https://en.wikipedia.org/wiki/Recurrence_plot), a field called [Recurrence Quantification Analysis](https://en.wikipedia.org/wiki/Recurrence_quantification_analysis).

* [Recurrence Plots](@ref), with cross-recurrence and joint-recurrence.
* [Recurrence Quantification Analysis](@ref) (RQA):
  * Recurrence rate, determinism, average/maximum diagonal length, divergence, laminarity, trend, entropy, trapping time, average/maximum vertical length.
  * Fine-tuning of the algorithms that compute the above (e.g. Theiler window and many more)
  * [Windowed RQA](@ref) of the above
