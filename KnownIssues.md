# Settings

## Many of the config options are non-functional. 

Many things were left as placeholders during the beginning of the port to 1.10. But this easily leads to all sorts of confusion, since it's so misleading. Note that this applies to both the in game Mod Options menu and the "config/agricraft/config.cfg" file, since they're automatically kept in sync.

TODO: Comment out the useless options for now. And list the working or not options here, as a stopgap. The problem is that the settings removed in the mod get recreated because they still exist in the user's config.cfg.

## The config options don't get synchronized with remote servers.

This isn't a problem for single player. And players can manually set or update the server side config.cfg. But it's a pain, and a source of bugs. 

TODO: Add the logic for sending and updating the settings.

## Some config options require a reboot to take effect, but aren't marked for it.

For example, you need to restart to change the chance of mutation versus a spread onto a cross crop. I'm pretty sure that there's ways of automatically enforcing this, but a fancy solution is a lower priority over the other config related issues. 

TODO: Add a hint to the comment at least.

# Sprinkler 

## Water droplets look weird

The rendering code for them hasn't been fixed up completely yet. Sorry. :(

## Farmland will flicker dry distractingly often

When vanilla farmland gets a random tick, and there isn't water nearby, it stops being moist. Meanwhile, the sprinkler does a full loop every few seconds (minimum 49 ticks). Unless the loop duration is incredibly long, the sprinkler will reset the moisture before the farmland gets enough random updates (seven?) to completely dry out. But the flicker is annoying, and I would like to improve that. 

## Sprinkler model disappears sometimes. 

I thought this was an issue with resource packs, but I've had it happen with vanilla textures. 

# Compatibility

## AgriCraft Sprinkler

When it encounters a block that implements `IGrowable` or `IPlantable`, it'll call `updateTick` on it. That's not the same as applying bonemeal, or `grow`, but since it only consumes water that seems fair for now.

## AgriCraft Crop Sticks

Currently, right clicks as a default get turned into harvest actions, and then end the activation chain. This prevents items from running their own code by default. But if you crouch while right-clicking, than Forge will skip the block logic. The crop sticks could handle this better, and the Fertilizers can be manually added the to existing exception list. But at least this all standard Forge behavior already.

## EnderIO

Sorta. The farming station just uses `ItemDye.applyBonemeal`, so it's compatible with anything that implements IGrowable. If you enable that setting, it will apply bonemeal you provide to crops, which is good. But it can also break (and pick up) the crop sticks in order to make room for other plants. I haven't tested it enough, but I suspect that giving the station tools or seeds is a bad idea.

## Extra Utilities 2

The Watering Can just does update ticks, so it works already. 

## Actually Additions

The Farmer only looks for blocks that extend the vanilla BlockCrops (which AgriCraft doesn't), so it does not work currently. The hand held fertilizer requires you to crouch first, because otherwise right-clicks are handled by the block before the item gets a chance to activate. The Ring of Growth works if you stand near the crops. The Worms should, although I haven't closely enough compared farmland with and without them. (They only give updates to IGrowable and IPlantable things on top of farmland.) 

## Thermal Expansion

All three of the Phyto-Gro tiers work, if you crouch. The area of affect works fine.

## Forestry

The Fertilizer works if you crouch.

## Others...

The IC2 Fertilizer doesn't work. Nor the Natura Bone Meal Bag. Nor the Roots Growth Powder (no idea if that's even for farming, tbh.) 

# Misc

## Mutations

The cross-over engine hasn't been updated to allow plants to spawn on cross crops when the light is invalid, or other requirements are unmet. 

## Seeds

The Seed Analyzer doesn't add the NBT tag for the associated plant, but seeds dropped by plants do have that tag. This prevents otherwise identical seeds from stacking, and it won't be obvious why unless you make NBT tags visible. Before fixing this, need to check which approach makes more sense. On the one hand, the plant you get from an item determined by what the item itself is. On the other hand, it's possible for multiple JSONs to accidentally use the same item as a seed.

## Magnifying Glass

The brightness check code results can still be a little weird sometimes (compare with F3 when clicking on a torch), so try different blocks and faces to make sure you have right answer. The reason is that it calls `getLightFromNeighbors` on the position above what was clicked, and get light from neighbors sometimes checks the five neighbors of that position. (Depending on `useNeighborBrightness`.) The bottom line though is that it's the same call that `GrowthRequirement#hasValidLight` uses, so for purposes of plant debugging it is functioning correctly. 

TODO: study vanilla lighting mechanics.

## `java.lang.RuntimeException: ALREADY CONSTRUCTING VERTICES`

Darn, I thought we were done with that. Check if you've got JourneyMap 1.10.2 - 5.4.9b1 installed. Try disabling it, even if it's a different version. Otherwise, check out #1034 for more fun.

# This document... 

* Add links to the corresponding posts on the issue tracker.