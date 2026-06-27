# Attribute-transfer and deployment guardrail audit

Verified order: sensitive relation labels are replaced before either structural phase. During relation-level rewiring, copied source-edge dictionaries are sanitized by setting `relation_type` and `protected_relation_type` to `PRIVATE_RELATION`, `sensitive` to `0`, and `relation_sensitivity` to `0.0`. The topology phase then operates on the current post-relation graph and transfers corresponding current source-edge dictionaries without additional sanitization. It therefore does not restore the pre-sanitization original relation label.

Residual boundary: any attribute intentionally retained in the current released dictionary can remain observable or be moved with its source edge. Production hardening should use an explicit edge-attribute allowlist and exclude original labels, internal policy fields/scores, and audit metadata before topology rewiring. This is a deployment recommendation, not an evaluated additional defense.

- Evidence: Section 4 strict evidence review items S4-020 through S4-026 and Algorithm 1 lines 6-8.
- Manuscript V10 paragraphs 121-127 and 157-159.
