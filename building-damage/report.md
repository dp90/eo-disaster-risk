# Building damage from satellite imagery

## Introduction and problem statement

After a major disaster, one of the first questions is where the damage is and how bad it is. Satellite imagery can answer that faster than teams on the ground. Organisations that do rapid mapping use it to produce damage maps, which then help guide assessment teams, aid and recovery planning. 

_Unit of prediction_: the building. For each building you crop a patch around its polygon from both the pre and post image, leaving a bit of margin for context, and predict its damage class. A tile can hold dozens of buildings with different damage levels, so it's the wrong unit to predict. Tiles and areas come in later, when you add up the building predictions.

_Label_: the damage class, with polygons given. Assuming you already have the polygons is realistic. In practice, building footprints come from OpenStreetMap, Microsoft or Google Open Buildings, or a local cadastre, and they exist before the disaster. Something to keep in mind: xBD's polygons are unusually good. They were drawn by hand on these exact images, so they line up perfectly. Footprints from other sources would sit a few pixels off. That's fine but it makes the task a little easier than reality.

Bigger picture: how many people were affected? We could add damaged buildings weighted by footprint up by area. But
1. Footprint area tells us how much building was damaged, but not how many people were affected. xBD has no population data. We'd have to bring in a layer such as WorldPop or GHSL. This could be interesting as a next step. To start, I'll use damaged footprint area per grid cell.
2. What to compare against? We can't recreate how practitioners do it today, which is mostly analysts interpreting the imagery by hand. We can compare against the labels by ranking the grid cells by damage computed from the true labels and seeing how closely the model's ranking matches. For example, of the 10 worst-hit cells, how many does the model put in its own top 10? We'll also add a simple baseline, such as ranking cells by how much the pixels changed between pre and post, so that we can tell whether the model adds anything.

A draft problem statement:

_Given pre- and post-disaster satellite images and building footprints for a disaster the model has not seen, predict each building's damage class. Then rank areas by damaged building footprint to show where damage is concentrated. Evaluate at two levels: per-building F1, and how well the area ranking matches the one computed from the true labels, compared with a simple pixel-change baseline._


## Data

Which disasters and why, the label counts per disaster and class, other descriptive statistics, closer look at a few individual samples.

## Methodology

### Evaluation design

How the data is split by disaster, geospatially, and in time. The metrics we consider at the building and area level, and the baselines. Written down before we have the results to avoid confirmation bias.

### Models

From the simplest baseline to the CNN: inputs, architecture, training setup and the choices made along the way.

## Results and error analysis

Building-level and area-level results against the baselines, followed by where the model goes wrong, for example, by class, by disaster, by building type, etc.

## Limitations and next steps

What we can conclude from the results, what was simplified compared with real use, and what I'd look at next.
