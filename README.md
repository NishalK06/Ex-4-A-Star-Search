<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: Nishal K
<h3>Register Number: 2305001021
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


// A* Search Algorithm

1.Initialize


   i) Open list ← priority queue (min-heap)

   ii) Closed list ← empty set

  iii) Insert the start node into the open list with:

        g = 0

        h = heuristic(start)

        f = g + h


2.While Open list is not empty:

   i) Remove the node q with the lowest f from the open list.

  ii) If q is the goal node, return the path (reconstruct from parents).

 iii) If q is already in the Closed list, skip it.

  iv) Add q to the Closed list.
  

3.For each neighbor n of q:

  i) Compute:

    g(n) = g(q) + cost(q, n)

    h(n) = heuristic(n)

    f(n) = g(n) + h(n)

ii) If n is not in Closed list:

    Insert (f(n), g(n), n, path_so_far) into Open list.

    
4.If goal is never reached and Open list becomes empty:

  i) Return "No path found".

## PROGRAM
```python


import heapq

def astar(g,s,t,h):
    q=[(h[s],0,s,[])]
    v=set()
    while q:
        f,gc,u,p=heapq.heappop(q)
        if u==t: return p+[u]
        if u in v: continue
        v.add(u)
        for x,c in g.get(u,[]): 
            if x not in v: heapq.heappush(q,(gc+c+h.get(x,0),gc+c,x,p+[u]))
    return None

g={}
print("Input edges as: node1 node2 cost (type 'done' when finished):")
while (e:=input())!="done":
    u,v,c=e.split();g.setdefault(u,[]).append((v,int(c)))

h={u:int(input(f"Heuristic for {u}: ")) for u in g}
s=input("Start node: ");t=input("Goal node: ")
print("Path:",astar(g,s,t,h) or "No path found")

```

## GRAPH 

<img width="373" height="395" alt="image" src="https://github.com/user-attachments/assets/e44e4f2a-f70b-4578-9ea8-b9cabf26a59b" />


## INPUT

A B 3

A D 5

B C 4

C E 6

D F 1

E F 2


## Output

<img width="792" height="603" alt="image" src="https://github.com/user-attachments/assets/0d341ceb-6556-4055-a9d2-bdc6cb9b0e7a" />



## RESULT:
Thus, the program successfully finds the shortest path from the start node to the goal node using the A* algorithm.


