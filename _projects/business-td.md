---
layout: page
title: Business Tower Defense
description: Tower defense game about maximizing profits. Solo project.
img: assets/img/businessTD_preview.gif
importance: 4
category: Gamedev
---

<img src="/assets/img/businessTD_preview.gif" alt="game_image">
<br>
<br>
<a href="https://github.com/dwlee0802/BusinessTD" target="_blank">GitHub</a>

### Overview
- Tower Defense meets Business Management. 
- Mine crystals on an alien planet while fighting off the hostile inhabitants. 
- Sell crystals to earn money.
- Determine whether to invest further or cash out.
    - Enemy waves increases over time, requiring more investment for security.
    - Cash out and retreat when costs exceeds profits.

### Techincal Highlights
**Scope**
- Made in Godot Engine 4 with GDScript
- Total lines of code: 2577

**Procedural Generation**
- The game map is generated dynamically using Perlin noise.
    - Different thresholds for different terrain types.
    - Multiple noise values are generated for different cell type layers.
        - For example: wall/floor, mud/plain, mineral/none
- Validates enough edge cells are valid spawn points and regenerates if invalid.

**Enemy unit pathfinding**
- Needed to support hundreds of units pathfinding to nearest player structure through a complex terrain generated with Perlin-noise on a 250x250 square grid.
- Optimized through caching the A* paths at the edge cells that the enemies spawn on so we don't have to recalculate for every unit.
- Cell is disabled as a spawn candidate if no path exists.

**Graph Connectivity Checking with BFS**
- Player structures in the game needs to be connected to a power source to be active.
- Set up the power supply checking functionality using Breadth First Search
    - Each building recurviely invokes the connection check of thoese inside its supply range by collision.
    - Only gets triggered when a new building is placed/removed to reduce unnecessary computation. 