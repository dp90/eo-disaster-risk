# Building damage from pre/post satellite imagery

Predict per-building damage level from a before/after image pair.

| Item | Detail |
|---|---|
| Data | xBD dataset (xView2 challenge): pre/post Maxar imagery, ~850k building polygons across hurricanes, floods, wildfires, earthquakes |
| Labels | Four classes per building: no damage, minor, major, destroyed |
| Scope | 2 to 3 disasters, fixed-size patches cropped around each building polygon |
| Model | Small CNN or pretrained ResNet on stacked pre/post patches; or a U-Net for segmentation |
| Use | Ranking buildings for on-the-ground inspection after a disaster |

## What makes it hard

- Severe class imbalance: most buildings are undamaged. Report per-class F1 and a confusion matrix, not accuracy.
- Label noise at the minor vs major boundary. Try collapsing to 3 classes and compare.
- Domain shift: hold out one whole disaster as the test set. A model trained on hurricanes scored on a wildfire is the honest number.
- Image alignment: pre/post pairs are not perfectly co-registered. Check a few by eye before training.

## Approach

1. Download a subset and look at 20 examples by eye.
2. Build the split first (hold out a whole disaster), then a baseline.
3. Train the real model; compare a random split with the held-out-disaster split.
4. Error analysis: which classes, disasters and building types does it get wrong?

## Data

Register and download at <https://xview2.org>. Put it in `data/xbd/`.

## Results

_To come._
