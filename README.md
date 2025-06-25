# Data Structures and Algorithms
# C Satellite Network

## Table of Contents
- [Overview](#overview)
- [Network Base Input](#network-base-input)

## Overview

This project models a network of satellites as a **binary tree**, where satellites are interconnected through direct communication links.
A **root satellite**, positioned closest to Earth’s atmosphere, serves as the communication hub for all other satellites in the network.
The network supports basic and simplified operations, such as

### Communication Frequency & Positioning

Each satellite is uniquely defined by its name. From a functional point of view, every satellite has a **reporting frequency**,
which indicates how often it transmits data. To optimise communication:

- Satellites that report **more frequently** are placed **closer to Earth** (closer to the root).
- Satellites with **lower frequencies** are positioned **farther away** in the binary tree.
- Each connection between two satellites has a **fixed distance K**.

To achieve this structure, **intermediate (linking) satellites** may be introduced. These are not primary satellites but serve to maintain the binary tree structure and ensure network connectivity.

### Binary Tree Construction Rules

To build the tree, the following process is applied iteratively:

1. Identify the two satellites with the **lowest reporting frequencies**.
2. Create a new link satellite as their **parent**:
   - Its frequency is the **sum** of the two children’s frequencies.
   - Its name is the **concatenation** of the left child’s name and the right child’s name.
3. Insert this new satellite into a **Min-Heap** based on frequency.
4. Repeat the process until all satellites are connected under a single binary tree structure.

## Network Base Input

Each task that the program can perform first requires providing the necessary data to build the binary tree as described in the above section.
This information is found at the beginning of a file named `tema2.in` found in the working directory. Any input required by the tasks will be 
added after these essential lines. The format is as follows:

1. **First line:**
   An integer `N` representing the number of primary satellites in the network
2. **Next N lines:**
   Separated by exactly one space, the reporting frequency and name of the satellites
   > Important: The name of each primary satellite cannot exceed 16 characters

## Base Tasks

The implemented program can handle simple tasks such as building and printing the binary tree as a routine check and tracking down satellites
based on a codified message. Each of these operations requires a properly built binary tree beforehand, respecting the above criteria. This part of
the implementation was handled separately before undertaking the actual tasks. 
Below are the four possible basic operations for this satellite network:

### Printing

Displays the satellites in the binary tree level by level, starting from the root and using breadth-first traversal. 
Each level will be printed on one line. For every satellite, prints the two identifiers in this format: `<frequency>-<name>`.
This operation does not require extra information about the network.

### Message Sender Identification

The space agency receives messages from one or more satellites, with the source(s) codified as a bitstring. 
The program finds the source(s) of each message, using the following rules:
- Each **`0`** in the bitstring represents a **left move** in the binary tree
- Each **`1`** in the bitstring represents a **right move** in the binary tree
- If a leaf is encountered when tracking down the source of a signal and the code is not over,
  the corresponding satellite is the first source. The other(s) can be found by resuming the search from the root.

For each decoded bitstring, the program prints on the same line the names of found source satellites, separated by one space.

Required input for this operation (appended to the `tema2.in` file):

1. **First added line:**
   An integer `N` representing the number of codes transmitted to the space agency
2. **Next N added lines:**
   The bitstrings that represent the codes 
   > Important: The length of each bitstring cannot exceed 1000 digits

## 
