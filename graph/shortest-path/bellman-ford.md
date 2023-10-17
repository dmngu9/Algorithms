## Note

- Works only for directed graph. If apply on undirected graph, for the edge (u, v), add additional edge (v, u)
- Work for graph with negative edge weight
- Not work for graph with negative weight cycle. Negative weight cycle means the sum of all edges in the cyle is less than 0.
- Can be used to detect negative weight cyle at the nth iteration

## Problem

Given a graph with **n** vertices labelled from **0** to **n-1**. Find the shortest path from vertex **0** to other vertex 

## Pseudocode

``` java
int[] distance = new int[n];

Arrays.fill(distance, Integer.MAX_VALUE); // initialize distance from vertex 0 to other vertex with big number
distance[0] = 0;

for (int i = 1; i <= n-1; i++) { // only do n-1 iterations
  for (edge e (u, v, w) of all edges) {
    if (distance[u] + w < distance[v]) {
      distance[v] = distance[u] + w;
    }
  }
}

// nth iteration to detect negative weight cycle
for (edge e (u, v, w) of all edges) {
  if (distance[u] + w < distance[v]) {
    System.out.print("negative weight cycle");
  }
}
```

Time complexity: O(VE)