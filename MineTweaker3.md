# MineTweaker3 integration

Documents all the methods provided by AgriCraft. For feature requests create an issue or head over to the FTB thread.


## CustomWood recipes

CustomWood recipes are the recipes for the Channel, Tank and Valve. These are like vanilla recipes with the only difference that for each plank type a seperate recipe is created.

Import: `import mods.agricraft.CustomWood`

### Provided methods 

- `remove(IItemStack result)`: Removes all recipes for crafting `result`
- `addShaped(IItemStack result, IItemStack[][] inputs)`
- `addShapeless(IItemStack result, IItemStack[] inputs)`

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

## Seed Mutations

Seed mutations are of the general form `<result> = <parent1> + <parent2>`. Additional parameters can further refine the mutation. Not all possibilities are exposed via MineTweaker (yet).

Import: `import mods.agricraft.SeedMutation`

### Provided methods

- `remove(IItemStack result)`: Removes all mutations where `<result>` is the result of the mutation.
- `add(IItemStack result, IItemStack parent1, IItemStack parent2)`
- `add(IItemStack result, IItemStack parent1, IItemStack parent2, int id, IItemStack block)`:
    - `id` can either be `1` or `2`. 
    - An `id` of `1` specifies that `block` must be **below** the resulting crop
    - An `id` of `2` specifies that `block` must be **nearby**.

### Example

    import mods.agricraft.SeedMutation;

    SeedMutation.remove(<minecraft:pumpkin_seeds>);
    SeedMutation.add(<minecraft:pumpkin_seeds>, <minecraft:melon_seeds>, <minecraft:wheat_seeds>);


## Seed blacklist

Seeds on the blacklist can **not** be planted on crops.

Import: `import mods.agricraft.SeedBlacklist`

### Provided methods

- `add(IItemStack seed)`
- `add(IItemStack[] seeds)`
- `remove(IItemStack seed)`
- `remove(IItemStack[] seeds)`

### Example

    import mods.agricraft.SeedBlacklist;

    SeedBlacklist.add([<minecraft:pumpkin_seeds>, <minecraft:melon_seeds>]);