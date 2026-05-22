# Minimal Complexity Self Assembly

## A Computational Modeling Notebook Inspired by Bio Inspired Nanotechnology

This repository contains a Python based computational modeling notebook inspired by the paper *Designing the Self Assembly of Arbitrary Shapes Using Minimal Complexity Building Blocks* by Joakim Bohlin, Andrew J. Turberfield, Ard A. Louis, and Petr Šulc.

The project explores a simplified version of the paper’s main idea: a target self assembled structure does not always require every building block to be unique. In some cases, the same structure can be represented using fewer reusable building block types, as long as the interaction rules still preserve enough information to guide the assembly toward the intended shape.

This is a student learning project focused on understanding the computational design logic behind minimal complexity self assembly. It does not attempt to reproduce the full scientific pipeline from the paper, but it builds a smaller graph based and stochastic modeling framework to study the tradeoff between simplicity and reliability.

---

## Project Motivation

Self assembly is an important idea in biological and bio inspired systems. In nature, complex structures often form through local interactions between smaller components. Bio inspired nanotechnology uses similar ideas to design programmable structures from components such as DNA, RNA, proteins, or other nanoscale building blocks.

The paper that inspired this project studies how arbitrary shapes can be designed using different levels of component complexity. At one extreme, every building block in the final structure is unique. At the other extreme, the structure is designed using the minimum number of reusable building block types that can still define the target assembly.

This notebook uses that idea as the foundation for a simplified computational model. The goal is to understand how target shapes can be represented, how building block species can be reused, and why reduced complexity can sometimes introduce ambiguity during assembly.

---

## Research Question

The main question explored in this notebook is:

Can a target shape be represented using fewer distinct building block types while still preserving enough interaction information to assemble the intended structure?

This question connects computer science concepts such as graph representation, constraint based reasoning, stochastic simulation, and optimization with bio inspired systems and programmable self assembly.

---

## What This Notebook Does

The notebook builds a simplified self assembly modeling workflow in Python.

It begins by representing target shapes as grid based graphs. Each occupied grid position is treated as a building block, and each connection between neighboring positions is treated as a required interaction.

The notebook then compares different design strategies for the same target shapes. A fully addressable design assigns a unique building block species to every position. A reduced complexity design reuses building block species when positions share similar local connection patterns.

After comparing design complexity, the notebook tests whether reduced designs can still assemble correctly using a simplified stochastic assembly model. This helps show that reducing the number of species is not automatically enough. A design must also preserve enough specificity to avoid incomplete, incorrect, or ambiguous assemblies.

Finally, the notebook introduces an orientation aware reduced model, where reusable building blocks can appear in different rotated forms while still preserving local geometric constraints.

---

## Main Concepts Used

The project uses the following computational ideas:

- Graph based representation of target structures
- Fully addressable design as a high complexity baseline
- Reduced complexity design using reusable building block species
- Local connection patterns
- Rotation aware species grouping
- Stochastic assembly testing
- Design quality comparison
- Interpretation of the tradeoff between simplicity and reliability

---

## Connection to the Original Paper

The original paper uses a much more advanced research pipeline. It formulates the inverse design problem using Boolean satisfiability, scans possible combinations of species and patch colors, tests candidate solutions using stochastic polycube assembly, and studies selected designs using patchy particle molecular dynamics simulations. The paper also discusses possible realization through DNA nanostructures using coarse grained DNA simulation tools.

This repository does not reproduce those full methods.

Instead, it focuses on the conceptual layer of the problem. It uses simplified Python models to understand why minimal complexity design is useful, why fully addressable designs are expensive, and why reduced designs must still be checked for assembly reliability.

---

## Sustainability Connection

Although the original paper is focused on programmable self assembly and bio inspired nanotechnology, the design idea has a broader connection to sustainability.

If future nanoscale materials, sensing systems, or engineered structures can be designed with fewer unique components, this may reduce material complexity, synthesis burden, and trial and error during experimental development. Computational modeling can also help researchers screen designs before physical fabrication, which may save time, resources, and laboratory effort.

This type of thinking could eventually support sustainability related applications such as environmental sensing, sustainable materials, resource efficient manufacturing, and low waste design workflows.

In this project, sustainability is not treated as a direct experimental result. Instead, it is presented as a broader motivation for why efficient computational design methods may matter in future scientific and engineering systems.

---

## Notebook Structure

The notebook is organized into the following steps:

### Step 1: Representing a Target Shape as a Graph

Target shapes are represented as grid based structures. Each occupied position becomes a node, and each neighboring connection becomes an edge.

### Step 2: Building a Fully Addressable Design

Each position in the target shape is assigned a unique building block species. Each required connection receives a unique interaction label. This creates the high complexity baseline.

### Step 3: Creating a Reduced Complexity Design

Positions with similar local connection patterns are grouped into reusable building block species. This reduces the number of distinct species required to describe the shape.

### Step 4: Comparing Fully Addressable and Reduced Designs

The notebook compares the number of species used in the fully addressable and reduced designs.

### Step 5: Interpreting the Complexity Reduction

The results are interpreted to explain how component reuse can reduce design complexity.

### Step 6: Testing Whether the Reduced Design Is Ambiguous

A simplified stochastic assembly model tests whether the reduced design still assembles into the intended target shape.

### Step 7: Visualizing Example Assembly Outcomes

Individual assembly outcomes are visualized to show successful, incomplete, off target, or ambiguous growth.

### Step 8: Creating a Simple Design Quality Score

A simplified score combines species reduction with target shape success rate to compare design quality.

### Step 9: Adding Orientation Awareness to the Reduced Design

The reduced design is improved by including local geometric orientation. This helps show why directionality and compatibility rules matter in self assembly.

### Step 10: Limitations and Connection to the Original Paper

The notebook explains how the simplified model differs from the original research pipeline.

### Step 11: Final Conclusion

The project concludes by summarizing the tradeoff between design simplicity and assembly reliability.

---

## Technologies Used

This project uses:

- Python
- Google Colab
- NumPy
- Pandas
- Matplotlib
- NetworkX

---

## How to Run

Open the notebook in Google Colab or Jupyter Notebook.

Install or import the required Python libraries:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import networkx as nx
