# Evolutionary Agent Simulation
A simple genetic-algorithm & neural-network based agent simulation on a 2D grid.

![Descriptive alt text](Center.gif)
![Descriptive alt text](Corner.gif)

## Key Concepts

- **Genome**  
  - Represented as a fixed-length hex string (GENOME_LEN = WEIGHTS_COUNT × 4 hex digits).  
  - Each 4-hex group → one 16-bit unsigned integer → weight in [–1, +1].

- **Neural “Brain”**  
  - **Inputs (SENSORS)**:  
    - 8 cells in ring 1 + 16 cells in ring 2 around the agent  
    - Age (normalized), X/Y position (normalized), random bias  
  - **Architecture**: 4 fully-connected layers of size 16 → tanh activation → 4 outputs (move N/S/E/W).

- **Mutation & Reproduction**  
  - Mutation rate = 2 / GENOME_LEN per hex digit per generation.  
  - Survivors chosen by spatial criteria; next generation sampled (with mutation) from survivors.

- **Selection Modes**  
  - **Center**: agents inside a circle at grid center  
  - **Corners**: agents inside quarter-circles at each corner

- **Outputs**  
  - Runs for GENS generations; logs survivor counts.  
  - Saves per-generation GIFs & final survivor-count plot in `output/`.

