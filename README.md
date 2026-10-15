# Experiment No. 8

## Title

**Dynamic Programming: Bellman-Ford Algorithm to Find the Shortest Path**

## Aim

To implement the Bellman-Ford Algorithm to find the shortest paths from a given source vertex to all other vertices in a weighted directed graph and analyze its time and space complexity.

## Program

```c
#include <stdio.h>

#define MAX 20
#define INF 99999

struct Edge
{
    int src, dest, weight;
};

int main()
{
    int V, E, source;
    struct Edge edges[MAX * MAX];
    int dist[MAX];

    printf("Enter number of vertices: ");
    scanf("%d", &V);

    printf("Enter number of edges: ");
    scanf("%d", &E);

    printf("Enter source, destination and weight of each edge:\n");

    for (int i = 0; i < E; i++)
    {
        scanf("%d %d %d",
              &edges[i].src,
              &edges[i].dest,
              &edges[i].weight);
    }

    printf("Enter source vertex: ");
    scanf("%d", &source);

    for (int i = 0; i < V; i++)
    {
        dist[i] = INF;
    }

    dist[source] = 0;

    for (int i = 1; i <= V - 1; i++)
    {
        for (int j = 0; j < E; j++)
        {
            int u = edges[j].src;
            int v = edges[j].dest;
            int w = edges[j].weight;

            if (dist[u] != INF &&
                dist[u] + w < dist[v])
            {
                dist[v] = dist[u] + w;
            }
        }
    }

    for (int j = 0; j < E; j++)
    {
        int u = edges[j].src;
        int v = edges[j].dest;
        int w = edges[j].weight;

        if (dist[u] != INF &&
            dist[u] + w < dist[v])
        {
            printf("Graph contains a negative weight cycle.\n");
            return 0;
        }
    }

    printf("\nShortest distances from source vertex %d:\n",
           source);

    printf("Vertex\tDistance\n");

    for (int i = 0; i < V; i++)
    {
        if (dist[i] == INF)
        {
            printf("%d\tUnreachable\n", i);
        }
        else
        {
            printf("%d\t%d\n", i, dist[i]);
        }
    }

    return 0;
}
```

## Output

The terminal output of the Bellman-Ford Algorithm is shown below:

**Sample Input:**

```text
Enter number of vertices: 5
Enter number of edges: 8
Enter source, destination and weight of each edge:
0 1 -1
0 2 4
1 2 3
1 3 2
1 4 2
3 2 5
3 1 1
4 3 -3
Enter source vertex: 0
```

**Sample Output:**

```text
Shortest distances from source vertex 0:
Vertex  Distance
0       0
1       -1
2       2
3       -2
4       1
```

**Note:** This is a sample output. You can replace it with a screenshot of your actual terminal output.

## Algorithm

1. Start the program.
2. Read the number of vertices and edges.
3. Read the source vertex, destination vertex, and weight of each edge.
4. Initialize the distance of every vertex to infinity.
5. Set the distance of the source vertex to zero.
6. Repeat the relaxation process for all edges **V − 1 times**, where V is the number of vertices.
7. For each edge `(u, v)` with weight `w`, check whether `dist[u] + w < dist[v]`.
8. If the condition is true, update `dist[v]` to `dist[u] + w`.
9. Check all edges once more to detect a negative-weight cycle reachable from the source.
10. If such a cycle exists, display a negative-weight-cycle message.
11. Otherwise, display the shortest distances from the source vertex to all vertices.
12. Stop the program.

## Time Complexity

| **Operation**                    | **Time Complexity** |
| -------------------------------- | ------------------- |
| Reading vertices and edges       | **O(V + E)**        |
| Initializing distances           | **O(V)**            |
| Relaxing all edges V − 1 times   | **O(V × E)**        |
| Detecting negative-weight cycles | **O(E)**            |
| Overall Time Complexity          | **O(V × E)**        |

### Explanation

The Bellman-Ford Algorithm calculates the shortest distances by repeatedly relaxing all edges in the graph.

* Initializing the distance array takes **O(V)** time.
* The algorithm relaxes all E edges for V − 1 iterations, requiring **O(V × E)** time.
* The final iteration checks for a reachable negative-weight cycle in **O(E)** time.

Therefore:

**Time Complexity = O(V × E)**

Where:

* **V** = Number of vertices.
* **E** = Number of edges.

## Space Complexity

The program uses the following data structures:

* `edges[MAX * MAX]` to store the edges of the graph.
* `dist[MAX]` to store the shortest distance from the source vertex to every other vertex.

The edge array requires **O(E)** space, and the distance array requires **O(V)** space.

Therefore:

**Space Complexity = O(V + E)**

## Applications

1. Finding shortest paths in weighted graphs.
2. Working with graphs containing negative edge weights.
3. Detecting negative-weight cycles reachable from a source vertex.
4. Network routing and distance-vector routing protocols.
5. Transportation and path-planning problems.
6. Analyzing weighted directed graphs.

## Advantages

* Handles negative edge weights.
* Finds shortest distances from a single source to all reachable vertices.
* Detects negative-weight cycles reachable from the source.
* Works with directed and undirected graphs when represented appropriately.
* Provides a systematic method for solving shortest-path problems.

## Limitations

* It is generally slower than Dijkstra's Algorithm for graphs with non-negative edge weights.
* The algorithm requires repeated relaxation of all edges.
* Shortest paths are undefined for vertices affected by a reachable negative-weight cycle.
* The given implementation uses fixed-size arrays.
* The program displays shortest distances but does not reconstruct the actual paths.
* Vertices must be numbered from `0` to `V - 1`.

## Conclusion

The Bellman-Ford Algorithm is implemented using repeated edge relaxation to find the shortest distances from a given source vertex to all other reachable vertices in a weighted graph.

Unlike Dijkstra's Algorithm, Bellman-Ford can handle negative edge weights and detect negative-weight cycles reachable from the source.

For the given implementation, the overall time complexity is **O(V × E)**, and the space complexity is **O(V + E)**.

The algorithm is useful for shortest-path problems involving negative edge weights and for detecting negative-weight cycles.
# output image 
<img width="1672" height="941" alt="bellman1" src="https://github.com/user-attachments/assets/d010b0a6-cbde-46e7-9bdc-b69bdf012701" />
