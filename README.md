# Data Structures and Algorithms
# C Satellite Network

## Table of Contents
- [Overview](#overview)

## Overview

This project models a network of satellites as a **binary tree**, where satellites are interconnected through direct communication links.
A **root satellite**, positioned closest to Earth’s atmosphere, serves as the communication hub for all other satellites in the network.
The network supports basic and simplified operations, such as

### Communication Frequency & Positioning

Each satellite is uniquely defined by its name. From a functional point of view, every satellite has a **reporting frequency**,
which indicates how often it transmits data. To optimise communication:

- Satellites that report **more frequently** are placed **closer to Earth** (i.e., nearer to the root).
- Satellites with **lower frequencies** are positioned **farther away** in the binary tree.
- Each connection between two satellites has a **fixed distance K**.

To achieve this structure, **intermediate (linking) satellites** may be introduced. These are not primary satellites but serve to maintain the binary tree structure and ensure network connectivity.

### Binary Tree Construction Rules

To build the tree, the following process is applied iteratively:

1. **Identify the two satellites** with the **lowest reporting frequencies**.
2. **Create a new link satellite** as their **parent**:
   - Its frequency is the **sum** of the two children’s frequencies.
   - Its name is the **concatenation** of the left child’s name and the right child’s name.
3. **Insert** this new satellite into a **Min-Heap** based on frequency.
4. **Repeat** the process until all satellites are connected under a single binary tree structure.
