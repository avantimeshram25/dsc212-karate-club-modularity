# DSC212: Modularity on the Karate Club Graph

This repository contains the research assignment notebook for recursive spectral modularity partitioning on Zachary's Karate Club graph.

## Contents

- `DSC212_Karate_Club_Modularity.ipynb`: Complete top-to-bottom analysis with code, outputs, visualizations, node metrics, discussion, and references.
- `LICENSE`: MIT License.
- `DSC212__Assignment.pdf`: Course assignment handout.

## Run the notebook

The notebook uses Python 3 with NumPy, NetworkX, pandas, Matplotlib, Jupyter, and nbconvert. From the repository directory:

```bash
python3 -m venv .venv
.venv/bin/pip install numpy networkx pandas matplotlib jupyter nbconvert
.venv/bin/jupyter nbconvert --to notebook --execute --inplace DSC212_Karate_Club_Modularity.ipynb
```

The graph is explicitly treated as unweighted, matching the 34-node, 78-edge graph defined in the handout. The notebook uses a fixed layout seed so its visualizations are reproducible.

## Attribution

The modularity matrix and spectral method follow Newman (2006), *Modularity and community structure in networks*. The data set originates from Zachary (1977), *An information flow model for conflict and fission in small groups*.
# dsc212-karate-club-modularity
