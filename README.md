# BeaverSim publications

BeaverSim is an agent-based simulator of beaver colonies on real terrain, developed at the
[CEAR Lab](https://github.com/CearLab), Technion. This repository holds the code and example data behind each
publication that uses it.

Each publication has its own branch and tag. A branch holds one frozen snapshot, a single commit with exactly the
code, notebooks and data used for that paper, and its README explains how to reproduce the results. This `main`
branch is only an index.

## Publications

| Year | Publication | Branch | Tag |
|---|---|---|---|
| 2026 | F. Oliva, J. Kennedy, J. Werfel, K. L. Bar-Sinai, A. Degani. *Biomimicry at the Landscape Scale: Agent-Based Model Simulating Beaver-Inspired Construction.* Biomimetics 11(7), 515. [doi:10.3390/biomimetics11070515](https://doi.org/10.3390/biomimetics11070515) | [`paper/biomimetics-2026`](../../tree/paper/biomimetics-2026) | [`biomimetics-2026`](../../releases/tag/biomimetics-2026) |

## Getting one publication's code

The example data include files stored with [Git LFS](https://git-lfs.com/). Install it first, then clone only the
branch you need:

```bash
git lfs install
git clone -b paper/biomimetics-2026 --single-branch https://github.com/CearLab/BeaverSim-Publications.git
```

## Licence

Licensed under the [Apache License, Version 2.0](LICENSE).
