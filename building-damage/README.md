# Building damage

Predict how badly a building was damaged from a pair of satellite images, one before the disaster and one after.

I'm using the [xBD dataset](https://xview2.org) from the xView2 challenge. It has pre/post Maxar imagery for hurricanes, floods, wildfires and earthquakes, with building polygons labelled as no damage, minor, major or destroyed. To register and download, go to xview2.org and put the data in `data/xbd/`.

The plan is to start with two or three disasters, crop a patch around each building, and train a small CNN on the stacked pre/post patches. The main thing I want to get right is the split. Testing on a disaster the model hasn't seen should give a much more realistic score than a random split.

## Notes

