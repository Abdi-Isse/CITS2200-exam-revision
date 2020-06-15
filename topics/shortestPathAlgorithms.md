# Shortest Path Algorithms
Topics: 
- Dijkstra
- Bellman-ford
- Floyd warshall 

# Dijkstra
[Dijkstra's algorithm in 3 minutes — Review and example](https://www.youtube.com/watch?v=_lHSawdgXpI)

Dijkstra pseudocode: 
```
Dijkstra(G, S): 
	For each vertex v in graph vertices G: 
		Distance[v] = infinity 
		Previous[v] = null
	
	Distance[S] = 0 // set the distance from the source to itself to 0 
	
	Q = priorityQueue(G) // create a priority queue of vertices  
	
	While Q is not empty: 
		U = removeMin(Q) // get the min vertex from the queue
		For edge (U, V) in edges: 
			If distance[V] > distance[U] + edgeWeight(U, V):  // perform relaxation 
				Distance[V] = distance[U] + edgeWeight(U, V)
				Previous[V] = U 
```
Dijkstra calculates the shortest path from the source to all vertices in a graph. 
Dijkstra does this by: 
1. Set distances to all other vertices to infinity initially 
2. Set distance from source to itself to 0
3. Create a priority queue of vertices and their edge weights 
4. Iterate through each vertex in the PQ
5. Dequeue the vertex with the minimum edge weights 
6. Perform relaxation on the vertex 
7. Repeat until no more vertex in the PQ

The time complexity for Dijkstra is: O(E log V).
- O(log V) as a heapify operation is performed on each vertex 
- O(E) as it iterates through all edges for every Vertex 


# Bellman-ford

[Bellman-Ford in 5 minutes — Step by step example](https://www.youtube.com/watch?v=obWXjtg0L64)

Bellman ford pseudocode: 
```
Bellman-ford pseudocode: 
Bellmanford(G, S): 
	For all vertex v in vertices G: 
		Distances[v] = infinity
		Previous = null 
	
	Distances[S] = 0 // set distance from source to itself to 0 
	
	For index in range( |V| - 1 ) : // loop through all vertices 
		 for all edge (u, v) in edges: 
			Distance[v] = min( distance[v], distance[u] + edgeWeight(u, v) ) // perform relaxation   

// additional function to detect negative cycles
For each edge(u, v) in edges: 
	If distance[v] > distance[u] + edgwWeights(u, v):
		Throw new Exception("negative cycle detected") // error 

```
Bellman-ford calculates the shortest path from source to all vertices in a graph. 
Bellman-ford achieves this by looping through all the vertices |V| - 1 in a graph O(|V|), and relaxing all edges associated with the vertex O(|E|). 
Unlike Dijkstra, Bellman-ford is able to handle negative edge weight as a result of looping through all edges. 
The time complexity for bellman-ford is O(|E| |V|). 


# Floyd-warshall
[Floyd–Warshall algorithm in 4 minutes](https://www.youtube.com/watch?v=4OQeCuLYj-4&t=29s)

Pseudocode: 

```
Floydwarshall(G):
	Distance = new int[V][V] // initialise distance as a new array of V*V 
	Distance.fill(infinity) // fill the array with the value infinity 
	
	For each vertex V in vertices:
		Distance[V][V] = 0 // set the distance between a vertex and itself to 0 
	
	For each edge(U, V) in edges:
		Distance[U][V] = edgeWeight(U, V) // set the value of known edges to its edge weight 
	
	For k from 1 to V: 
		For I from 1 to V:
			For J from 1 to V: 
				If distance[i][j] > distance[ I ] [k] + distance [k][j]:
					Distance[i][j] = distance[ I ] [k] + distance [k][j]
```

Floyd warshall calculates the shortest distance for each vertex to all other vertices in a graph. 
Floyd warshall does this by: 
1. Initialising an array of V*V and setting the values to infinity 
2. Setting the distance between a vertex and itself to 0 
3. Setting known edge weights in the array 
4. Looping through each vertex (outer loop, K) and relaxing each vertex (find the minimum shortest path). 
5. Keep looping until all the outer loop (K) is complete and all vertices are visited once 

Floyd warshall has a time complexity of O(V^3) as there are 3 nested loops it needs to complete. 
