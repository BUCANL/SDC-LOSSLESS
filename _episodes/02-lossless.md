---
title: "The Lossless Pipeline"
teaching: 20
exercises: 10
questions:
- "What are the inputs and outputs of the Lossless pipeline?"
- "What kinds of decisions does the Lossless pipeline make?"
objectives:
- "Understand the flow of decisions in the Lossless pipeline."
keypoints:
- "Decisions are made via criteria functions."
- "Parameters are changed via batch configuration files."
---

This section is designed to outline the key procedures of each of the [Lossless pipeline scripts](https://github.com/BUCANL/BIDS-Lossless-EEG/wiki/Pipeline-Scripts).

### Scalpart (s01)

1. Load an initialized BIDS file.
2. Initialize marks
3. Optional staging
4. Co-register to MNI surface
5. Special case average re-reference
6. Compute ch_sd for time
7. Compute ch_sd for channels
8. Re-reference data
9. High pass filter
10. Low pass filter
11. Low R channel annotation
12. Bridge channel annotation
13. Flag rank channel
14. Re-reference data
15. Low R time annotation
16. Mark gaps
17. Save state
18. Purge data for Amica
19. Create Amica parameter files

### Initial Amica (s02)

The Amica script is run once initially.

### Compart (s03)

1. Load a `*_sa.set` file.
2. Load initial Amica model.
3. Recreate data via ICs
4. Compute log likelihood
5. Compute ic_sd1 annotation
6. Mark gaps
7. Save state
8. Purge data for Amica
9. Create Amica parameter files

### Amica (s04a, s04b, s04c)

The Amica script is run three more times in parallel after teh compnent artefact rejection to ensure that the Amica procedure is replicable if run multiple times on the same dataset.

### Concat and Dipfit (s05)

1. Load a `*_compart_data.set` file.
2. Load AMICA model A
3. Recreate data via model A ICs
4. Compute log likelihood for model A
5. Load models B and C
6. Compute log likelihood for models B and C
7. ISCtest
8. Compute ic_sd2 annotation
9. Theta/delta power annotation
10. Alpha power annotation
11. Beta power annotation
12. Low gamma annotation
13. High gamma annotation
14. Mark gaps
15. Dipole fitting
16. Rotate montage back to EEGLAB
17. Save state
18. Purge data
19. ICLabel
20. Load previous state, add back ICLabel info
21. Marks updates
22. BIDS export

{% include links.md %}