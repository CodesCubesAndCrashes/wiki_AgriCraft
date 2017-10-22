# Things to do

###### (The [[Known Issues|KnownIssues]] list has some separate items currently. So check that out too.)

## JSONs
* The defaults need reviewing.
* The seeds for the the different dye plants can't be obtained without cheating.
* All five tiers of the Infernum plant give the same amount of essence.
* Mods should have separate address spaces, to prevent name collisions.

## Features
* Add fluid capabilities. At least to the tank, but then all of the irrigation stuff.
* Fire events for planting, growing, fertilizing, etc. Probably subclass the Forge events.
* Add support for detecting liquids, fire, skulls, and other atypical blocks. For examples, sugarcane can be planted without water nearby.
* Set the documentation or website up so that we can accept PRs or contributions.
* Expand compatibility. For example, MFR machines.
* Enable weeds to actually be a threat.
* The Journal and JEI interfaces need updating.

## Misc Fixes
* The `water_pad` is not working 100% yet, so there's no workaround for supporting plants that grow on water.
* Grate rendering and bounding boxes aren't correct.
* Need to check for other client side lighting information bugs.
* Stacking issue with seeds from the analyzer versus crop sticks.
* When picking plants from a list (spawning, spreading) the code often favors items from the front of the list. That needs instead to be a fair weighted random pick. Maybe add a helper method or class. (Cache the work.)
* Redstone ore that is glowing is different from normal kind, and so is invalid for the redstone resource plant.
* The Sprinkler irrigation doesn't respect `bonemeal: false`. Oops.
* Crop sticks won't replace grass and other such items when being placed. Instead they get put next to them.
* The Sprinkler could cache what it has found and search less often.
* The irrigation multiblocks need review.
* Water particle effect for the sprinkler's target.

## Porting 
* Look into how big the changes for 1.11 and 1.12 are.

## Wishful ideas
* Fertilizers with different features.
* Using consumable fertilizers in the irrigation.
* Plants affecting the player when the walk through the crop.
* Variety to the crop sticks. For example, supporting larger versions of normal plants.
* Instead of harvesting resetting growth progress to zero, have a difference between initial growth and regrowth.