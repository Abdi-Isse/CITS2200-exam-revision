# Tree traversals 
Topics:
- Traversals 
- Breadth First Search
- Depth First Search

# Traversals 
![tree-traversal-exercise](/images/treeTraversal-image1.png)

In-order:
- Visit left side
- Vist root
- Visit right side

`{j,d,b,e,m,i,n,a,f,c,h}`

Pre-order:
- Visit root
- Visit left side
- Visit right side

`{a,b,j,d,e,i,m,n,c,f,h}`

Post-Order:
- Visit left side
- Visit right side
- Visit root

`{j,d,e,b,m,n,i,f,h,c,a}`

# Breadth first search
[BFS Tutorial](https://www.hackerearth.com/practice/algorithms/graphs/breadth-first-search/tutorial/)

Pseudocode: 
```
Bfs(G, S): 
	Q = new Queue() // create a new queue to store vertices 
	Q.enqueue(S) // add the source to the queue 
	Visited = [G.Vertices] // create an empty array 
	Visited.fill(False) // fill the array with false
	Visited[S] = True // set the source node to visited 
	
	While Q is not empty: 
		V = Q.dequeue() // remove the vertex at the front of the queue 
		For all neighbours W of V: 
			If visited[W] == false: // if not yet visited 
				Q.enqueue(W)
				Visited[W] = true 
```
Explanation: 
BFS traverses an entire graph starting from the source vertex using the following steps: 
1. Create a new empty queue 
2. Add the source vertex to the queue 
3. Initialise an array to mark vertices as visited. Set all values to False. 
4. Mark the source node as visited. 
5. While the Queue is not empty:
  - Dequeue the vertex at the front of the queue 
  - Get all the neighbors of the dequeud vertex 
    - If neighbours are not yet visited:
      - Add the neighbor to the queue and mark as visited. 

Time complexity:
- O(V+E)
  - O(V) as all vertices are visited as part of the queue 
  - O(E) as the edges of each vertex are examined. 

# Depth first search
[DFS Tutorial](https://www.hackerearth.com/practice/algorithms/graphs/depth-first-search/tutorial/)

DFS(non-recursive) pseudocode: 
```
Dfs(G, s): 
	stk = new Stack()
	stk.push(s)
	Visited = [G.vertices] 
	Visited.fill(False)
	Visited[s] = True // mark the source as visited  
	While stk is not empty: 
		V = stk.pop() 
		For all neighbours w of v:
			If visited[w] == False:
				Stk.push(w)
				Visited[w] = True
```

Recursive pseudocode: 
```
Dfs(G, v):
	Visited[v] = True // mark v as visited  -- assume visited is created elsewhere and also passed into the function or declared globally 
	For all neighbors w of v:
		If visited == false:
			Dfs(G, w)  
```

Explanation:
(similar to BFS).

Time complexity: 
- O(V+E)
  - O(V) as all vertices are visited once as part of the stack or recursion 
  - O(E) as neighbor edges of each vertex is examined. 