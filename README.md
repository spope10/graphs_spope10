# graphs_spope10

This Python library finds the lowest-cost paths from one starting vertex to other vertices in a weighted graph. It packages the Dijkstra implementation and heap module provided by Dr. Thyago Mota for CSC3020 Homework 4.

## Installation

From the repository folder containing pyproject.toml:

```powershell
python -m pip install .
```

After the public repository is created, it can also be installed directly:

```powershell
python -m pip install git+https://github.com/spope10/graphs_spope10.git
```

## Usage

```python
from graphs_spope10 import sp

graph = {
    0: {1: 4, 2: 10},
    1: {2: 3},
    2: {}
}
dist, path = sp.dijkstra(graph, 0)
print(dist)  # {0: 0, 1: 4, 2: 7}
print(path)  # {0: [], 1: [0], 2: [0, 1]}
```

The graph is a dictionary of neighbor dictionaries. Each edge maps a destination vertex to its weight. All vertices, including destinations without outgoing edges, must appear as top-level keys. Weights must be nonnegative, and finite path costs must be less than sys.maxsize.

The function returns two dictionaries: dist contains the minimum costs, and path contains the vertices before the destination on each reachable shortest path. For example, path[2] = [0, 1] represents the complete route 0 -> 1 -> 2. An unreachable vertex has a distance of sys.maxsize and no entry in path.

## Sample graph files

Each line contains three integers: source, destination, and weight. A line describes a directed edge; include the reverse edge when travel is allowed in both directions.

Run the supplied example after installation:

```powershell
python test.py data/example1.txt
```

The other supplied files are data/example2.txt and data/example3.txt.

## Development

Use dev for development and merge reviewed changes into main. The main branch must be protected in GitHub repository settings. Branch protection is configured on GitHub, not by these files.

## Repository URL

https://github.com/spope10/graphs_spope10


## Credits

Dijkstra's implementation and heapq.py were supplied in the instructor's starter repository. Original heap module author credits are preserved in heapq.py. The packaging configuration, package layout, and README were prepared for Soni Pope's assignment.
