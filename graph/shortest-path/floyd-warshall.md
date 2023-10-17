## Note

- Works only for directed graph. If apply on undirected graph, for the edge (u, v), add additional edge (v, u)
- Used for all pairs of shortest-path problems

## Problem

Given a graph with **n** vertices labelled from **0** to **n-1**. Find the shortest path for all pairs of vertices

## Pseudocode

``` java
int[][] distance = new int[n][n];
for (int[] r : distance) {
  Arrays.fill(r, Integer.MAX_VALUE);
}
for (edge (u, v, w) of all edges) {
  distance[u][v] = w;
}

for (int via = 0; via < n; via++) { // the intermediate vertex between i and j vertex
  for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
      if (distance[i][via] + distance[via][j] < distance[i][j]) {
        distance[i][j] = distance[i][via] + distance[via][j];
      }
    }
  }
}
```

Time complexity: O(V^3)