## Note

- Works for both undirected and directed graph
- Not work for graph with negative edge weight

## Problem

Given a graph with **n** vertices labelled from **0** to **n-1**. Find the shortest path from vertex **0** to other vertex 

## Pseudocode

``` java
int[] distance = new int[n];
boolean[] vis = new boolean[n];

Arrays.fill(distance, Integer.MAX_VALUE); // initialize distance from vertex 0 to other vertex with big number
distance[0] = 0;

PriorityQueue<Pair<Integer, Integer>> q = new PriorityQueue<>((a, b) -> a.second - b.second); // pair of vertex and distance to it. Init min heap based on distance
q.offer(new Pair(0, 0)); // insert vertex 0 and the distance to reach it from vertex 0

while (!q.isEmpty()) {
  Pair<Integer, Integer> p = q.poll();

  if (vis[p.first]) continue;
  vis[p.first] = true;

  for (child c of vertex p.first) {
    if (p.second + distance_to_c_from_p.first < distance[c]) {
      distance[c] = p.second + distance_to_c_from_p.first;
      q.offer(new Pair(c, distance[c]));
    }
  }
}
```

Time complexity: O(V + ElogV)