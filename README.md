# Constraint Based 3D Self Assembly and Minimal Complexity Inverse Design

## A Completed Computational Modeling Notebook Inspired by Bio Inspired Nanotechnology

This repository contains a Python based computational modeling notebook inspired by the paper *Designing the Self Assembly of Arbitrary Shapes Using Minimal Complexity Building Blocks* by Joakim Bohlin, Andrew J. Turberfield, Ard A. Louis, and Petr Šulc.

The project explores a simplified version of the paper’s main idea: a target self assembled structure does not always require every building block to be unique. In some cases, the same structure can be represented using fewer reusable building block species, as long as the interaction rules still preserve enough information to guide the assembly toward the intended shape.

This notebook is a completed second stage extension of an earlier minimal complexity self assembly model. The earlier notebook introduced the basic idea of simplified self assembly and reduced building block complexity. This final notebook extends that idea into a more complete 3D computational prototype using voxel based target shapes, adjacency graphs, reduced design strategies, constraint style validation, stochastic assembly testing, off target risk analysis, and final strategy comparison.

This is a student research and learning project focused on understanding the computational design logic behind minimal complexity self assembly. It does not attempt to reproduce the full scientific pipeline from the paper, but it builds a smaller graph based, constraint inspired, and stochastic modeling framework to study the tradeoff between simplicity and reliability.

---

## Project Motivation

Self assembly is an important idea in biological and bio inspired systems. In nature, complex structures often form through local interactions between smaller components. Bio inspired nanotechnology uses similar ideas to design programmable structures from components such as DNA, RNA, proteins, nanoparticles, or other nanoscale building blocks.

The paper that inspired this project studies how arbitrary shapes can be designed using different levels of component complexity. At one extreme, every building block in the final structure is unique. This is called a fully addressable design. At the other extreme, the structure is designed using a smaller number of reusable building block species that can still define the target assembly.

This notebook uses that idea as the foundation for a simplified computational model. The goal is to understand how target shapes can be represented, how building block species can be reused, how compatibility rules can be checked, and why reduced complexity can sometimes introduce ambiguity or off target assembly risk.

The project is motivated by the idea that computational modeling can help explain design tradeoffs before moving toward more advanced simulation methods. Instead of only summarizing the paper, this notebook builds a working Python prototype that tests related ideas through code, tables, plots, and visual assembly examples.

---

## Research Question

The main question explored in this notebook is:

Can a target 3D structure be represented using fewer unique building block species while still preserving reliable assembly behavior?

This question connects computer science concepts such as graph representation, constraint based reasoning, stochastic simulation, local rule validation, and design optimization with bio inspired systems and programmable self assembly.

---

## What This Notebook Does

The notebook builds a simplified 3D self assembly modeling workflow in Python.

It begins by representing target shapes as voxel based structures. Each occupied voxel position is treated as one building block location in the final assembled structure. Each face sharing neighbor relationship between voxels is treated as a required bond.

The notebook then compares different design strategies for the same target shapes. A fully addressable design assigns a unique building block species to every voxel position. A strict reduced design reuses species when voxel positions have the same local patch pattern in the same global directions. A rotation aware reduced design allows species to be reused when local patch patterns are equivalent under cube rotations.

After comparing design complexity, the notebook checks whether the reduced designs remain rule consistent. It tests whether patch assignments exist, whether compatibility relationships are symmetric, and whether any patch color is forced to bind to multiple different partners.

The notebook then runs simplified stochastic assembly tests. These tests ask whether the target shape can form under target guided growth and whether the same design rules could create incorrect or overgrown structures under free growth. This helps show that reducing the number of species is not automatically enough. A reduced design must also preserve enough specificity to avoid incomplete, incorrect, ambiguous, or off target assemblies.

Finally, the notebook creates a final comparison dashboard and capstone conclusion. The notebook ends as a completed computational prototype rather than as a future work proposal.

---

## Main Concepts Used

The project uses the following computational ideas:

- 3D voxel based target representation
- Local adjacency and bond extraction
- Graph based structure analysis
- Fully addressable design as a high complexity baseline
- Strict reduced design using local patch signatures
- Rotation aware reduced design using cube rotation equivalence
- Reusable building block species
- Patch compatibility rules
- Constraint style validation
- Stochastic target guided assembly testing
- Free growth off target stress testing
- Assembly success and failure mode analysis
- Species reduction analysis
- Design quality comparison
- Final dashboard based strategy ranking
- Interpretation of the tradeoff between simplicity and reliability

---

## Connection to the Original Paper

The original paper uses a more advanced scientific pipeline. It formulates the inverse design problem using Boolean satisfiability, scans possible combinations of species and patch colors, tests candidate solutions using stochastic polycube assembly, and studies selected designs using patchy particle molecular dynamics simulations. The paper also discusses possible realization through DNA nanostructures using coarse grained DNA simulation tools.

This repository does not reproduce those full methods.

Instead, it focuses on the conceptual and computational layer of the problem. It uses simplified Python models to understand why minimal complexity design is useful, why fully addressable designs are expensive, why reduced designs must still be validated, and why assembly behavior matters in addition to species count.

The notebook captures the following ideas from the paper in simplified form:

- target structures can be represented as connected arrangements of building blocks,
- fully addressable designs provide a maximum complexity baseline,
- reduced designs can reuse building block species,
- interaction rules must be specific enough to guide assembly,
- stochastic testing can reveal whether a design is likely to assemble correctly,
- compact rule sets must be checked for possible off target behavior.

This makes the notebook a computational bridge toward the inverse design logic used in the original research.

---

## Target Shapes Tested

The notebook tests multiple simplified 3D target structures:

1. Solid 2 x 2 x 2 cube
2. 3D L shape
3. Staircase structure
4. Hollow 3 x 3 x 3 cube shell
5. Wireframe 3 x 3 x 3 cube

These shapes were selected because they represent different levels of geometric and connectivity complexity. Some structures are compact, some are branched, and some contain shell or wireframe like geometry. This allows the notebook to compare how target geometry affects species reduction, patch assignment, assembly success, and off target risk.

---

## Design Strategies Compared

The notebook compares three main design strategies.

### Fully Addressable Design

In the fully addressable design, every voxel position receives its own unique building block species. Every required bond receives its own unique complementary patch color pair.

This design is easy to understand and highly specific, but it requires the largest number of unique building blocks.

### Strict Reduced Design

In the strict reduced design, voxel positions are grouped together when they have the same local patch pattern in the same global directions.

For example, two voxels with active connections on the same faces can share the same building block species. This reduces the number of unique species, but it does not account for rotated versions of the same local pattern.

### Rotation Aware Reduced Design

In the rotation aware reduced design, voxel positions can share a species if their local patch patterns are equivalent under cube rotations.

This allows the notebook to reuse geometrically similar building blocks even when they appear in different orientations. This strategy usually gives stronger species reduction than the strict reduced design.

---

## Notebook Structure

The notebook is organized into the following steps:

### Step 1: Project Setup, Research Framing, and Notebook Goals

The notebook begins by importing required libraries, setting a random seed, preparing an output folder, and explaining the purpose of the project. This step frames the notebook as a second stage extension of the earlier minimal complexity self assembly model.

### Step 2: Define Simplified 3D Voxel Target Shapes

Multiple 3D target structures are defined using voxel coordinates. These include a solid cube, 3D L shape, staircase, hollow cube shell, and wireframe cube.

### Step 3: Build Adjacency and Bond Structure

Each target shape is converted into a connectivity structure. Each voxel is treated as a building block position, and each face sharing neighbor relationship becomes a required bond.

### Step 4: Build the Fully Addressable Design

A maximum complexity baseline is created for each target shape. Every voxel gets a unique species and every required bond gets a unique complementary patch color pair.

### Step 5: Build a Strict Reduced Design

The notebook groups voxels into reusable species when they have identical local patch signatures in the same global directions. This tests how much component reuse is possible without considering rotation equivalence.

### Step 6: Build a Rotation Aware Reduced Design

The notebook improves the reduction strategy by grouping local patch signatures that are equivalent under cube rotations. This allows more reusable building block species while still preserving local geometric structure.

### Step 7: Constraint Style Validation of Design Strategies

Each design strategy is checked for simplified rule consistency. The notebook checks for missing patch assignments, asymmetric compatibility relationships, and ambiguous patch colors with multiple possible partners.

### Step 8: Simplified Stochastic Assembly Test

Repeated target guided stochastic assembly trials are run for every target shape and design strategy. The notebook measures assembly success rate, number of attempts, final assembled fraction, and failure reasons.

### Step 9: Visual Assembly Snapshots

The notebook generates 3D visual assembly snapshots. These figures show seed states, partial growth, and final assembled or failed structures, making the assembly process easier to understand visually.

### Step 10: Off Target Assembly Risk Check

The notebook performs a stricter free growth stress test. Instead of only allowing growth along the intended target bonds, the simulation uses the patch compatibility rules to test whether the design can create incorrect or overgrown structures.

### Step 11: Final Comparison Dashboard

The notebook combines species reduction, constraint validity, assembly success, off target risk, and overall prototype score into final dashboard tables and visualizations. This step provides the main strategy comparison results.

### Step 12: Conclusive Research Interpretation

The notebook turns the final dashboard results into written interpretation. It summarizes the main quantitative takeaways, shape by shape conclusions, limitations, and broader research implications.

### Step 13: Final Capstone Summary and Completed Contribution Statement

The notebook ends with a final capstone conclusion. This section summarizes what the notebook completed and presents it as a self contained computational prototype rather than an unfinished future work plan.

---

## Key Outputs

The notebook generates several important outputs:

- 3D voxel visualizations of all target shapes
- Bond network visualizations
- Voxel degree distribution plots
- Fully addressable species and patch rule tables
- Strict reduced species assignment tables
- Rotation aware species assignment tables
- Compatibility validation summaries
- Constraint issue tables
- Stochastic assembly success rate plots
- Assembly growth traces
- 3D assembly snapshot figures
- Free growth off target outcome plots
- Off target overgrowth risk summaries
- Final dashboard heatmaps
- Complexity versus reliability scatter plots
- Final best strategy summary tables
- Final capstone conclusion files

The notebook also saves several output files into a local folder called:

self_assembly_outputs

These outputs can be reused in a GitHub README, meeting discussion, or future presentation.

---

## Technologies Used

This project uses:

- Python
- Google Colab
- Jupyter Notebook
- NumPy
- Pandas
- Matplotlib
- NetworkX
- IPython Markdown display tools

---

## How to Run

Open the notebook in Google Colab or Jupyter Notebook.

The main notebook file is:

Constraint_Based_3D_Self_Assembly_and_Minimal_Complexity_Inverse_Design.ipynb

Install or import the required Python libraries:

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import itertools
import random
import math
import os
import textwrap
from collections import defaultdict, Counter, deque

NetworkX is optional but useful for graph based visualizations:

import networkx as nx

Then run the notebook cells in order from Step 1 through Step 13.

---

## Main Result

The main result of this project is that reduced complexity self assembly can be studied through a transparent computational pipeline.

The notebook shows that fully addressable designs are reliable and easy to specify, but they require the largest number of unique building block species. Reduced strategies can lower the number of species by reusing local building block patterns. Rotation aware reduction is especially useful because it identifies reusable geometric patterns even when they appear in different orientations.

However, the notebook also shows that reducing the number of species is not automatically enough. A reduced design must still be checked for compatibility conflicts, target assembly success, and off target growth risk.

The most important conclusion is:

A smaller building block library is useful only when it still preserves enough specificity to assemble the intended target and avoid unintended structures.

---

## Why This Project Is Useful

This project is useful because it demonstrates a complete computational modeling workflow for a scientific design problem.

It shows how a Python notebook can be used to explore ideas from bio inspired nanotechnology, self assembly, and inverse design without immediately needing to implement a full molecular simulation pipeline.

The project is also useful because it turns a research paper into an understandable computational experiment. Instead of only summarizing the paper, the notebook builds a simplified working model that tests related ideas through code, tables, simulations, and visualizations.

The notebook demonstrates technical work across multiple areas:

- data structure design,
- graph representation,
- geometric reasoning,
- stochastic simulation,
- model comparison,
- scientific visualization,
- result interpretation.

---

## Sustainability Connection

Although this project is inspired by self assembly and bio inspired nanotechnology, it also connects to sustainability at a broader design level.

If future programmable materials or nanoscale structures can be designed with fewer unique components, this may reduce synthesis complexity, material preparation burden, design trial and error, and experimental cost. Computational screening can also help identify promising designs before physical fabrication, which may reduce wasted laboratory time and resources.

This project does not claim to produce a direct sustainability application. Instead, it shows how efficient computational design methods could support future work in resource efficient materials, environmental sensing, programmable structures, and low waste design workflows.

---

## Limitations

This notebook is a simplified computational prototype.

It does not perform:

- full SAT based inverse design,
- molecular dynamics simulation,
- DNA origami modeling,
- sequence design,
- thermodynamic modeling,
- experimental validation,
- physical patchy particle simulation.

The stochastic assembly and free growth tests are simplified models intended to compare design strategies at a conceptual level. They are not substitutes for molecular simulation or experimental testing.

The value of the notebook is that it clearly demonstrates the computational logic of the design tradeoff and creates a foundation for understanding more advanced inverse design methods.

---

## Repository Files

This repository includes the following notebook files:

Minimal_Complexity_Self_Assembly_A_Computational_Modeling_Notebook_Inspired_by_Bio_Inspired_Nanotechnology.ipynb

This notebook contains the initial simplified self assembly model.

Constraint_Based_3D_Self_Assembly_and_Minimal_Complexity_Inverse_Design.ipynb

This notebook contains the completed second stage 3D extension with constraint style validation, stochastic assembly testing, off target analysis, and final dashboard comparison.

---

## Academic Inspiration

This project was inspired by:

Bohlin, J., Turberfield, A. J., Louis, A. A., and Šulc, P.

*Designing the Self Assembly of Arbitrary Shapes Using Minimal Complexity Building Blocks.*

The original paper studies the design of arbitrary self assembled structures using minimal numbers of building block species and interaction types. This repository is a simplified student project built to understand and computationally explore the design ideas behind that work.

---

## Author

Tejas Sharma

Computer Science Student at Arizona State University

Interested in computational modeling, sustainability, bio inspired systems, data science, and scientific computing.
