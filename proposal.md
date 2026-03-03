Based on the research gaps we identified and the search results that provide additional validation for your research direction , here is a comprehensive research proposal template developed specifically for your topic.

---

# RESEARCH PROPOSAL TEMPLATE

## Limitations of Classical Queuing Models in Modern Campus Networks: An Empirical Evaluation and Hybrid Simulation Framework

---

## SECTION 1: TITLE AND IDENTIFICATION

### Proposed Title
**"Limitations of Classical Queuing Models in Modern Campus Networks: An Empirical Evaluation and Hybrid Simulation Framework"**

### Alternative Title Options
- "Beyond M/M/1: Quantifying the Discrepancy of Classical Queuing Theory in Heterogeneous Campus Network Environments"
- "TCP-Aware Performance Modeling for Campus Networks: A Hybrid Approach to Overcome Classical Queuing Limitations"

### Researcher Information
| Field | Details |
| :--- | :--- |
| **Name** | Raphael Ayeh Mensah |
| **Department** | Computer Science |
| **Program** | B.Sc |
| **Supervisor** | Julius Y. Ludu |
| **Date** | [Submission Date] |
| **Research Duration** | [e.g., 12-24 months] |

---

## SECTION 2: ABSTRACT

This research investigates the fundamental limitations of classical queuing models—particularly M/M/1 and its variants—when applied to performance prediction in modern campus networks. While classical queuing theory remains the simplest and most accessible tool for network modeling , recent empirical evidence suggests these models fail to accurately capture critical dynamics introduced by TCP congestion control and wireless link fluctuations . This study pursues three primary objectives: (1) empirically quantify the discrepancy between classical model predictions and actual performance metrics in live campus network environments, (2) identify specific traffic characteristics (self-similarity, burstiness, TCP feedback loops) that contribute most significantly to modeling errors, and (3) develop and validate a hybrid simulation-analytical framework that overcomes these limitations while maintaining practical usability for network administrators. The research will employ trace-driven simulation using real campus traffic captures, comparative analysis of queuing disciplines, and controlled experimentation in isolated testbed environments. Expected contributions include a validated error taxonomy for classical models, an open-source hybrid modeling toolkit, and practical guidelines for model selection based on network-specific traffic characteristics.

**Keywords:** Queuing Theory, Campus Networks, TCP Congestion Control, Network Performance Modeling, Self-Similar Traffic, Discrete-Event Simulation, Hybrid Systems

---

## SECTION 3: INTRODUCTION AND BACKGROUND

### 3.1 Research Context

Data communication networks rank among the most complex engineered systems, with campus networks presenting particular challenges due to their heterogeneous traffic patterns, mixed wired/wireless infrastructure, and diverse user communities . Network designers and administrators have long relied on queuing theory as a foundational tool for capacity planning, performance prediction, and congestion management. Classical models—M/M/1, M/G/1, and their network extensions—offer mathematical tractability and intuitive insights that make them attractive for practical deployment.

However, a fundamental tension exists between the analytical convenience of these models and their fidelity to real-world network behavior. As early as 2005, researchers at Rutgers University identified the need to "quantify the error of simple queuing models when traffic follows self-similar behavior" . This concern has only intensified with the evolution of campus networks toward increasingly complex architectures.

### 3.2 Problem Statement

Classical queuing models rest on assumptions that are increasingly violated in modern campus networks:

1. **Poisson arrival processes** assume memoryless, exponentially distributed inter-arrival times, yet empirical studies demonstrate that campus network traffic exhibits self-similarity, long-range dependence, and heavy-tailed distributions .

2. **Exponential service time distributions** fail to capture the variable packet sizes and processing requirements characteristic of contemporary applications.

3. **TCP congestion control mechanisms** create feedback loops between network conditions and traffic generation that classical models cannot represent. Research confirms that "analytical queuing models studied did not provide good approximations, mostly by not reflecting the control exercised by the Transmission Control Protocol (TCP)" .

4. **Wireless link dynamics** introduce rate mismatches and fluctuation patterns absent from wired-network-focused classical theory.

The consequence is a critical gap: network administrators must choose between analytically tractable but potentially inaccurate models and highly accurate but computationally expensive packet-level simulations. This research addresses the need for a middle ground—a hybrid approach that balances accuracy and practicality.

### 3.3 Research Questions

This study is guided by the following primary research questions:

**RQ1:** To what extent do classical queuing models (M/M/1, M/G/1, M/M/c) deviate from observed performance metrics in modern campus network environments, and how does this discrepancy vary with traffic self-similarity and burstiness?

**RQ2:** Which specific network dynamics—TCP congestion control, wireless link fluctuations, or application-layer patterns—contribute most significantly to the predictive errors of classical models?

**RQ3:** Can a hybrid simulation-analytical framework, incorporating TCP-aware dynamics and short-timescale averaging, provide more accurate performance predictions while maintaining computational tractability for practical use?

**RQ4:** How do different queuing disciplines (FIFO, Priority Queuing, Weighted Fair Queuing, Modified Deficit Round Robin) interact with real traffic patterns, and can their performance be better predicted through enhanced modeling approaches?

### 3.4 Research Objectives

| Objective | Description | Success Criterion |
| :--- | :--- | :--- |
| **O1** | Characterize campus network traffic through extensive packet captures, quantifying self-similarity parameters (Hurst exponent), burstiness, and protocol distributions | Complete traffic repository with statistical characterization |
| **O2** | Quantify prediction errors of classical models across multiple performance metrics (queue length, waiting time, packet loss, delay variation) | Error bounds established as functions of traffic characteristics |
| **O3** | Identify specific mechanisms (TCP window dynamics, wireless rate adaptation) that classical models fail to capture | Causal analysis linking model assumptions to observed discrepancies |
| **O4** | Develop hybrid modeling framework combining analytical tractability with simulation-based TCP/wireless dynamics | Framework implementation with documented API |
| **O5** | Validate framework against real campus traffic and compare with both classical models and full packet-level simulation | Accuracy improvement metrics and computational cost analysis |

---

## SECTION 4: LITERATURE REVIEW

### 4.1 Classical Queuing Theory in Network Performance Modeling

The application of queuing theory to communication networks dates to the foundational work of Kleinrock and others in the 1960s and 1970s. The M/M/1 queue remains the most widely taught and applied model due to its closed-form solutions for key performance metrics:

- Average queue length: $L = \frac{\rho}{1-\rho}$ where $\rho = \lambda/\mu$
- Average waiting time: $W = \frac{1/\mu}{1-\rho}$
- Probability of n customers: $P_n = (1-\rho)\rho^n$

These models offer the advantage of simplicity and intuitive parameter interpretation. Network designers can estimate utilization, predict congestion points, and plan capacity using minimal input data. However, the assumptions underlying these formulas—memoryless arrivals, exponential service times, infinite buffers, steady-state operation—are rarely satisfied in practice .

### 4.2 Empirical Evidence of Model Limitations

The research gap identified in this proposal is not new but remains unresolved. A 2005 graduate course at Rutgers University explicitly proposed a project to "quantify the error of simple queuing models when traffic follows self-similar behavior," suggesting that students would "quantify the discrepancy of a variety of properties obtainable from classic queuing theory such as the average time spent in a queue, average queue length, and drop probabilities, as a function of the self-similarity of the traffic" . This acknowledgment from nearly two decades ago indicates persistent challenges.

Subsequent research has reinforced these concerns. Studies of campus networks reveal that traffic exhibits:
- **Self-similarity** with Hurst parameters H > 0.5, indicating long-range dependence
- **Heavy-tailed distributions** for file sizes and connection durations
- **Burstiness** across multiple time scales
- **Protocol-specific patterns** with TCP dominating traffic volume

### 4.3 TCP-Aware Modeling Approaches

A significant advancement in understanding model limitations comes from hybrid systems research. As documented in a Master's thesis from Eindhoven University of Technology, "aggregate fluid-like models... mostly capture steady-state behavior because the averaging is typically done over large time scales. For instance, detailed transient behavior during congestion control cannot be captured" . This work proposed hybrid systems that "combine both continuous-time dynamics and discrete-time logic," averaging discrete variables over time scales on the order of a round-trip time to capture transient phenomena .

This approach addresses a critical gap: TCP's congestion control algorithm creates feedback loops where packet loss triggers window reductions, which in turn reduce offered load, affecting queue dynamics. Classical models treat arrivals as exogenous processes, ignoring this coupling.

### 4.4 Priority-Based Queuing and Quality of Service

Modern campus networks increasingly implement Quality of Service (QoS) mechanisms to differentiate traffic classes. Priority Queuing, Weighted Fair Queuing, and algorithms like Modified Deficit Round Robin (MDRR) allocate bandwidth based on packet classifications . Research has explored Model Predictive Control approaches to dynamically tune these algorithms, comparing "controlled and uncontrolled MDRR algorithm" implementations .

These developments introduce additional complexity for performance modeling. Classical queuing networks with multiple customer classes (BCMP networks) become computationally intractable with more than 3-4 classes, yet campus networks may require finer-grained differentiation for applications ranging from video conferencing to research data transfers.

### 4.5 Campus Network-Specific Research

The academic environment presents unique characteristics that influence network performance. Research on "performance modeling and knowledge processing in high-speed interconnected intelligent educational networks" has proposed methodologies for "understanding network traffic behavior through the combination of quality of service, degradation policies, and a queue scheme" . This work recognizes that educational networks serve dual purposes: supporting administrative operations and enabling knowledge dissemination, with traffic patterns reflecting academic calendars, class schedules, and research activities.

Contemporary research at Boston University demonstrates the continued relevance of queuing approaches for campus infrastructure. A 2025 project on "Optimizing Electric Vehicle Charging Infrastructure on University Campuses: A Queueing-Theoretic Analysis of Capacity and Congestion" applies similar methodologies to physical infrastructure, showing the broader applicability of these analytical tools .

### 4.6 Identified Research Gaps

| Gap Area | Current State | What Remains Unexplored |
| :--- | :--- | :--- |
| **TCP-Aware Modeling** | Hybrid systems proposed but limited validation with real campus traffic  | Empirical validation of hybrid models against live campus network measurements |
| **Wireless Integration** | Wired and wireless segments modeled separately | Integrated models accounting for rate mismatch and handover dynamics |
| **Multi-Class Scalability** | Exact solutions for 4+ classes computationally prohibitive | Practical approximation methods validated with campus traffic |
| **Self-Similarity Quantification** | Error identified but not systematically characterized  | Comprehensive error bounds as functions of self-similarity parameters |
| **Queuing Discipline Comparison** | Individual algorithms studied in isolation | Comparative analysis under realistic campus traffic mixes |

---

## SECTION 5: THEORETICAL FRAMEWORK

### 5.1 Foundational Concepts

This research builds upon several interconnected theoretical domains:

**Queuing Theory Fundamentals:** The analysis will employ classical models (M/M/1, M/G/1, M/M/c) as baselines, deriving their steady-state performance predictions using standard formulas.

**Self-Similar Traffic Theory:** Traffic characterization will utilize Hurst parameter estimation (rescaled range analysis, variance-time plots) to quantify long-range dependence. The relationship between self-similarity and queuing performance will be explored through established relationships between Hurst parameter and queue length distributions.

**TCP Congestion Control Dynamics:** The research will incorporate models of TCP Reno, Cubic, and BBR behaviors, focusing on how congestion window evolution interacts with queue dynamics during both steady-state and transient conditions.

**Hybrid Systems Theory:** Following the framework described in prior work, the proposed hybrid model will combine continuous dynamics (queue evolution, TCP window growth) with discrete events (packet drops, timeout events) using short-timescale averaging .

### 5.2 Conceptual Model

The proposed hybrid framework conceptualizes campus network performance through three interacting layers:

```
┌─────────────────────────────────────────────┐
│  Application Layer                          │
│  • Traffic generation patterns               │
│  • Protocol mix (HTTP, video, file transfer) │
│  • User behavior models                       │
└─────────────────┬───────────────────────────┘
                  │ Offered load
                  ▼
┌─────────────────────────────────────────────┐
│  Transport Layer (TCP/UDP)                   │
│  • Congestion window dynamics                 │
│  • Flow control                                │
│  • Retransmission mechanisms                   │
└─────────────────┬───────────────────────────┘
                  │ Shaped traffic
                  ▼
┌─────────────────────────────────────────────┐
│  Network Layer (Queuing System)              │
│  • Queue evolution (continuous)               │
│  • Packet drops (discrete events)              │
│  • Scheduling discipline                         │
│  • Link sharing                                  │
└─────────────────────────────────────────────┘
```

The key innovation is the feedback loop: queue dynamics influence packet drops, which trigger TCP reactions, which modify offered load. Classical models break this loop by treating arrivals as exogenous.

### 5.3 Mathematical Formulation

**Classical Model (Baseline):**
For an M/M/1 queue, the system is described by:
$$\frac{d}{dt}P_n(t) = \lambda P_{n-1}(t) + \mu P_{n+1}(t) - (\lambda + \mu)P_n(t)$$

**Hybrid Model Extension:**
The proposed hybrid model modifies the arrival process to reflect TCP dynamics:
$$\lambda(t) = \sum_{i=1}^{N} \frac{W_i(t)}{RTT_i}$$
where $W_i(t)$ represents the congestion window size of flow i, evolving according to:
$$\frac{dW_i}{dt} = \frac{1}{RTT_i} \text{ (during congestion avoidance)}$$
with discrete reductions upon packet drops:
$$W_i(t^+) = \frac{W_i(t)}{2} \text{ (on drop event)}$$

Queue evolution follows:
$$\frac{dQ}{dt} = \sum \lambda_i(t) - C \cdot 1_{\{Q>0\}}$$
with drop events triggered when Q exceeds buffer capacity.

---

## SECTION 6: RESEARCH METHODOLOGY

### 6.1 Research Design Overview

This study employs a mixed-methods approach combining empirical measurement, simulation experimentation, and analytical modeling. The design follows a sequential phases structure:

| Phase | Duration | Primary Activities | Outputs |
| :--- | :--- | :--- | :--- |
| **Phase 1** | 3-4 months | Traffic capture, characterization, classical model implementation | Traffic repository, baseline predictions |
| **Phase 2** | 3-4 months | Discrepancy quantification, causal analysis | Error characterization, gap taxonomy |
| **Phase 3** | 4-5 months | Hybrid framework development, implementation | Working hybrid simulator |
| **Phase 4** | 2-3 months | Validation, comparative analysis | Validation results, guidelines |
| **Phase 5** | 1-2 months | Thesis writing, dissemination | Final dissertation, publications |

### 6.2 Phase 1: Empirical Traffic Characterization

**Data Collection:**
- Deploy packet capture sensors at strategic campus network points (core router, distribution switches, wireless controllers, departmental edge)
- Capture duration: Minimum 4 weeks to capture weekly/daily patterns
- Capture periods: Include academic session and break periods for comparison
- Anonymization: Strip payload data, preserve packet headers and timing

**Traffic Analysis:**
- Protocol distribution analysis (TCP/UDP, application protocols)
- Flow characterization (arrival patterns, sizes, durations)
- Self-similarity estimation using multiple methods:
  - Rescaled Range (R/S) analysis
  - Variance-time plots
  - Periodogram-based estimation
- Burstiness characterization across time scales

**Classical Model Implementation:**
- Implement M/M/1, M/G/1, and M/M/c models
- Estimate parameters from traffic data (arrival rates, service times)
- Generate performance predictions for comparison points

### 6.3 Phase 2: Discrepancy Quantification

**Comparison Framework:**
Compare classical model predictions against observed metrics:

| Metric | Classical Prediction | Observed Value | Error Measure |
| :--- | :--- | :--- | :--- |
| Average queue length | $L_{M/M/1} = \rho/(1-\rho)$ | $\bar{L}_{obs}$ | Relative error, absolute error |
| Average waiting time | $W_{M/M/1} = 1/(\mu(1-\rho))$ | $\bar{W}_{obs}$ | Relative error, absolute error |
| Queue length distribution | $P_n = (1-\rho)\rho^n$ | Empirical CDF | KS statistic, KL divergence |
| Loss probability | $P_{loss} \approx 0$ (infinite buffer) | Actual loss rate | Absolute difference |

**Causal Analysis:**
- Segment traffic by protocol, time of day, and application type
- Identify conditions where errors are maximized
- Correlate errors with traffic characteristics (Hurst parameter, burstiness index, TCP ratio)
- Isolate specific mechanisms through controlled testbed experiments

### 6.4 Phase 3: Hybrid Framework Development

**Framework Architecture:**
```
┌─────────────────────────────────────────────────────┐
│                 Input Module                          │
│  • Traffic trace reader / Synthetic generator         │
│  • Network topology definition                         │
│  • Protocol parameter configuration                    │
└─────────────────────┬───────────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────────┐
│              Hybrid Simulation Engine                    │
├───────────────────┬───────────────────┬─────────────────┤
│ Continuous Solver │ Event Scheduler   │ State Manager   │
│ • Queue ODEs      │ • Drop events     │ • Flow states   │
│ • Window dynamics │ • Timeout events  │ • Queue states  │
│ • Rate equations  │ • RTO expirations │ • Link states   │
└───────────────────┴───────────────────┴─────────────────┘
                      │
┌─────────────────────▼───────────────────────────────────┐
│                 Output Module                            │
│  • Performance metrics collection                        │
│  • Trace generation                                      │
│  • Visualization                                         │
└─────────────────────────────────────────────────────────┘
```

**Key Innovations:**
1. **Short-timescale averaging:** Update continuous variables at RTT-scale intervals (10-100ms) rather than packet-scale (μs-ms)
2. **Hybrid state representation:** Queues modeled as continuous while drops remain discrete events
3. **TCP feedback incorporation:** Two-way coupling between queue state and source behavior
4. **Wireless link models:** Incorporate rate adaptation and fluctuation patterns

**Implementation Plan:**
- Develop core framework in Python/C++ for performance
- Implement pluggable queue disciplines (FIFO, PQ, WFQ, MDRR)
- Create visualization and analysis tools
- Document API for extensibility

### 6.5 Phase 4: Validation and Comparative Analysis

**Validation Approaches:**
1. **Trace-driven simulation:** Replay captured traffic through hybrid model, compare outputs with observations
2. **Testbed experiments:** Deploy controlled environment with traffic generators, compare model predictions with measurements
3. **Comparative benchmarking:** Compare hybrid model accuracy against classical models and full packet-level simulation (ns-3)

**Validation Metrics:**
- Prediction accuracy (RMSE, MAPE) for key performance indicators
- Computational cost (runtime, memory usage)
- Scalability with network size and traffic volume
- Sensitivity to parameter estimation errors

**Comparative Framework:**
| Model Type | Examples | Expected Accuracy | Expected Cost |
| :--- | :--- | :--- | :--- |
| Classical analytical | M/M/1, M/G/1 | Low-Medium | Very Low |
| Hybrid (proposed) | TCP-aware fluid model | Medium-High | Medium |
| Packet-level simulation | ns-3, OMNeT++ | High | Very High |

### 6.6 Phase 5: Synthesis and Dissemination

- Develop practical guidelines for model selection based on network characteristics
- Create decision framework for network administrators
- Prepare manuscripts for conference and journal submission
- Write comprehensive dissertation

---

## SECTION 7: EXPECTED CONTRIBUTIONS

### 7.1 Theoretical Contributions

1. **Empirical error taxonomy:** Systematic characterization of classical model limitations under real campus traffic conditions, extending the preliminary observations in prior work  with quantitative error bounds.

2. **TCP-aware modeling framework:** Advancement of hybrid systems theory applied to network performance modeling, building on the foundation of short-timescale averaging approaches .

3. **Self-similarity impact quantification:** Mathematical relationships between traffic self-similarity parameters and queuing model accuracy.

### 7.2 Practical Contributions

1. **Open-source hybrid modeling toolkit:** Freely available software implementing the proposed framework, enabling network administrators to obtain more accurate performance predictions without full packet-level simulation.

2. **Model selection guidelines:** Practical decision framework helping practitioners choose appropriate modeling approaches based on their specific network characteristics and prediction needs.

3. **Traffic characterization repository:** Anonymized campus traffic traces with statistical characterization, supporting future research.

### 7.3 Anticipated Publications

| Publication Type | Target Venue | Timeline | Contribution |
| :--- | :--- | :--- | :--- |
| Conference paper | IEEE/IFIP Networking or ACM SIGCOMM (poster) | Month 8-10 | Preliminary discrepancy results |
| Journal article | IEEE/ACM Transactions on Networking | Month 14-16 | Full error characterization |
| Conference paper | IEEE/IFIP Performance or ValueTools | Month 18-20 | Hybrid framework design |
| Journal article | Performance Evaluation or Computer Networks | Month 22-24 | Validation and guidelines |
| Dissertation | University repository | Month 24 | Complete research synthesis |

---

## SECTION 8: TIMELINE AND MILESTONES

### Gantt Chart Overview

| Activity | M1-2 | M3-4 | M5-6 | M7-8 | M9-10 | M11-12 | M13-14 | M15-16 | M17-18 | M19-20 | M21-22 | M23-24 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Phase 1** | ████ | ████ | | | | | | | | | | |
| Literature review | ██ | ██ | ██ | | | | | | | | | |
| Traffic capture setup | ██ | ██ | | | | | | | | | | |
| Data collection | | ██ | ██ | ██ | | | | | | | | |
| Traffic characterization | | | ██ | ██ | ██ | | | | | | | |
| **Phase 2** | | | | | | | | | | | | |
| Classical model implementation | | | | ██ | ██ | | | | | | | |
| Discrepancy analysis | | | | | ██ | ██ | ██ | | | | | |
| Causal investigation | | | | | | ██ | ██ | ██ | | | | |
| **Phase 3** | | | | | | | | | | | | |
| Framework design | | | | | | | ██ | ██ | | | | |
| Implementation | | | | | | | | ██ | ██ | ██ | | |
| Testing & refinement | | | | | | | | | ██ | ██ | ██ | |
| **Phase 4** | | | | | | | | | | | | |
| Validation experiments | | | | | | | | | | ██ | ██ | ██ |
| Comparative analysis | | | | | | | | | | | ██ | ██ |
| **Phase 5** | | | | | | | | | | | | |
| Paper writing | ██ | ██ | ██ | ██ | ██ | ██ | ██ | ██ | ██ | ██ | ██ | ██ |
| Thesis writing | | | | | | | | | | | ██ | ██ |
| Final submission | | | | | | | | | | | | ██ |

### Key Milestones

| Milestone | Due Date | Deliverable |
| :--- | :--- | :--- |
| Research proposal approval | Month 1 | Approved proposal |
| Traffic capture infrastructure | Month 2 | Working capture system, ethics approval |
| Preliminary traffic characterization | Month 5 | Technical report, initial statistics |
| Classical model implementation | Month 7 | Working baseline models |
| Discrepancy analysis complete | Month 11 | Conference paper submission |
| Hybrid framework design | Month 13 | Design document |
| Framework implementation | Month 18 | Working software, documentation |
| Validation complete | Month 22 | Validation report |
| Dissertation draft | Month 23 | Complete draft |
| Final submission | Month 24 | Approved dissertation |

---

## SECTION 9: RESOURCES AND BUDGET

### 9.1 Personnel Requirements

| Role | Responsibility | Time Commitment |
| :--- | :--- | :--- |
| Principal Researcher | Overall project execution, development, analysis | 100% (PhD candidate) |
| Supervisor | Guidance, methodology review, publication support | 2-4 hours/week |
| Network Administrator | Access facilitation, capture coordination | 2 hours/week (initial phase) |
| Technical Support | Server maintenance, software installation | As needed |

### 9.2 Hardware Resources

| Item | Specification | Purpose | Status |
| :--- | :--- | :--- | :--- |
| Capture server | High-performance workstation, 1TB+ storage | Packet capture storage | To acquire |
| Testbed nodes | 4-6 commodity PCs | Controlled experiments | Available |
| Network taps/SPAN ports | - | Capture access | University IT |
| Development machine | Modern laptop/desktop | Software development | Available |

### 9.3 Software Resources

| Software | Purpose | License |
| :--- | :--- | :--- |
| Wireshark/tcpdump | Packet capture | Open source |
| Python with scientific stack | Analysis, development | Open source |
| ns-3 | Packet-level simulation baseline | Open source |
| MATLAB/Octave (optional) | Mathematical analysis | Available/Open source |
| Git | Version control | Open source |

### 9.4 Budget Estimate

| Category | Item | Estimated Cost | Funding Source |
| :--- | :--- | :--- | :--- |
| Hardware | Capture server | $1,500 - $2,000 | Department/Research grant |
| Storage | External backup drives | $300 - $500 | Department |
| Conference travel | 1-2 international conferences | $2,500 - $4,000 | University/Grant |
| Publication fees | Open access journals | $1,000 - $2,500 | Research fund |
| Miscellaneous | Software licenses (if needed) | $0 - $500 | Contingency |
| **Total** | | **$5,300 - $9,500** | |

---

## SECTION 10: ETHICAL CONSIDERATIONS

### 10.1 Data Privacy and Anonymization

Network packet captures may contain sensitive information. The following safeguards will be implemented:

1. **Ethics approval:** Obtain university ethics committee approval before any data collection
2. **Informed consent:** If collecting from end-user traffic, implement opt-in/opt-out mechanisms
3. **Payload stripping:** Remove all packet payloads, retaining only headers for analysis
4. **IP anonymization:** Replace IP addresses with consistent but non-identifiable tokens (Crypto-PAn or similar)
5. **Timing preservation:** Maintain inter-arrival times for queuing analysis
6. **Data storage:** Encrypted storage with access limited to research team
7. **Retention policy:** Delete raw captures after analysis, retain only anonymized, aggregated statistics

### 10.2 Network Impact Considerations

1. **Passive monitoring only:** Use SPAN ports or network taps; no inline deployment
2. **Minimal overhead:** Ensure capture infrastructure does not affect production network performance
3. **Coordinated scheduling:** Schedule any active measurements during low-usage periods
4. **IT department coordination:** Maintain ongoing communication with university network team

### 10.3 Publication Ethics

1. **Anonymized results:** Ensure no identifying information appears in publications
2. **Reproducibility:** Release anonymized datasets where possible to support reproducible research
3. **Attribution:** Properly cite all prior work, including foundational research 
4. **Transparency:** Clearly document methodologies, limitations, and potential biases

---

## SECTION 11: REFERENCES

[1] Rutgers University, Department of Computer Science. (2005). *CS 552 Fall 2005 Class Project Assignment*. https://people.cs.rutgers.edu/~rmartin/teaching/fall05/cs552/project.html 

[2] Academia.edu. (2006). *Performance modeling and knowledge processing in high-speed interconnected intelligent educational networks*. https://www.academia.edu/82932802/Performance_modeling_and_knowledge_processing_in_high_speed_interconnected_intelligent_educational_networks 

[3] Boston University, Institute for Global Sustainability. (2025). *Yikai Zhang Profile*. https://www.bu.edu/igs/profile/yikai-zhang/ 

[4] Ibrahim, A. M. E. (2016). *Validation of a Model Predictive Control Algorithm for Priority-Based Routing* [Master's thesis, Eindhoven University of Technology]. https://research.tue.nl/en/studentTheses/validation-of-a-model-predictive-control-algorithm-for-priority-b 

### Additional References to Incorporate (from initial analysis):

[5] Nzobokela (2024) - Comparative analysis of queuing disciplines using OPNET

[6] HAL Archive - Heavy-tailed traffic and maximum entropy methods

[7] APCC Research (2025) - Wireless congestion control and queue management

[8] SciELO Study (2018) - Empirical characterization showing TCP limitations in queuing models

[9] Jean-Marie (2000) - Historical evolution and new challenges in network performance evaluation

[10] NIH/PMC Study (2024) - Computational limits of BCMP networks and parallel simulation alternatives

[11] AoI Research (2023) - Gaps between queuing theory and modern wireless systems

[12] Chen et al. (2012) - Mixed queueing network model for mobility

---

## SECTION 12: APPENDICES

### Appendix A: Detailed Traffic Characterization Methodology
[To be developed]

### Appendix B: Classical Model Mathematical Derivations
[To be developed]

### Appendix C: Hybrid Framework Pseudocode and Algorithms
[To be developed]

### Appendix D: Ethical Approval Application Template
[To be developed]

### Appendix E: Data Management Plan
[To be developed]

---

## SUBMISSION CHECKLIST

| Item | Completed |
| :--- | :--- |
| Title page with all identifiers | ☐ |
| Abstract (250-300 words) | ☐ |
| Introduction with clear problem statement | ☐ |
| Research questions (2-4) | ☐ |
| Literature review with gap identification | ☐ |
| Methodology section with sufficient detail | ☐ |
| Timeline with milestones | ☐ |
| Resources and budget | ☐ |
| Ethical considerations | ☐ |
| References in proper format | ☐ |
| Supervisor signature | ☐ |

---

Would you like me to develop any specific section in greater detail, or would you like assistance with tailoring this template for a specific funding application or university requirement?


