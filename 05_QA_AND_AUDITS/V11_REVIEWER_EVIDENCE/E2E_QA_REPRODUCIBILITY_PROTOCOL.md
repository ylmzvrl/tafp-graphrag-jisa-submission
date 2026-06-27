# End-to-end relation-QA reproducibility protocol

- Model identifier: `Qwen/Qwen2.5-3B-Instruct`
- Prompt contract: `1.2-relation-label-only`
- Generation seed: `42`
- Decoding: `do_sample=False`; protocol lock records temperature `0.0`
- Maximum input tokens: `3072`
- Maximum generated tokens: `32`
- Batch size: `2`
- Conditions: `baseline, full, random_full_budget, 2K`
- Protection seeds: `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]`
- Actual rows: `43080`
- Runner: `tafp_run_locked_e2e_relation_qa_v1_3.py`
- Runner SHA-256: `611e6b7006a4f4fd787ce1f01aad2d1d873003d3606fd2500a237798ff43d189`
- Query-manifest SHA-256: `2942e2a71fd1ad743a1df9de9d23fbbcc8d5774c2d500ae1bb59326e59b90efa`
- Protocol-lock SHA-256: `7b652eef11ad0f9bb63a19caec802b32bb48cfdeb12ba47d3b838064e106ac37`
- Raw 43,080-row evidence SHA-256: `d025b5ac1b79164316f640884cdfb29af075332b5d71a149de39606ac824e193`
- Repository branch: `revision/applied-sciences-pre-submission-20260620t212703z`
- Repository HEAD: `d961d965fa449fff2826a9f6c640b892121cb0b1`

## Exact prompt contract

The exact locked runner instructs the model to use only the numbered `RETRIEVED ORDERED PATH EVIDENCE` lines, copy only the relation label between the two `--` separators for each path line, preserve order, join labels using ` > `, output exactly `NOT_CONNECTED` when no path exists, and return one line without node identifiers, explanations, JSON, bullets, or code fences.

## Parser

The parser strips code fences and common answer prefixes, normalizes arrow/pipe/comma delimiters, maps only against the query-specific allowed relation list, and returns `PARSE_ERROR` when no allowed relation can be recovered. The primary analysis retained all parse failures.

## Reproducibility boundary

The run metadata identifies the Hugging Face model repository but does not record a separate model-snapshot commit. Exact runner, prompt contract, query manifest, raw outputs, branch, repository HEAD, environment, and result artifacts are nevertheless hash-identified.
