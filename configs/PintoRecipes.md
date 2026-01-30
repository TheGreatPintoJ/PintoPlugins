### recipes.yml
<details>
  <summary>Default</summary>
  
  ```yaml
  netherite_sword:
    enabled: false
    type: shapeless
    category: WEAPONS
    limit: -1
    limit-type: PLAYER
    result:
      ==: org.bukkit.inventory.ItemStack
      v: 4440
      type: NETHERITE_SWORD
    recipe:
      - netherite_ingot
      - diamond_sword
  endermite_spawnegg:
    enabled: false
    type: shaped
    category: MISC
    limit: -1
    limit-type: SERVER
    result:
      ==: org.bukkit.inventory.ItemStack
      v: 4440
      type: ENDERMITE_SPAWN_EGG
    recipe:
      - left: air
        middle: ender_pearl
        right: air
      - left: ender_pearl
        middle: ender_eye
        right: ender_pearl
      - left: air
        middle: ender_pearl
        right: air
  wither_skull:
    enabled: false
    type: smoking
    category: MISC
    limit: 3
    limit-type: PLAYER
    result:
      ==: org.bukkit.inventory.ItemStack
      v: 4440
      type: WITHER_SKELETON_SKULL
    recipe: SKELETON_SKULL
  ```
</details>

The first key is whatever the name of the recipe is (defaults are endermite_spawnegg and netherite_sword)
`result` - This is the raw data of the item that spigot stores. I highly recommend leaving this be and using the commands to generate it.<br><br>
`recipe` - This is where the recipe is stored. The format of this will vary with type.<br><br>
`enabled` - Whether to load the recipe when the server starts.<br><br>
`type` - The type of the recipe.<br>
Valid options:
* `shaped` - recipe with defined shape
* `shapeless` - list of materials with no defined shape
* `furnace`, `blasting`, `smoking`, `stonecutter` - single material, single output

`category` - The category of whatever book to put the recipe in. This will show in the recipe book for the respective menu.<br>
Valid options:
* For type `shaped` or `shapeless`
  * `EQUIPMENT`
  * `BUILDING`
  * `REDSTONE`
  * `MISC`
* For type `furnace`, `blasting`, `smoking`
  * `FOOD`
  * `BLOCKS`
  * `MISC`
  
`cooktime` - How long the recipe will take to cook for cooking-related recipes in ticks (`furnace`, `blasting`, `smoking`, or `campfire`)
`experience` - How much experience the recipe will give when taken out of the furnace/container (`furnace`, `blasting`, `smoking`)

`limit` - How many of these items should be craftable (`-1` for no limit)
`limit-type` - What basis on which this limitation should apply (`SERVER`, or `PLAYER`)
