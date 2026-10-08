# EO disaster risk

Machine learning on Earth-observation data for natural hazards.

| Project | Task | Data |
|---|---|---|
| [Building damage](building-damage/) | Classify per-building damage from pre/post satellite image pairs | [xBD](https://xview2.org) |

## Evaluation

The modelling is standard; the evaluation is where geospatial ML goes wrong.

| Trap | Why it bites | What to do |
|---|---|---|
| Spatial leakage | Nearby buildings and tiles are near-duplicates; random splits leak the test set into training | Split by region or event; report random vs blocked side by side |
| Class imbalance | Destroyed buildings are rare | Per-class F1 and a confusion matrix, never raw accuracy |
| Domain shift | Models tuned on one region or disaster type degrade on another | Hold out an entire event as the final test |
| Label quality | Labels come from human annotators working at the limits of image resolution | Inspect a sample by eye; test sensitivity to label cleaning |

## Layout

```
building-damage/   notebooks, code and results
data/              downloaded datasets, git-ignored
```

## Setup

Uses [uv](https://docs.astral.sh/uv/).

```sh
uv sync
uv run jupyter lab
```

Datasets go in `data/<dataset>/` and are never committed.
