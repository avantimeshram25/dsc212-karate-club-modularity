# Modularity on the Karate Club Graph

Research assignment for DSC212: Graph Theory Module. This project implements recursive spectral modularity partitioning on Zachary's 34-member Karate Club network.

## 1. Goals

The notebook addresses the required tasks:

1. Construct the modularity matrix and use its leading eigenvector to find a bipartition.
2. Apply the spectral split recursively to detect multiple communities.
3. Visualize the graph after every accepted split using a fixed layout and community colors.
4. Compute degree, betweenness, closeness, and clustering metrics after each iteration.
5. Plot metric evolution and discuss which nodes remain central as the graph is divided.

## 2. Method

For adjacency matrix $A$, degree vector $k$, and $m$ edges, the notebook constructs

$$B = A - \frac{kk^\top}{2m}.$$

The leading eigenvector of a restricted modularity matrix supplies a sign-based candidate split. A split is accepted only when both groups are nonempty and the actual discrete modularity gain is positive. For recursive communities, the notebook uses Newman's corrected restricted matrix

$$B_C = B[C,C] - \operatorname{diag}(B[C,C]\mathbf{1}),$$

which gives the restricted matrix zero row sums and makes the eigenvalue stopping rule valid. The graph is explicitly unweighted, matching the handout's 78-edge definition.

## 3. Results

The executed notebook detects four communities and obtains final modularity $Q = 0.3934$:

| Community | Nodes |
| --- | --- |
| 1 | 1, 5, 6, 7, 11, 12, 17 |
| 2 | 2, 3, 4, 8, 13, 14, 18, 20, 22 |
| 3 | 9, 10, 15, 16, 19, 21, 23, 27, 30, 31, 33, 34 |
| 4 | 24, 25, 26, 28, 29, 32 |

Nodes 1 and 34 are important reference points because they are the historical faction leaders and have strong network-centrality roles. When metrics are calculated inside induced communities, betweenness generally decreases for nodes whose original importance came from connecting different communities. Degree, closeness, and clustering are also rescaled by the size and density of the community being analyzed.

## 4. Repository contents

```text
.
├── DSC212_Karate_Club_Modularity.ipynb  # Executed notebook with code and outputs
├── DSC212__Assignment.pdf               # Course handout
├── LICENSE                              # MIT License
└── README.md
```

## 5. How to run

From the repository directory:

```bash
python3 -m venv .venv
.venv/bin/pip install numpy networkx pandas matplotlib jupyter nbconvert
.venv/bin/jupyter nbconvert --to notebook --execute --inplace DSC212_Karate_Club_Modularity.ipynb
```

The notebook runs top-to-bottom without manual edits. A fixed spring-layout seed makes the visualizations reproducible.

## 6. AI usage disclosure

I used GitHub Copilot to clarify Python library APIs, organize notebook sections, and check implementation details. I reviewed the mathematics, code, outputs, interpretation, and final submission, and I am responsible for the submitted work.

## 7. References

1. M. E. J. Newman (2006), *Modularity and community structure in networks*, PNAS, 103(23), 8577-8582.
2. W. W. Zachary (1977), *An information flow model for conflict and fission in small groups*, Journal of Anthropological Research, 33(4), 452-473.
3. DSC212 course handout, *Modularity on the Karate Club Graph*.

