# Runtime and 2K telemetry audit

- Full-variant dataset-level mean apply_variant runtime range: 0.052353-0.330011 s.
- Full-variant normalized runtime range: 0.018724-0.022807 s per 1,000 original edges.
- Controlled 2K-to-full mean runtime ratio range: 1.640105-2.444996.
- 2K target/realized summary equality: True.
- Controlled replication evidence reports 75 primary 2K conditions, 75 deterministic replays, and zero convergence failures.
- Peak memory and proposal-attempt counts were not retained in the reviewed evidence. Acceptance ratios and asymptotic scaling are therefore not reported.

## Full variant, primary runtime telemetry

| dataset_name   |   runtime_mean |   runtime_sd |   normalized_mean |   normalized_sd |   semantic_retention_mean |
|:---------------|---------------:|-------------:|------------------:|----------------:|--------------------------:|
| AGNews         |       0.135357 |     0.045219 |          0.020691 |        0.006912 |                  0.919621 |
| CNN_DM         |       0.330011 |     0.029450 |          0.021643 |        0.001931 |                  0.917093 |
| IMDB           |       0.184783 |     0.047777 |          0.022807 |        0.005897 |                  0.919185 |
| PubMed         |       0.079651 |     0.041730 |          0.018724 |        0.009809 |                  0.899346 |
| SynthPII       |       0.052353 |     0.031896 |          0.021814 |        0.013290 |                  0.921934 |

## Same-telemetry 2K comparison

| dataset_name   |   dk2_full_budget |     full |   random_full_budget |   ratio_2k_to_full |
|:---------------|------------------:|---------:|---------------------:|-------------------:|
| AGNews         |          0.108105 | 0.060909 |             0.062804 |           1.774861 |
| CNN_DM         |          0.298490 | 0.176440 |             0.184923 |           1.691737 |
| IMDB           |          0.145328 | 0.082684 |             0.084164 |           1.757631 |
| PubMed         |          0.100303 | 0.041024 |             0.043327 |           2.444996 |
| SynthPII       |          0.040750 | 0.024846 |             0.021043 |           1.640105 |
