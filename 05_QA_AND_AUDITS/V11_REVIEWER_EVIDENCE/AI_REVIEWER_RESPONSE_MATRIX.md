# AI reviewer response matrix

| ID | Reviewer issue | Assessment | V11 action | Evidence/location | New experiment |
|---|---|---|---|---|---|
| Q1 | Non-sensitive semantic retention definition | AGREE - clarity gap | Added exact denominator, numerator, edge identity condition, seed aggregation, and non-pooled interpretation. | Methods 5.2; METRIC_DEFINITION_AUDIT.md | NO |
| Q2 | E2E model, prompts, decoding, queries, and scripts | PARTIALLY AGREE - many details existed, exact prompt/parser visibility improved | Added exact prompt contract, parser behavior, prompt-contract version, runner/query/raw-output hashes; no generation rerun. | Methods 5.5-5.6; E2E_QA_REPRODUCIBILITY_PROTOCOL.md | NO |
| Q3 | Runtime, acceptance ratio, memory, scaling | PARTIALLY AGREE | Surfaced existing S6/S17 runtime and 2K completion telemetry. Explicitly states that memory and proposal-attempt counts were not instrumented. | Results after Table 3; Limitations; RUNTIME_AND_2K_TELEMETRY_AUDIT.md | NO |
| Q4 | Topology-phase attribute transfer leakage | PARTIALLY AGREE | Clarified that topology transfer occurs after relation sanitization and cannot restore pre-sanitization labels; added explicit release-attribute allowlist guidance. | Methods 4.2; ATTRIBUTE_TRANSFER_AND_DEPLOYMENT_GUARDRAIL_AUDIT.md | NO |
| Q5 | Connected components, path length, reachability | ALREADY EVALUATED / cross-reference gap | Added direct cross-reference to Table 7 and S17; explicitly states global average shortest-path length was not computed. | Results 6.4 | NO |
| Q6 | PRIVATE_RELATION shared covers and stochastic covers | ALREADY EVALUATED / interpretation strengthened | Added no-universal-optimum interpretation and scoped stochastic/taxonomy covers as future work. | Discussion 7.5; S20 | NO |
| Q7 | Directed/heterogeneous/multigraph robustness | SCOPE LIMITATION | Added concrete design changes required for directed, typed, heterogeneous, and multigraph settings; no unsupported generalization. | Discussion 7.7 | NO |
| Q8 | Cross-release alias linkability and HMAC | AGREE - deployment guidance gap | Added keyed HMAC, per-release secret, rotation, collision detection, and access-controlled mapping guidance while retaining evaluated MD5 scheme. | Methods 4.1; Discussion 7.7 | NO |
| Q9 | False-positive/false-negative policy drift | ALREADY EVALUATED / visibility strengthened | Made 5%, 10%, and 20% nested false-negative, false-positive, and symmetric scenarios explicit and cross-referenced S21. | Methods 5.2 and 5.4; Results 6.3 | NO |
| Q10 | 2K implementation, invariants, budget, cost | ALREADY EVALUATED / visibility strengthened | Added explicit cross-reference to exact implementation, same-budget targets, realized counts, joint-degree checks, component metrics, and runtime in S17-S18. | Methods 5.3; Results 6.2 | NO |
| Q11 | When policy guidance wins versus random | AGREE - synthesis gap | Added objective-dependent synthesis: semantic selectivity and E2E favor policy guidance; structural/representation regimes can be random-competitive; no causal density/entropy claim. | Discussion 7.1 | NO |
| Q12 | Exact degree privacy-utility impact and weaker constraints | AGREE - deployment interpretation gap | Added quasi-identifier risk, clarified compatibility role, and scoped partial/distributional preservation to future work. | Discussion 7.3 | NO |

## Revision rule

No new experiment, dataset, attack protocol, formal guarantee, or numerical result was introduced. All edits are evidence-backed clarification, visibility, deployment guidance, or explicit scope boundaries.
