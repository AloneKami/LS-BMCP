# LS-BMCP
# Enhancing Scalability and Solution Quality for Budgeted Maximum Coverage via Problem-Oriented Local Search

This repository contains the implementation accompanying the paper:

**Enhancing Scalability and Solution Quality for Budgeted Maximum Coverage via Problem-Oriented Local Search**

The solver is designed for the **Budgeted Maximum Coverage Problem (BMCP)**.

---

## Overview

The Budgeted Maximum Coverage Problem (BMCP) is a combinatorial optimization problem in which a subset of items must be selected under a budget constraint so as to maximize the total profit of covered elements.

This project provides a local search solver for BMCP, together with support for two input formats.

---

## Requirements

- C++ compiler with C++ support
- CMake

---

## Build

This project can be built with CMake.

```bash
mkdir build
cd build
cmake ..
make
```
---

After compilation, an executable will be generated in the build directory.

## Running

The solver is executed from the command line.

## Basic Usage

```bash
./LS-BMCP --input_type <1|2> --data_file <instance_file> [options]
```
---

### Required Arguments

- `--input_type <1|2>`
  - `1`: use the first input format
  - `2`: use the second input format

- `--data_file <instance_file>`
  - path to the input instance file

### Optional Arguments

- `--seed <int>`  
  Random seed.

- `--time_limit <int>`  
  Time limit in seconds.

- `--imax1 <int>`  
  Parameter `imax1`.

- `--imax2 <int>`  
  Parameter `imax2`.

- `--lambda <float>`  
  Parameter `lambda`.

### Example

```bash
./LS-BMCP \
  --input_type 1 \
  --data_file ./instances/585_600_0.05_2000.txt \
  --seed 1 \
  --time_limit 600 \
  --imax1 10000 \
  --imax2 500 \
  --lambda 0.9
```
---

### Input Formats

The solver supports two input formats.

### Input Type 1

The instance file should follow the format below:
```bash
m=<m> n=<n> knapsack size=<C>

The weight of <m> items_next
<w<sup>1</sup>> <w_2> ... <w_m>

The profit of <n> elements_next
<p_1> <p_2> ... <p_n>

Relation matix
<a_11> <a_12> ... <a_1n>
...
<am_1> <am_2> ... <a_mn>
```
where:

- m is the number of items,
- n is the number of elements,
- C is the knapsack capacity,
- w_i is the weight of item i,
- p_j is the profit of element j,
- a_ij = 1 means item i covers element j, otherwise a_ij = 0.
### Input Type 2

The instance file should follow the format below:
```bash
<m> <n> <line> <C>
<u1> <v1>
<u2> <v2>
...
<uline> <vline>
<w1> <w2> ... <wm>
<p1> <p2> ... <pn>
```

where:

- m is the number of items,
- n is the number of elements,
- line is the number of item-element relations,
- C is the knapsack capacity,
- each pair (u, v) means item u covers element v,
- the next line gives the weights of all items,
- the final line gives the profits of all elements.

## Output

The program prints the solution information through the solver output routine after the search procedure finishes.