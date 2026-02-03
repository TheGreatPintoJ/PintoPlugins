<h1 align="center">PintoRecipes</h1>
<p align="center">A Spigot plugin that provides a GUI to create, edit, view, and manage custom recipes (crafting and smelting variants) with full support for item NBT and per-recipe permissions/limits.</p>

## Key features
- GUI for save, edit, show, remove and list recipes
- Supports shaped, shapeless, furnace, blasting, smoking, campfire and stonecutter recipes
- Any item may be made craftable/smeltable (including NBT)
- Optional craft limits per recipe; permission to bypass limits (`pintorecipes.craftbypass`)
- Per-recipe craft permission `pintorecipes.craft.<recipe_name>`
- An Uncrafting GUI
  - Supports switching through multiple recipes per item
  - Can uncraft using custom recipes

## Commands
- `/pintorecipe` - Aliases: `/pr` `/precipes`
- `/pintorecipes show <recipe_name>` — Open read-only GUI for a recipe
- `/pintorecipes save <recipe_name>` — Open recipe creation GUI (cancelled if both input grid and result are empty on close)
- `/pintorecipes edit <recipe_name>` — Open editable GUI for an existing recipe (same save rules as `save`)
- `/pintorecipes remove <recipe_name>` — Delete recipe from storage
- `/pintorecipes reload` — Reloads all recipes
- `/pintorecipes list` — Open GUI that lists all available recipes


## Permissions
- `pintorecipes.recipes` — use base command
- `pintorecipes.recipes.show` — show recipes
- `pintorecipes.recipes.save` — create recipes
- `pintorecipes.recipes.edit` — edit recipes
- `pintorecipes.recipes.remove` — remove recipes
- `pintorecipes.recipes.list` — open recipe list GUI
- `pintorecipes.craftbypass` — bypass craft limits and permission checks
- `pintorecipes.craft.<recipe_name>` — allow crafting of `recipe_name`

## Configuration (`recipes.yml`)
- Top-level keys are recipe identifiers (any string).
- A recipe entry contains:
  - `result` — raw serialized item (use the plugin GUI to produce correct data)
  - `recipe` — rows/ingredients for the recipe input (first set = first row)
  - `type` — recipe type: `shaped`, `shapeless`, `furnace`, `blasting`, `smoking`, `campfire`, `stonecutter`
  - `enabled` — `true`/`false` for loading at server start
  - `category` — optional grouping for GUIs/books
  - `cooktime` / `experience` — for applicable smelting recipes
- More information [here](https://thegreatpintoj.github.io/PintoPlugins/configs/PintoRecipes.html)

## Notes
- Changes generally require a server restart to guarantee consistent state.
- Use the plugin GUI to generate `result` data to avoid formatting errors.
- To restrict vanilla recipe crafting, create a custom recipe with the same output and set limits/permissions.

## Troubleshooting
- If a recipe does not appear: verify `enabled: true` and restart server.
- If a GUI action fails: check server logs for stack traces; the plugin logs load/SQL errors at startup.
- If any stack trace appears in the server logs (relating to this plugin), create an issue on the [GitHub Repo](https://github.com/TheGreatPintoJ/PintoRecipes/issues).
- If craft limits or permissions aren't enforced: confirm permission nodes on the player and plugin restart.

## Files of interest
- `recipes.yml` — stored recipes (data-folder after run)
- `crafts.db` — The SQLite database that stores player crafts
