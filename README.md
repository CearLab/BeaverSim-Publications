# BeaverSim for "Biomimicry at the Landscape Scale" (Biomimetics, 2026)

This branch contains the code, notebooks and example data used in:

> F. Oliva, J. Kennedy, J. Werfel, K. L. Bar-Sinai, A. Degani. *Biomimicry at the Landscape Scale: Agent-Based
> Model Simulating Beaver-Inspired Construction.* Biomimetics 2026. https://doi.org/10.3390/biomimetics11070515

It is a frozen snapshot: one commit, tagged `biomimetics-2026`, built from commit `d50a880` of the BeaverSim
repository. Ongoing development, and the full history, are on the repository's `main` branch.

## Setup

You need Python 3.12 and [Git LFS](https://git-lfs.com/). The Rumney Marsh elevation table (287 MB) is
stored with LFS, so install LFS before cloning:

```bash
git lfs install
git clone -b paper/biomimetics-2026 https://github.com/CearLab/BeaverSim-Publications.git
cd BeaverSim-Publications
git lfs pull                       # only needed if RumneyMarsh.csv is a small text pointer
python -m venv beaversim_env
source beaversim_env/bin/activate  # Windows: beaversim_env\Scripts\activate
pip install -r requirements.txt
```

Run the notebooks from the repository folder, in VS Code or Jupyter.

## The simulator

BeaverSim is an agent-based simulator of beaver colonies on real terrain. The terrain is an elevation model or a
classified drone image. Agents switch between two roles: Explorers look for resources and Builders do localized
engineering. They harvest vegetation, move material and reinforce canals, and the vegetation regrows with the
seasons. The code is in `beaversim/`:

```
beaversim/
  ral/backend/        simulation and visualization backends
  ral/environment/    the environment: vegetation, water, terrain
  ral/robot/          the agents' behaviour
  scenarios/          the simulation scenario used in the notebooks
data_acquisition/
  modules/            conversion of elevation tables and RGB images into simulation grids
  example_datasets/   the example data of the three sites
notebooks/            preprocessing and simulation notebooks (below)
```

## Case studies and example data

| Site | Input | Example data | Preprocessing notebook |
|---|---|---|---|
| Acadia National Park | elevation model (DEM), 0.5 m | `data_acquisition/example_datasets/ACADIA_DEM/` | `notebooks/notebooks_DEM/dem_conversion_Acadia_interactive.ipynb` |
| Rumney Marsh, Boston | elevation model (DEM), 1 m | `data_acquisition/example_datasets/RUMNEY_MARSH_DEM/` | `notebooks/notebooks_DEM/dem_conversion_RumneyMarsh_interactive.ipynb` |
| Rumney Ranch, Montana, area A2 | drone RGB images, 2018 | `data_acquisition/example_datasets/RUMNEY_RANCH_RGB/A2/` | `notebooks/notebooks_RGB/rgb_conversion_RumneyRanch_A2_interactive.ipynb` (and `_iterative`), settings in `notebooks/notebooks_RGB/config/` |

The raw elevation data come from USGS and NOAA (see the paper's Data Availability statement).

## Notebooks and figures

| Notebook (`notebooks/simulations/`) | Site | Figures |
|---|---|---|
| `demo_csv_acadia.ipynb` | Acadia | 1, 2a |
| `demo_csv_boston.ipynb` | Rumney Marsh | 4, 5, 6 |
| `data_analysis.ipynb`, `data_analysis_montecarlo.ipynb` | Rumney Marsh | 7, 8, 9, 10 |
| `demo_rgb_montana.ipynb` | Rumney Ranch A2 | 2b, 11, 12 |
| `demo_rgb_montana_montecarlo.ipynb` | Rumney Ranch A2 | 13, 14 |

Appendix figures A1, A2 and A3 come from the preprocessing notebooks in the table above. Monte Carlo results use
n = 5 replications.

Simulation outputs are written to `output/`, which git ignores.

## Known differences from the current code

- **Exploration direction.** In this version, the exploration step is rotated by 90 degrees. The paper's results
  were produced with this behaviour, and this snapshot keeps it so the results can be reproduced. It is fixed
  on `main` (commit `c7250a0`), so runs with the current code will differ.
- **Random seeds.** In this version, setting the seed does not make a run exactly repeatable: a rerun gives
  statistically similar results, not identical ones. Seeding is fixed on `main` (commit `1e91230`).

## Citation

```bibtex
@article{oliva2026biomimicry,
  title   = {Biomimicry at the Landscape Scale: Agent-Based Model Simulating Beaver-Inspired Construction},
  author  = {Oliva, Federico and Kennedy, Jordan and Werfel, Justin and Bar-Sinai, Karen Lee and Degani, Amir},
  journal = {Biomimetics},
  year    = {2026},
  volume  = {11},
  number  = {7},
  pages   = {515},
  doi     = {10.3390/biomimetics11070515}
}
```

## Licence

Licensed under the [Apache License, Version 2.0](LICENSE).
