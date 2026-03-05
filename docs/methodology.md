# Methodology: The 7.5% Structural Baseline

The SDAG framework utilizes a **conservative empirical baseline of ~7.5%** for non-productive compute in hyperscale LLM environments. This figure represents the "Architectural Tax" inherent in current-generation MoE (Mixture of Experts) and Sparse Transformer models.

### Decomposition of the Baseline:

1. **Safety & Alignment Overhead (~3.5%)**
   Hyperscale models operate with secondary validation passes, safety classifiers, and policy filters. These guardrails consume compute cycles that stabilize the output according to safety protocols but do not contribute to the raw task-solving efficiency.

2. **Routing Instability (~2.5%)**
   In MoE systems, expert load balancing is a known trade-off. Under high concurrency, schedulers often prioritize latency, leading to "expert over-activation" or sub-optimal routing decisions. This creates a persistent delta between theoretical sparsity and real-world execution.

3. **Multi-Pass Inference Correction (~1.5%)**
   Internal consistency checks, re-ranking, and corrective decoding loops are often employed to maintain generation quality across long-context windows. These represent redundant compute cycles.

### Conclusion
While specific cluster performance may vary, the **7.5% baseline** serves as a realistic "Zero-Point" for auditing infrastructure durability and OpEx leakage.
