# MineTweaker3 integration

Documents all the methods provided by AgriCraft. For feature requests create an issue or head over to the FTB thread.


## CustomWood recipes

CustomWood recipes are the recipes for the Channel, Tank and Valve. These are like vanilla recipes with the only difference that for each plank type a seperate recipe is created.

Import: `import mods.agricraft.CustomWood`

### Provided methods 

- remove(IItemStack)
- addShaped(IItemStack, IItemStack[][])
- addShapeless(IItemStack, IItemStack[])

### Example

    import mods.agricraft.CustomWood;

    CustomWood.remove(<AgriCraft:waterChannel>);
    CustomWood.addShaped(<AgriCraft:waterChannel>,
        [[<minecraft:planks>, null, <minecraft:planks>],
        [null, null, null],
        [null, <minecraft:planks>, null]]);

    CustomWood.remove(<AgriCraft:channelValve>);
    CustomWood.addShapeless(<AgriCraft:channelValve>,
        [<AgriCraft:waterChannel>, <AgriCraft:waterChannel>, <minecraft:stick>])

This example will change the recipe for all Channel and Valve versions. Note that the `<minecraft:planks>` in the shaped recipe and the `<AgriCraft:waterChannel>` in the shapeless recipe, will get replaced with the "correct" instance for all the recipes.