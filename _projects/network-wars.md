---
layout: page
title: Network Wars
description: RTS about building efficient networks made in C++ with SDL
img: assets/img/network-wars-preview.gif
importance: 1
category: Gamedev
---

RTS on a node graph.
Build efficient networks to better transport troops to the front, recognize bottlenecks in enemy's network to detect and exploit weak points.

### Techincal Highlights
- Made in C++ with SDL.
- Layered architecture inspired by the TCP/IP model: Units only communicate with Links, Links only communicate with Nodes.
- Node and Link capacity mechanic inspired by locks and mutexes.
    - For an item to enter a node, it reserves space at the link and the destination node
    - After it's finished traversing, the spaces are freed.
- A* graph pathfinding for setting directions of links en-masse based on player input.
- Event driven computation instead of busy-waiting for optimization.
    - Nodes and edges have limited capacity, and they notify their neighbors when a change happens.
    - Player input processing using SDL events.
- Matrix representation of transforms to enables proper parenting of game actor transforms.
    - Optimized with the dirty bit pattern to avoid expensive matrix operations.
- Collisions using bounding boxes.
    - Optimized by grouping relevant colliders into separate containers and only checking ones that fit the context (ex. player mouse input, unit interactions)