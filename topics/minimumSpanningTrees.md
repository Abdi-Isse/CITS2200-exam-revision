# Minimum Spanning Trees
Topics: 
- Kruskal
- Prim

# Kruskal's MST
[Kruskal's algorithm in 2 minutes — Review and example](https://www.youtube.com/watch?v=71UQH7Pr9kU)

Kruskal's pseudocode: 

```
Kruskal(V, E):
	For each vertex v in vertices V: 
		Makeset(v) // 
	X = {} // create an empty set to store the minimum spanning tree 
	
	For each edge(u, v) in edges, ordered by lowest weight to highest weight: 
		If find(u) != find(v): // make sure that there are no cycles
			X = X.append(u, v) // add the edge 
			Union(u, v) 
```
Kruskal finds a minimum spanning tree by: 
1. Creating an emptyset to store the MST
2. Looping through each edge ordered from lowest to highest weight
3. Checking that the edge does not contain a cycle
    - If it does: reject the edge 
    - If it doesn't: add the edge to the MST
4. Keep repeating until reached all edges 

Time complexity: 
- Kruskal has a time complexity of O(E log V):
    - O(E) as it has to iterate through all the edges
    - O(log V) to perform heapify. 

# Prim's MST
[Prim's algorithm in 2 minutes — Review and example](https://www.youtube.com/watch?v=cplfcGZmX7I)

Prim's pseudocode: 
```
Prim(V, E): 
	For each vertex v in vertices V: 
		Distance[v] = infinity 
		Previous[v] = null
	Distance[0] = 0 // pick a random starting node and set the distance to itself to 0 
	Q = createQueue(V) // create a priority queue of vertices 
	
	While Q is not empty: 
		U = removeMin(Q) // get the vertex with the minimum edge weight 
		For edge(u, v) in edges: 
			If distance[v] > edgeWeight[u][v]:
				Distance[v] = edgeWeight(u, v)
				Previous[v] = U
				decreaseKey(Q, v) 
```
Prim finds the MST through the following steps: 
1. Initialise distances from the initial node to all other nodes to infinity 
2. Pick a random node as the starting node and set the distance to itself to 0 
3. Create a priority queue of vertices 
4. While the priority queue is not empty, keep doing the following: 
    - If there is a shorter distance, then set the distance[v] to that of edgeWeight(u v) and add it to the MST 
    - Keep repeating until the queue is empty 
5. We should now have our MST 

Time complexity: 
- O(E log V) 
    - O(E) because we iterate through all the edges
    - O(log V) because we perform a heapify operation on each edge
