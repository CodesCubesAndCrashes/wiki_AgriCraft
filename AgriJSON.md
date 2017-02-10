AgriCraft 2.0.0 introduces an exciting new feature: **JSON Customization**!

JSON Custom Files (i.e. AgriJSONs) allow for total control of your agricultural experience, and even work in multiplayer environments! The files are so powerful, that there are no longer any hard-coded plants coded into the mod, as instead they are all done by JSON files. This means that if wheat plants dropping wheat is too vanilla for you, you can easily modify them to drop cooked chickens instead (it tastes like chicken...). This page serves as your definitive guide to modding AgriCraft in this manner, as to make you essentially a meta-modder.

AgriCraft JSON Files are currently broken down into three categories:
 - [AgriPlants](AgriPlants)
 - [AgriMutations](AgriMutations)
 - [AgriSoils](AgriSoils)

These JSON files may be placed in any sub-directory of `config/agricraft/json/defaults`. Specially named folders, herein known as AgriSets, allow for the conditional loading of a large group of plants based on the presence of mods. Specifically, if a JSON file is placed in a sub-directory of a folder named `harvestcraft_mod` the JSON file will only be loaded by AgriCraft if a mod with the id `harvestcraft` is currently loaded by Minecraft Forge.