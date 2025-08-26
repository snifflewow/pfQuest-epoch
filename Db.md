````markdown
# Db structure

Short explanation of each file 

Short value explanation:
fac -- Faction by letter:  A (Alliance), H (Horde), AH (both)
U -- Unit 
O -- Object

---

## `db/`

### `quests-epoch.lua`

Contains quest information, including start and end points, level, and the next quest in a chain.

**Format**

```lua
[QUESTID#] = {
  ["start"] = {
    ["U"] = { UNITID# },
  },
  ["end"] = {
    ["U"] = { UNITID# },
  },
  ["lvl"] = quest level,
  ["min"] = required level,
  ["next"] = next quest id after this one,
},
```

**Example**

```lua
[27246] = {
  ["start"] = {
    ["U"] = { 14624 },
  },
  ["end"] = {
    ["U"] = { 46164 },
  },
  ["lvl"] = 50,
  ["min"] = 50,
  ["next"] = 27242,
},
```

### `units-epoch.lua`

Contains unit information such as level, ID, coordinates, and faction.
Both quest npc's and mobs are in this file.

**Format**

```lua
[UNITID#] = {
  ["coords"] = {
    [1] = { x, y, zoneid, respawn },
    [2] = { x, y, zoneid, respawn },
  },
  ["fac"] = "faction", 
  ["lvl"] = "level",
},
```

**Example**

```lua
[61100] = {
  ["coords"] = {
    [1] = { 96.5, 66.8, 440, 280 },
    [2] = { 52.7, 80.7, 5121, 280 },
  },
  ["fac"] = "AH",
  ["lvl"] = "55",
},
```

### `items-epoch.lua`

Contains item information, including which units (`"U"`) and objects (`"O"`) they drop from. An item can drop from multiple units or objects.

**Format**

```lua
[ITEMID#] = {
  ["O"] = {
    [OBJECTID#] = drop%number, -- first object it drops from
    [OBJECTID#] = drop%number, -- second object it drops from
  },
  ["U"] = {
    [UNITID#] = drop%number, -- first npc it drops from
    [UNITID#] = drop%number, -- second npc it drops from
  },
},
```

**Example**

```lua
[4606] = {
  ["O"] = {
    [153462] = 4.17,
  },
  ["U"] = {
    [3] = 4.73,
    [48] = 4.55,
  },
},
```

### `areatrigger-epoch.lua`

Contains area trigger locations for exploration quests.

**Format**
```lua
[AREATRIGGERID#] = {
  ["coords"] = {
    [1] = { x, y, zoneid },
  },
},
````

**Example**

```lua
[1] = {
  ["coords"] = {
    [1] = { 35.8, 62.1, 11 },
  },
},
```

### `objects-epoch.lua`

Contains object information, such as coordinates and ID.

**Format**

```lua
[OBJECTID#] = {
  ["coords"] = {
    [1] = { x, y, zoneid, respawn },
  },
},
```

**Example**

```lua
[34] = {
  ["coords"] = {
    [1] = { 40.6, 17, 40, 2700 },
  },
},
```

### `meta-epoch.lua`

Contains meta-relations, such as lists of game objects that are ores, unit IDs that are flight points, etc.

**Format**

```lua
["chests"] = {
  [-CHESTID#] = 0,
},
["flight"] = {
  [UNITID#] = "FACTIONLETTER", 
  [UNITID#] = "FACTIONLETTER",
  [UNITID#] = "FACTIONLETTER",
},
["rares"] = {
  [UNITID#] = LEVEL,
  [UNITID#] = LEVEL,
},
```

**Example**

```lua
["chests"] = {
  [-3000248] = 0,
  [-3000247] = 0,
},
["flight"] = {
  [352] = "A",
  [1233] = "AH",
  [1387] = "H",
},
["rares"] = {
  [61] = 11,
  [79] = 10,
},
```

### `minimap-epoch.lua`

Contains minimap scale factors for specific areas, which helps to correctly display dots on the minimap inside buildings.

**Format**

```lua
[MAPID] = { xsize, ysize },
```

**Example**

```lua
[25] = { 711.56, 468.68 },
```


### `quests-itemreq-epoch.lua`

Contains a list of items required for a quest that are usable in the floating quest log UI.

### `refloot-epoch.lua`

Contains item requirements for specific quests, such as listing all anvil objects for the "Broken Tools" quest.


### `zones-epoch.lua`

Contains information about zones and their positions on maps, as well as the maps themselves.

**Format**
(No format or example provided in the original text)

-----

## `enUS/` (Localization Folder)

This folder contains localized names and information.

### `items-epoch.lua`

Contains item IDs and their corresponding names.

**Format**

```lua
[ITEMID#] = "ITEMNAME",
```

### `objects-epoch.lua`

Contains object IDs and their corresponding names.

**Format**

```lua
[OBJECTID#] = "OBJECTNAME",
```

### `professions-epoch.lua`

Contains IDs and names for custom professions only.

**Format**

```lua
[PROFESSIONID#] = "PROFESSIONNAME",
```

### `quests-epoch.lua`

Contains quest IDs and their title, objective, and description.

**Format**

```lua
[QUESTID#] = {
  ["T"] = "QUESTTITLE",
  ["O"] = "QUESTOBJECTIVE",
  ["D"] = "QUESTDESCRIPTION",
},
```

### `units-epoch.lua`

Contains unit IDs and their corresponding names.

**Format**

```lua
[UNITID#] = "UNITNAME",
```

### `zones-epoch.lua`

Contains zone IDs and their corresponding names.

**Format**

```lua
[ZONEID#] = "ZONENAME",
```

```
```

