# EO disaster risk

Machine learning on Earth-observation data for natural hazards.

So far there's one project: [building-damage](building-damage/), predicting damage to buildings from before/after satellite images.

## Setup

Uses [uv](https://docs.astral.sh/uv/):

```sh
uv sync
uv run jupyter lab
```

Datasets go in `data/` and aren't committed.
