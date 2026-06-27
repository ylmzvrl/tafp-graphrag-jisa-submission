# Non-sensitive semantic retention: exact operational definition

## Verified implementation

The graph-level metric iterates over every original edge. An edge is in the denominator when the original edge is not sensitive under the supplied policy. It contributes one to the numerator only when the transformed graph still contains the same unordered endpoint pair and the exposed transformed relation equals the original `relation_type`. Removed or rewired-away original edges contribute zero. The condition-level value is numerator divided by the number of original policy-non-sensitive edges.

Table 2 reports the arithmetic mean and standard deviation across 15 protection seeds separately for each dataset and variant. It is not a pooled cross-dataset micro-average.

- Source: `/mnt/data/section5_5/exact_sources/v10_graphrag_structural_utility.py`
- Source SHA-256: `f4499acda1a3c28b90eb3d98f23ed7fcb19b4e38cb823e5fb4f9bfa96296ddb7`

## Source excerpt

```python
589: 
590:     base_edges = {
591:         canonical_edge_key(base_graph, u, v)
592:         for u, v in base_graph.edges()
593:     }
594: 
595:     protected_edges = {
596:         canonical_edge_key(protected_graph, u, v)
597:         for u, v in protected_graph.edges()
598:     }
599: 
600:     common_edges = base_edges & protected_edges
601:     removed_edges = base_edges - protected_edges
602:     added_edges = protected_edges - base_edges
603: 
604:     sensitive_total = 0
605:     sensitive_hidden = 0
606:     non_sensitive_total = 0
607:     non_sensitive_semantics_preserved = 0
608: 
609:     for u, v, base_attrs in base_graph.edges(data=True):
610:         is_sensitive = edge_is_sensitive(base_attrs)
611: 
612:         if is_sensitive:
613:             sensitive_total += 1
614:         else:
615:             non_sensitive_total += 1
616: 
617:         if not protected_graph.has_edge(u, v):
618:             if is_sensitive:
619:                 sensitive_hidden += 1
620:             continue
621: 
622:         protected_attrs = (
623:             protected_graph.get_edge_data(u, v) or {}
624:         )
625: 
626:         original_relation = str(
627:             base_attrs.get(
628:                 "relation_type",
629:                 "related_to",
630:             )
631:         )
632: 
633:         protected_relation = exposed_relation(
634:             protected_attrs
635:         )
636: 
637:         if is_sensitive:
638:             if protected_relation != original_relation:
639:                 sensitive_hidden += 1
640:         else:
641:             if protected_relation == original_relation:
642:                 non_sensitive_semantics_preserved += 1
643: 
644:     return {
645:         "dataset_name": dataset,
646:         "protection_seed": protection_seed,
647:         "variant": variant,
648:         "base_nodes": base_graph.number_of_nodes(),
649:         "base_edges": base_graph.number_of_edges(),
650:         "protected_nodes":
651:             protected_graph.number_of_nodes(),
652:         "protected_edges":
653:             protected_graph.number_of_edges(),
654:         "retained_original_edges": len(common_edges),
655:         "removed_original_edges": len(removed_edges),
656:         "added_edges": len(added_edges),
657:         "original_edge_retention": safe_divide(
658:             len(common_edges),
659:             len(base_edges),
660:         ),
661:         "changed_degree_nodes": changed_degree_nodes,
662:         "degree_l1_error": degree_l1_error,
663:         "exact_per_node_degree_preservation": int(
664:             changed_degree_nodes == 0
665:         ),
666:         "sensitive_relation_hidden_rate": safe_divide(
667:             sensitive_hidden,
668:             sensitive_total,
669:         ),
670:         "non_sensitive_semantic_retention": safe_divide(
671:             non_sensitive_semantics_preserved,
672:             non_sensitive_total,
673:         ),
674:         "risk_computation_seconds": risk_seconds,
```

## Independent identity check

The full-variant means in S6 were compared with the independently generated private-token means in S20. All five dataset values matched within 1e-12.

- AGNews: S6=0.919620958751393; S20=0.919620958751394; |difference|=1.110e-16; PASS=True
- CNN_DM: S6=0.917092651757189; S20=0.917092651757189; |difference|=0.000e+00; PASS=True
- IMDB: S6=0.919185246352876; S20=0.919185246352876; |difference|=1.110e-16; PASS=True
- PubMed: S6=0.899346405228758; S20=0.899346405228758; |difference|=1.110e-16; PASS=True
- SynthPII: S6=0.921934369602763; S20=0.921934369602763; |difference|=1.110e-16; PASS=True
