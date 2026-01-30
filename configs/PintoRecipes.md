<h1 align="center">Config — Details</h1>
<p align="center">This page documents all configuration used by the plugin (primary focus: recipes.yml). Keep changes minimal and use the plugin GUI to generate result payloads.</p>

## Locations
- Bundled defaults: src/main/resources/recipes.yml
- Active data (after first run): plugin data-folder recipes.yml

### Top-level format
- Top-level keys are recipe identifiers (any string). Each recipe entry contains the fields below.

### Field reference
- result (required) — raw serialized ItemStack string. Use the GUI to produce this to avoid serialization issues.
- recipe (required for crafting types) — list of rows / ingredients; the first set = first row. For shaped recipes, entries beyond three rows are ignored.
- type (required) — recipe type. Valid values:
  - shaped
  - shapeless
  - furnace
  - blasting
  - smoking
  - campfire
  - stonecutter
- enabled — true / false. If false, recipe is not loaded at server start.
- category — grouping for GUIs/books.
- cooktime — ticks required for smelting/cooking types.
- experience — experience granted when removing cooked result (for smelting types).

### Notes:
- Per-recipe craft permission follows the pattern pintorecipes.craft.<recipe_name>.
- Craft limits and tracking are implemented separately (see SQLiteManager in source); storage/config for that is internal and not part of recipes.yml.

## Examples  
Shaped recipe (3x3)
```
my_custom_pickaxe:
  result: <serialized item stack>
  recipe:
    - "DIAMOND,DIAMOND,DIAMOND"
    - "AIR,STICK,AIR"
    - "AIR,STICK,AIR"
  type: shaped
  enabled: true
  category: tools
```
Shapeless recipe
```
berry_salad:
  result: <serialized item stack>
  recipe:
    - "APPLE"
    - "BERRY"
  type: shapeless
  enabled: true
  category: food
```
Furnace / smelting recipe
```
super_ingot:
  result: <serialized item stack>
  recipe:
    - "RAW_SUPER_ORE"
  type: furnace
  enabled: true
  cooktime: 200    # ticks
  experience: 0.7
  category: materials
```
Stonecutter (single-input)
```
polished_marble:
  result: <serialized item stack>
  recipe:
    - "MARBLE_BLOCK"
  type: stonecutter
  enabled: true
```
## Best practices
- Use the plugin GUI to create result values; manual serialization often causes issues.  
- Restart the server after changing recipes.yml to ensure consistent state.  
- If replacing vanilla recipes, create a custom recipe with the same output and use permission/limits to control access.

## Troubleshooting
- Recipe not loading: confirm enabled: true and restart server; check server logs for parse errors.  
- Invalid result payloads cause load failures — regenerate via GUI.  
- Craft limits not enforced: check startup logs for DB errors.  
