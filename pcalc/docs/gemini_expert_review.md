---
title: "<strong>`presence-calculus/samplepath` </strong>"
subtitle: "Deep Research Review"
author: |
  Google Gemini
number-sections: true
figures-numbered: true
link-citations: true
toc-title: "Contents"
toc-depth: 2
figPrefix: "Figure"
---
# Executive Summary

This report provides an expert technical review of the Presence Calculus (PC)
framework, as implemented by the presence-calculus/samplepath GitHub project.
The review focuses on the underlying mathematical principles, the technical
relevance to established Operations Research (OR) methodologies, and the novelty
of its application in Operations Management (OM).

**Key Findings:** The Presence Calculus establishes a novel, constructive
analytical framework for measuring system performance by rigorously quantifying
observed behavior (sample paths) using measure theory.1 This approach offers
significant technical advantages over traditional stochastic modeling and
simulation by providing deterministic, non-stationary measurements of
time-dependent system state.

**Technical Relevance:** High. PC directly addresses core OM concerns—queueing,
capacity planning, and inventory control—by analytically defining crucial
performance metrics, such as Little's Law components ($L$, $\lambda$, $W$),
without requiring the restrictive assumptions of stationarity or ergodicity.2

**Novelty Assessment:** High. PC is distinguished by its fundamental reliance on
integral calculus over observed signal histories (presences) rather than
probability distributions, statistical simulation, or differential
optimization.1 This measure-theoretic foundation 1 positions it as a
foundational technology for dynamic, data-driven Operations Research.

**Strategic Recommendation:** Adoption is recommended, conditional on the
validation of computational scalability. The framework provides a crucial
analytical substrate for next-generation dynamic control systems, offering a
verifiable, mathematically precise measure of operational efficiency and
effectiveness.4

---

# Foundational Architecture of Presence Calculus (PC)

The Presence Calculus is presented as a novel, constructive approach designed
for modeling and measuring observed behavior in complex dynamic systems, ranging
from simple, linear structures to non-linear, stochastic, and adaptive
architectures.1 Its technical power stems directly from its mathematical
foundation, which departs significantly from typical OR methodologies.

## The Mathematical Substrate: Measure Theory and Real Analysis as PC’s Core

The Presence Calculus is built upon measure theory, a specialized branch of real
analysis.1 This choice of mathematical foundation is critical, as it dictates
the rigor and general applicability of the entire framework. Calculus, in its
traditional sense, is the study of continuous change, encompassing differential
calculus (rates of change) and integral calculus (accumulation of quantities).5
By choosing measure theory as its base, PC aims for a level of mathematical
precision and generality that is often compromised in applied OR modeling.

In contrast to most traditional stochastic modeling, which relies heavily on
probability theory and statistical approximations (e.g., stochastic processes
defined by families of random variables 6), PC is designed to be inherently
robust to complexity and volatility. This signals an intention to develop an
analytical tool capable of precisely modeling the *observed reality* of system
behavior, rather than idealized theoretical distributions or simplified
statistical approximations inherent in pure simulation.7 The framework is
therefore positioned as an analytical solution that remains mathematically
precise even when systems exhibit non-linear or highly stochastic behavior.1

## Defining the Presence Primitive: The 5-Tuple of Observation

The fundamental primitive unit in PC is the *presence*, formally defined as a
5-tuple $p = (e, b, t_0, t_1, m)$ .1 This structure formalizes the 
measurement
of dynamic system behavior. The elements typically represent the entity ($e$),
the boundary or scope ($b$), the start time ($t_0$), the end time ($t_1$), and
the total accumulated mass ($m$).1

This formal structure ensures that the core data unit required for dynamic
Operations Management analysis—associating the magnitude of a phenomenon with
the precise time interval of its existence—is consistently captured. The system
behavior observed over time is encapsulated in an underlying signal, which PC
terms the *presence density function*, denoted $f(e, b, t)$.1

## Signal Representation and Presence Mass: An Integrated View of System Behavior

Presence mass ($m$) is the quantitative manifestation of a presence.1 It is
explicitly a composite measure that quantifies a real-valued quantity and the
duration of time over which that quantity was maintained. Conceptually, it
measures an area in a two-dimensional space where time is one dimension and the
real-valued quantity is the other.1

Mathematically, presence mass is computed by integrating the presence density
function over the observed time interval $[t_0, t_1)$:

$$mass(e, b, [t_0, t_1]) = \int_{t_0}^{t_1} f(e, b, t) dt$$

The integral of the function over the interval is equivalent to the area under
the signal over that interval.1 While binary presences (where the quantity is
strictly 0 or 1, often used to model status) are intuitive, the analytical power
of PC is fully realized when generalizing to density functions with arbitrary
mass.1  
The significance of defining mass via integration is profound for Operations
Management. In OM, cost accumulation is frequently proportional to the integral
of a state variable over time. For instance, inventory holding cost is directly
proportional to the time-integral of the inventory level 8, and waiting cost in
a queue is proportional to the integral of the queue length. PC
institutionalizes this integral calculation as the fundamental state metric.
This inherent integration capability transforms PC into a direct, mathematically
optimized language for modeling utilization, throughput, and accumulated
financial consequences over time, potentially simplifying complex algebraic
derivations often required in classical optimization modeling.3

## Modeling Epistemic Uncertainty

A notable feature of the calculus is its ability to handle reasoning about
signal dynamics under *epistemic uncertainty*.1 This is uncertainty arising from
incomplete knowledge, as opposed to aleatoric uncertainty (inherent randomness)
addressed by traditional stochastic processes.6 PC formally permits constructs
such as "eternal presences," where both the start and end times are unknown.1

Furthermore, PC assertions about a signal do not require the assertion time to
align with the presence interval; assertions can reference the past, reflect the
present, or anticipate future signal behavior.1 This capability allows for the
formal inclusion of hypotheses, forecasts, or incomplete data streams directly
into the analytical calculation of system state (mass). For Operations Managers
grappling with volatile supply chains or systems with significant forecast
reliance, PC provides a framework for robust scenario testing and dynamic
planning, integrating hypotheses directly into the analytical calculation where
data is insufficient or only partially known.

---

# Technical Relevance: Bridging PC to Operations Research Fundamentals

Operations Management (OM) is fundamentally concerned with optimizing the design
and control of systems that convert inputs into outputs, focusing on decisions
related to operations strategy, quality, capacity, production planning, and
inventory control.9 Operations Research (OR) provides the mathematical models to
enhance this decision-making process.10 PC demonstrates technical relevance by
providing a powerful, analytical substrate for measuring and analyzing the
time-varying performance measures crucial to OR objectives.4

## Analytical Modeling of Accumulated System State

Classical mathematical approaches in OM use calculus for optimization tasks,
such as determining optimal staffing levels, inventory quantities (Economic
Order Quantity models 8), and production rates by setting derivatives to zero to
find optimal profit points.3 PC complements this by offering a superior
framework for modeling and measuring the system history and dynamic trajectories
necessary to feed into these optimization routines.1

By providing a constructive framework for modeling signal histories and
representing system trajectories in a parameter space 1, PC provides the
underlying data model for analyzing system dynamics. This distinguishes it from
descriptive, statistical methods that focus primarily on high-level
distributions rather than detailed observational history. The fact that the
calculus is constructive, meaning everything has a computational aspect 1,
confirms its direct applicability to real-world performance auditing.

## Case Study: Little's Law Reinterpreted through the Presence Calculus Lens

One of the most critical applications of PC in Operations Management is its
rigorous handling of queueing systems, particularly Little's Law ($L = \lambda
W$).12 Little's Law relates the long-term average number of items present in a
system ($L$), the long-term average arrival rate ($\lambda$), and the average
time an item spends in the system ($W$).12

PC provides a clear analytical interpretation of these terms 2:

* $L$ is defined as a *time average*—the average number of items present over a
  continuous time interval.
* $W$ is an *item average*—the average time accumulated by an item while present
  in the system.
* The time average of the number of items in the system, $L(T)$, is analytically
  defined by the area under the sample path of the number of items in the
  system, $N(t)$, divided by the observation time $T$.2 That is:

  $$L(T) = \frac{A(T)}{T}, \text{ where } A(T) = \int_0^T N(t) dt$$

This formulation highlights a profound technical advantage. Little's original
proof relies on strong assumptions: that the system is strictly stationary (
joint distributions are invariant under time shift) and metrically transitive (
ergodic).2 Real-world operational environments—such as contact centers, flexible
manufacturing, or dynamic delivery systems—are often highly transient and
non-stationary. PC’s mechanism, implemented in the samplepath project, defines
$L$ constructively via the exact integral over the observed time $T$.2 This
means that the framework can calculate the precise, time-averaged queue size or
utilization for *any specific, finite observation period*, irrespective of
whether the system has reached a statistical steady state.

This capability is essential for modern operations analysis, where the system is
rarely stationary. The project name, samplepath, emphasizes this focus on
analyzing the physical realization of the process 13, allowing for verifiable
performance auditing and highly accurate measurement in dynamic environments,
which is crucial for modern practices like measuring software delivery
performance (e.g., DORA metrics).1 PC’s foundation ensures that it utilizes the
full, modern, and mathematically correct understanding of Little's Law, rather
than the simplified versions historically developed for manufacturing and
queueing systems that rely on 50-year-old ideas.1

---

# Assessment of Novelty: Comparative Analysis of Modeling Paradigms

The novelty of the Presence Calculus framework can be most clearly demonstrated
by contrasting its core tenets against established Operations Research modeling
methodologies. PC offers a distinct analytical perspective rooted in
deterministic measurement rather than probabilistic prediction or statistical
estimation.

## PC versus Classical Calculus and Optimization

Classical calculus is primarily utilized in OM to determine optimal fixed points
by using derivatives to maximize or minimize objective functions under
constraints.3 Operational calculus, also known as operational analysis, is a
technique used to transform differential equations into simpler algebraic
problems.14

PC is distinct because its fundamental purpose is not static optimization but
dynamic **measurement and state representation**.1 The system state is
formalized as presence mass ($m$) via integration over time.1 While optimization
techniques use derivatives to find the rate of change and equilibrium, PC uses
integrals to find the exact accumulation of value or cost over observed time. PC
provides the analytically rigorous, high-fidelity inputs (e.g., exactly measured
non-stationary system averages) necessary for subsequent optimization routines,
confirming its novelty as a prerequisite modeling substrate.

## PC versus Stochastic Processes and Itô Calculus

Stochastic processes, such as the Wiener process or Markov chains 6, model
systems where variables change in a random manner. Itô calculus extends
classical calculus to handle integration with respect to stochastic processes
that are not differentiable (like Brownian motion).16

PC’s objective diverges from these approaches. Itô calculus focuses on the
theoretical dynamics of inherent, continuous randomness. Conversely, PC is
concerned with providing a rigorous, measurable integral (mass) over an
*observed realization* or sample path.1 PC focuses on the analytical
quantification of empirical phenomena using a measure-theoretic framework 1,
allowing it to handle complex, observed non-linear paths robustly, without
needing the specialized algebraic transformations (like the Itô integral)
designed for modeling probability distributions.

## PC versus Simulation Methodologies: Discrete Event Simulation (DES)

Discrete Event Simulation (DES) models system operation as a discrete sequence
of events, where time jumps to the next event occurrence (next-event time
progression).17 DES output relies on statistical methods, requiring multiple
independent replications and deletion of initial transient periods to reduce
variance and estimate steady-state performance measures with statistical
confidence intervals.7

PC, however, is an analytical, constructive methodology based on integral
calculus.1 This approach is fundamentally distinct from the descriptive,
statistical nature of DES.

**The Determinism Advantage:** Because PC calculates the exact integral of the
observed sample path $N(t)$ to derive the time-average $L$ 2, it produces a *
*deterministic, mathematically certain value** for performance over the observed
finite time window $T$. This capability fundamentally contrasts with DES
results, which are probabilistic estimates that inherently contain statistical
uncertainty. The absence of statistical noise translates into significantly
higher confidence in the performance data generated by PC, making the feedback
loops necessary for dynamic operational management more responsive and reliable.

The following table summarizes the key distinctions between the Presence
Calculus and established modeling techniques:

Table 1: Comparative Analysis of System Modeling Methodologies

| Feature                       | Presence Calculus                                                | Discrete Event Simulation (DES)                       | Classical Stochastic Modeling                                     | Classical OM Calculus                  |
|:------------------------------|:-----------------------------------------------------------------|:------------------------------------------------------|:------------------------------------------------------------------|:---------------------------------------|
| **Mathematical Basis**        | Measure Theory / Real Analysis 1                                 | Event Logic / Statistical Inference                   | Probability Theory / Stochastic Processes 6                       | Differential Calculus (Optimization) 3 |
| **Primary Goal**              | Analytical Measurement of Accumulated State (Mass)               | Statistical Estimation of System Dynamics             | Defining Probability and Expected Values                          | Finding Optimal Fixed Points (Max/Min) |
| **Handling Time**             | Continuous integration of density function 1                     | Discrete time jumps (Next-Event Progression) 17       | Continuous or discrete index sets 18                              | Static (Steady-State/Equilibrium)      |
| **Handling Non-Stationarity** | Robust; calculates exact time average for finite intervals $T$ 2 | Requires extensive replication and deletion periods 7 | Typically requires strong assumptions (stationarity/ergodicity) 2 | Not applicable to dynamic systems      |
| **Result Type**               | Deterministic Measure (Mass, $L$)                                | Probabilistic/Statistical Estimate                    | Theoretical Distribution                                          | Fixed Solution Value                   |

## PC and Sample-Path Optimization (SPO)

Sample-path optimization is a methodology used for optimizing limit functions in
stochastic modeling, particularly relevant to steady-state functions in
discrete-event dynamic systems.13 The samplepath implementation of Presence
Calculus provides a mechanism that rigorously quantifies the system's
performance based on its realization (the sample path).

In the context of SPO, PC acts as the analytical engine that supplies robust,
non-stationary performance metrics (like the integrated area $L$). By converting
raw observational data into a rigorous analytical quantity (mass), PC ensures
that the subsequent optimization step is applied to a stable and accurate
representation of the system’s behavior, making the overall SPO methodology more
robust than traditional methods that rely on stochastic approximation of the
objective function.

---

# Technical Review of the samplepath Project and Computational Feasibility

The technical viability of the Presence Calculus for industrial Operations
Management hinges on its computational tractability. Given that PC is defined as
a *constructive* calculus, its concepts must translate into performant
computations.1 The samplepath project is the practical implementation required
to perform these measure-theoretic integrals 1 efficiently on observed data.

## Implementation Strategy: Translating Theory to Computation

The primary engineering challenge is to convert the conceptually continuous
definition of presence mass—an integral over time—into a computationally
efficient algorithm that can process potentially vast streams of time-series
data. This involves systematic, step-by-step computations.1

To manage the complexity and volume of data, PC requires a specialized data
structure designed for aggregating and querying system state across various time
scales and windows.

## Computational Efficiency: The Presence Accumulation Matrix (PAM)

The foundational element for efficient computation within the Presence Calculus
is the **Presence Accumulation Matrix (PAM)**.1 This matrix is specifically
designed to compress information regarding the interaction between the
micro-level and macro-level behavior of a system of presences across different
time scales and observation windows.1

The significance of the PAM lies in its necessity to facilitate rapid, ad-hoc
querying of system state. For instance, an operations manager must be able to
ask: "What was the total resource utilization (presence mass) for machine 3
during the second quarter, filtered only for products A and B?" The PAM must
support this calculation of mass efficiently.

## Algorithmic Tractability and the Risk of Complexity Explosion

The efficiency of the samplepath project and the PAM is the critical technical
risk for widespread adoption. The challenge involves maintaining continuous
integral sums over dynamic, potentially infinite data streams without incurring
exponential growth in computational resources.

This concern is grounded in the experience of similar algebraic theories applied
to system analysis. For example, Network Calculus (NC), an algebraic theory used
for establishing time bounds in communication networks, is known to face
significant algorithmic tractability issues.19 In NC, algebraic expressions,
though compact, often result in unfeasibly large data structures during
computation due to operations like min-plus convolution, rendering analysis
intractable even for systems with a small number of steps.19

The success of the samplepath implementation relies entirely on solving this
complexity problem. The calculation of presence mass, which is a continuous
accumulation metric, must be achieved with efficient, potentially specialized
computational and algebraic techniques that mitigate the space explosion risk.19

For PC to be a viable enterprise OM solution, the performance of the PAM must
demonstrably ensure that the computational overhead of deriving the
deterministic, high-fidelity metrics (calculating mass) is significantly lower
than the statistical overhead (i.e., the extensive replication runs, transient
period deletion, and variance reduction techniques) required to achieve
comparable certainty and accuracy within a traditional Discrete Event Simulation
model.7

---

# Strategic Implications and Advanced Applications in Operations Management

The analytical capabilities of the Presence Calculus translate directly into
actionable improvements across core Operations Management domains.

##  Dynamic Capacity Planning and Queueing Systems

PC’s capacity to measure the exact time-average number of items in the system (
$L$) under non-stationary conditions 2 enables dynamic capacity decisions that
are impossible to derive accurately using steady-state models.

Traditional OM queueing models often assume stable arrival and service rates to
estimate average performance. PC allows operations managers to calculate the
exact time-weighted utilization (a direct application of presence mass) for
highly variable time slices, such as every five-minute interval during peak
hours, enabling real-time adjustments to labor scheduling or machine
provisioning. This moves capacity planning from a generalized, long-term
strategic decision to a granular, tactical control mechanism.

## Inventory Control Modeling

Inventory management involves minimizing holding costs and ordering costs, often
modeled using calculus-based optimization (e.g., EOQ).8 In PC, inventory holding
cost is directly modeled as the presence mass of the inventory level over time.1

This framework offers two significant advancements for inventory control:

1. **Modeling Non-Linear Holding Costs:** If holding costs are dynamic (e.g.,
   due to product degradation, rapid obsolescence, or time-sensitive capital
   constraints), the presence density function $f(e, b, t)$ can be adjusted
   non-linearly. PC then calculates the precise, integral-based total cost (
   mass), providing a cost model that is far more accurate than simplified
   linear models.
2. **Uncertainty in Transit:** By leveraging PC’s ability to model unknown
   temporal boundaries 1, managers can formally include components that are in
   transit (pipeline inventory) with defined probabilistic arrival windows. This
   integrates uncertainty directly into the calculation of total system
   inventory presence, improving inventory visibility and planning accuracy.

## Real-Time Scheduling and Resource Allocation in Complex Systems

Scheduling theory relies on evaluating system feasibility and assigning
priorities to tasks to meet deadlines.20 PC can provide constructive, continuous
metrics for managing complex resource usage and dependencies, much like how
Network Calculus is employed to establish time bounds in communication
systems.19

In environments like flexible manufacturing or multi-project management,
resource availability and consumption are critical constraints.20 PC allows
managers to track the presence mass of a resource consumed by various competing
tasks, providing an objective, analytical measure of accumulated delay and
actual utilization. This capability has the potential to unify algebraic
modeling approaches like Max-Plus Algebra, which is used for dealing with
certain discrete event systems, with traditional real-time scheduling theory,
facilitating optimal priority assignment even for general task models.20

## Modeling Epistemic Uncertainty for Robust Forecasting in Supply Chains

The ability of PC to reason about signal dynamics under epistemic uncertainty
and to allow assertions to anticipate future behavior 1 is highly valuable for
robust planning.

When managing long-lead-time supply chains, managers rely heavily on forecasts
and constrained assertions about future events (e.g., "The factory capacity
signal will drop by 20% during the summer maintenance window," or "The order
fulfillment presence will occur between dates X and Y"). PC provides a rigorous,
mathematical framework to integrate these probabilistic or informational
assertions directly into the calculation of expected system presence mass. This
allows for the analytical definition of robust performance bounds, enabling
decision-makers to quantitatively assess the resilience of the system under
specified levels of informational uncertainty.

---

# Conclusion and Recommendations

## Synthesis of Technical Novelty and Operational Value

The presence-calculus/samplepath project introduces a highly novel and
technically relevant analytical framework for Operations Management. Its
foundation in measure theory provides the necessary mathematical rigor to model
systems ranging from simple to chaotically complex.1

The core operational value proposition lies in the shift from statistical
estimation to analytical determination of performance metrics. By calculating
time averages (like $L$ in Little's Law) through the exact integration of the
observed sample path 2, PC delivers deterministic, high-fidelity metrics that
are independent of the restrictive stationarity and ergodicity assumptions
governing classical OR models. This capability is paramount for auditing and
controlling highly dynamic, non-stationary operations common in modern industry.
This inherent determinism offers a substantial competitive advantage over
statistical simulation methods, which require extensive effort to reduce
variance and establish statistical confidence.7

## Strategic Roadmap for Integration and Research

The analysis yields three core recommendations for organizations considering the
adoption or further study of the Presence Calculus and the samplepath
implementation:

**Recommendation 1**: Validate Computational Scalability (High Priority)  
The viability of PC in enterprise-level Operations Management is critically
dependent on the computational efficiency of the Presence Accumulation Matrix (
PAM).1 Given the documented complexity challenges in related algebraic modeling
fields, such as Network Calculus 19, immediate and extensive benchmarking of the
samplepath implementation is required. Validation must confirm that the
computational overhead of PAM for calculating accumulated mass and supporting
queries is scalable to high-volume operational data streams without an
exponential increase in time or space complexity.  

**Recommendation 2**: Initiate Pilot Program in Transient Analysis.  
The most distinct advantage of PC is its ability to measure non-stationary
system behavior accurately. A pilot program should be implemented targeting
operational areas dominated by transients, such as system ramp-up and ramp-down
phases, shift changes, or extreme demand spikes. The program should use PC to
calculate precise time-average metrics ($L$ and utilization) during these
transient periods, comparing the deterministic results directly against
performance derived from both classical steady-state formulas and traditional
Discrete Event Simulation techniques. This will quantitatively validate PC's
unique high-fidelity measurement capabilities in real-world scenarios.  

**Recommendation 3**: Integrate with Prescriptive Optimization Layers.  
PC should be treated as the foundation for future prescriptive analytics.
Research and development efforts should focus on integrating PC’s rigorous
analytical outputs—specifically the non-stationary presence mass and the formal
representation of epistemic uncertainty 1—into advanced Sample-Path Optimization
algorithms.13 This integration will facilitate the creation of next-generation
control systems capable of optimized, dynamic resource allocation and capacity
management in highly complex and volatile operational landscapes.

# References

1. The Presence Calculus, accessed November 27,
   2025, [https://docs.pcalc.org/pandoc/intro_to_presence_calculus.html](https://docs.pcalc.org/pandoc/intro_to_presence_calculus.html)
2. A Deep Dive into Little's Law - The Presence Calculus, accessed November 27,
   2025, [https://docs.pcalc.org/pandoc/littles_law_history.html](https://docs.pcalc.org/pandoc/littles_law_history.html)
3. How Business Calculus Drives Success: Applications in Economics and
   Management, accessed November 27,
   2025, [https://blog.fastlearner.ai/how-business-calculus-drives-success/](https://blog.fastlearner.ai/how-business-calculus-drives-success/)
4. 1.3 steps in an operations research study - MIT, accessed November 27,
   2025, [https://web.mit.edu/urban_or_book/www/book/chapter1/1.3.html](https://web.mit.edu/urban_or_book/www/book/chapter1/1.3.html)
5. Calculus - Wikipedia, accessed November 27,
   2025, [https://en.wikipedia.org/wiki/Calculus](https://en.wikipedia.org/wiki/Calculus)
6. Stochastic process - Wikipedia, accessed November 27,
   2025, [https://en.wikipedia.org/wiki/Stochastic_process](https://en.wikipedia.org/wiki/Stochastic_process)
7. Discrete event simulation | Applications of Scientific Computing Class
   Notes - Fiveable, accessed November 27,
   2025, [https://fiveable.me/applications-of-scientific-computing/unit-3/discrete-event-simulation/study-guide/bcJgzbxwWopLQ6My](https://fiveable.me/applications-of-scientific-computing/unit-3/discrete-event-simulation/study-guide/bcJgzbxwWopLQ6My)
8. Inventory Control Models, accessed November 27,
   2025, [http://faculty.fortlewis.edu/huggins_e/inventory.pdf](http://faculty.fortlewis.edu/huggins_e/inventory.pdf)
9. Operations management - Wikipedia, accessed November 27,
   2025, [https://en.wikipedia.org/wiki/Operations_management](https://en.wikipedia.org/wiki/Operations_management)
10. Abstract Operations Research Modeling Using Natural Language Inputs - MDPI,
    accessed November 27,
    2025, [https://www.mdpi.com/2078-2489/16/2/128](https://www.mdpi.com/2078-2489/16/2/128)
11. Inventory Control Models, accessed November 27,
    2025, [https://hithaldia.in/faculty/sas_faculty/Dr_D_K_Jana/Class%20Note-MM_401-MODEL-4-Inventory%20Control%20Models.pdf](https://hithaldia.in/faculty/sas_faculty/Dr_D_K_Jana/Class%20Note-MM_401-MODEL-4-Inventory%20Control%20Models.pdf)
12. Little's law - Wikipedia, accessed November 27,
    2025, [https://en.wikipedia.org/wiki/Little%27s_law](https://en.wikipedia.org/wiki/Little%27s_law)
13. Analysis of Sample-Path Optimization | Mathematics of Operations Research -
    PubsOnLine, accessed November 27,
    2025, [https://pubsonline.informs.org/doi/10.1287/moor.21.3.513](https://pubsonline.informs.org/doi/10.1287/moor.21.3.513)
14. Operational calculus - Wikipedia, accessed November 27,
    2025, [https://en.wikipedia.org/wiki/Operational_calculus](https://en.wikipedia.org/wiki/Operational_calculus)
15. Chang-notes.pdf - Yale Statistics and Data Science, accessed November 27,
    2025, [http://www.stat.yale.edu/~pollard/Courses/251.spring09/Handouts/Chang-notes.pdf](http://www.stat.yale.edu/~pollard/Courses/251.spring09/Handouts/Chang-notes.pdf)
16. Itô calculus - Wikipedia, accessed November 27,
    2025, [https://en.wikipedia.org/wiki/It%C3%B4_calculus](https://en.wikipedia.org/wiki/It%C3%B4_calculus)
17. Discrete-event simulation - Wikipedia, accessed November 27,
    2025, [https://en.wikipedia.org/wiki/Discrete-event_simulation](https://en.wikipedia.org/wiki/Discrete-event_simulation)
18. Markov process vs. markov chain vs. random process vs. stochastic process
    vs. collection of random variables - Math Stack Exchange, accessed November
    27,
    2025, [https://math.stackexchange.com/questions/266183/markov-process-vs-markov-chain-vs-random-process-vs-stochastic-process-vs-co](https://math.stackexchange.com/questions/266183/markov-process-vs-markov-chain-vs-random-process-vs-stochastic-process-vs-co)
19. Computationally efficient worst-case analysis of flow-controlled networks
    with Network Calculus - IEEE Xplore, accessed November 27,
    2025, [https://ieeexplore.ieee.org/iel7/18/4667673/10042451.pdf](https://ieeexplore.ieee.org/iel7/18/4667673/10042451.pdf)
20. REAL-TIME CALCULUS FOR SCHEDULING HARD REAL-TIME SYSTEMS Lothar Thiele,
    Samarjit Chakraborty and Martin Naedele Swiss Federal In - Computer
    Engineering and Networks Laboratory, accessed November 27,
    2025, [https://tik-old.ee.ethz.ch/file/994e3fb9a12a2471eb73d0d30a4317d3/scheduling.pdf](https://tik-old.ee.ethz.ch/file/994e3fb9a12a2471eb73d0d30a4317d3/scheduling.pdf)