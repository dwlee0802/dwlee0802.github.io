---
layout: page
title: Graph Econ Game
description: Build efficient production networks to meet your production quota. Solo project.
img: assets/img/graph-econ-game.jpg
importance: 5
category: Gamedev
---

<img src="/assets/img/graph-econ-game.jpg" alt="game_image">
<br>
<br>

#### Overview
- You are a governor appointed by the central government.
- The nation is at war, and you are given a quota to produce military supplies.
- If you fail to meet them, you will be fired.
- Set up item buses, hubs, and buffers for efficient use of the supply network.
    - Building new roads is expensive - reuse as much as possible
- Set up routing between nodes for different good types.
- Balance between civilian and military production for funds/quota.

#### Techical Highlights
**Scope**
- Made in Godot Engine 4 with GDScript
- Total lines of code: 3315

**Mutually exclusive link use**
- Items take up one capacity of links between nodes.
- If the capacity is full, other items are blocked from traversing it.
- I had to carefully coordinate the capacity acquiring and freeing, similar to locks.
    - Items can enter and take up capacity only after it gets permission to enter from a link.
    - The link gives permission when it has enough capacity and the destination node has space
        - When it grants permission, it increments its capacity usage by one.
    - When the item gets permission, it traverses the link, and notifies the link when its done.
        - Node ownership of the item is also changed when permission is granted.
    - Whenever a link clears up, meaning it went from occupied to available, it notifies the two nodes at each end of it.
    - Additionally, when a node is cleared up, it notifies the links it is connected to.
    - When a node is notified that a link it is connected to has changed from occupied to available, it notifies the waiting items in its queue.
    - When an item is notified by its host node, it tries to ask for permission again from links.
- This allowed not only better coordination and for occupancy changes to cascade throughout the graph, but also for busy-waiting for items to be removed, saving computation power.