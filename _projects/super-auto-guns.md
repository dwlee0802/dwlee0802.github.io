---
layout: page
title: Super Auto Guns
description: WW2 themed Auto Battler, inspired by Super Auto Pets. Solo project.
img: assets/img/super-auto-guns-preview.gif
importance: 2
category: Gamedev
---

<img src="/assets/img/super-auto-guns-preview.gif" alt="game_image">
<br>
<a href="https://github.com/dwlee0802/SuperAutoGuns" target="_blank">GitHub</a>

#### Simulation
- The battles are processed in 'ticks'. Unit movement and attack all take a certain number of ticks to actually fire.
- One round consists of unit placement, and simulation. Each player places their units on the battlefield, and when both are finished the battle commences.

#### Units
- Units have two health points, one for Hit Points and one for Morale.
    - When a unit runs out of HP, it is removed from the battlefield.
    - When a unit runs out of morale, it cannot do anything for one tick.
- All of their actions are done automatically., and the player can influence the outcome of the battle through strategically. placing units on the battlefield based on predicting how the battle will turn out through the ticks.
- Movement
    - Units must not have a tile in front of them for them to attack.
    - When a unit has empty space in the column in front of them, they move there.

#### Battlefield
- The attacking side's must traverse no man's land in the column, while the defenders don't have to and can start ticking for their attacks immediately.
- Difference tiles have different terrain types, which influence the movement tick cost of units and attack ranges. Exampes are roads reduce movement cost by one tick, and hills increase it by one but increases attack range by one if a unit is on it.