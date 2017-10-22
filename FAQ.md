## How do I prevent a plant from spawning? How do I disable it?

In the corresponding JSON file, change the `spawn_chance` or `enabled` settings. Note that if you delete the JSON file for a bundled plant, it will be regenerated with its default settings.

## How do I disable weeds? 

Quick answer: Same like any other plant.

Longer answer: In `config/agricraft/json/SELECTSERVERHERE/vanilla/plants/weed_plant.json` set `"enabled": false`, or set `"spawn_chance": 0.0`.

Longest answer: As part of the transition to using customizable JSON files for all of the plants, weeds are now no longer special or different than other plants. What gives them that annoying nature is that they have a non-zero chance to spontaneously spawn, and because they're aggressive they have the ability to technically replace neighboring plants. Except that, by default they're too weak to do that really.

## Why won't some plant products stack with others?

Probably because one of those stacks have the AgriCraft plant stats on them, and so the NBT data doesn't agree. AgriCraft can use existing items as seeds, but it has to record extra information on there. The tooltip should show some of it, plus there's a config option to show a more in-depth tooltip. There's also a bug currently that makes leaves off an NBT tag seeds, and so those form a separate stack too.

## How do I use Fertilizers from other mods?

Crouch while right clicking. The way right clicks work, the block usually gets the first chance to handle the click, and if it does, then the item doesn't do anything. If you want to skip the block, you have to crouch while right clicking. Forge allows coders to add exceptions, but that is the basic rule.

## Why can I keep applying bonemeal to a fully grown plant?

Plants can have a non-zero chance to spread to their neighboring single crop sticks. This is different from the spread onto a cross crop, because the stats don't change here. This behavior might change in the future, once more fertilizers are added.

## Why can't I put the seed into the Seed Analyzer?

My first guess is that there isn't support for that plant or mod yet. Check the JSON folder for the server (default is for all of single player), then if there's a folder for the mod, and then if there's a file for that plant.