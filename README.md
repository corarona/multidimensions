# multidimensions
Licenses: code: LGPL-2.1, media: CC BY-SA-4.0  
Version: 2 

Multi dimensions
This mod adds a few dimensions to the game (you can add more)

You can find the "Dimensions teleport tool" in creative to go to them, or type "/giveme dim"
(You need the "dimensions" privilege to use it)
Teleport yourself to dimensions by point in air/blocks, or teleport other players/objects by pointing them.

There are also crafable "teleport blocks" (click to teleport, and works with mesecons)

All teleported players that not have the "dimensions" privilege will get there spawnpoin and home set in the new dimension (using "beds" and "sethome")
They cant get back unless teleporting in somehow or have/making "teleport blocks"

Player cant see or hear players from "other diamnsions" or just if they are 800 blocks away

You can change settings in the init.lua

Used settings:
unlimited_player_transfer_distance=false
player_transfer_distance=50
[Main manu[--> [Settings[ --> [Advanced Settings[ --> [Server / Singleplayer[ --> [Game]


---
# The API

everything can be nil, except the name
```lua

multidimensions.register_dimension("name",{

  ground_ores = {
    ["default:tree"] = 1000,            -- (chance) ... spawns on ground, used by trees, grass, flowers...
    ["default:stone"] = {chance=1000}, 	-- same as above
    ["default:dirt_with_snow"] = {
    	chance=5000,	     -- chance
	min_heat=10,	     -- min heat
	max_heat=40,	     -- max heat
	chunk=3,	     -- chunk size
    },
  },
  stone_ores = {},     	     -- works as above, but in stone
  dirt_ores = {},
  grass_ores = {},
  air_ores = {},
  water_ores = {},
  sand_ores = {},

  min_y = 2000,             -- dimension start (don't change if you don't know what you're doing)
  max_y = 3000,             -- dimension end (don't change if you don't know what you're doing)
  dirt_start 501,           -- when dirt begins to appear (default is 501)
  dirt_depth = 3,	    -- dirt depth
  ground_limit = 530,	    -- ground y limit (ground ends here)
  water_depth = 8,	    -- depth fron ground and down
  enable_water = nil,       -- (nil = true)
  terrain_density = 0.4,    -- or ground density
  flatland = nil,           -- (nil = false)
  teleporter = nil,         -- (nil = true) dimension teleporter
  gravity = 1,		    -- (1 = default) dimension gravity
  
  stone = "default:stone",
  dirt = "default:dirt",
  grass = "default:dirt_with_grass",
  air = "air",
  water = "default:water_source",
  sand = "default:sand",
  bedrock = "multidimensions:bedrock", -- at dimension edges
  
  map = {
    offset = 0,
    scale = 1,
    spread = {x=100,y=18,z=100},
    seeddiff = 24,
    octaves = 5,
    persist = 0.7,
    lacunarity = 1,
    flags = "absvalue",
   },
   
   craft = { -- teleport craft recipe
	{"default:obsidianbrick", "default:steel_ingot", "default:obsidianbrick"},
	{"default:wood","default:mese","default:wood",},
	{"default:obsidianbrick", "default:steel_ingot", "default:obsidianbrick"},
   }
})
```
