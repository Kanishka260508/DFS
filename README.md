# Depth-First Search (DFS) in Python

## 📌 Overview

This project demonstrates the implementation of the **Depth-First Search (DFS)** algorithm using Python. DFS explores a graph by going as deep as possible along each branch before backtracking.

It is commonly used for:

* Path finding
* Cycle detection
* Solving puzzles (like mazes)

---

## 🚀 Features

* Recursive DFS implementation
* Tracks visited nodes to avoid cycles
* Uses a **parent dictionary** to reconstruct the path
* Displays traversal and backtracking steps
* Finds a path from start node to goal node

---

## 🧠 How It Works

1. Start at the initial node
2. Mark it as visited
3. Recursively visit each unvisited neighbor
4. If the goal is found, stop immediately
5. If a dead end is reached, backtrack
6. Reconstruct the path using parent pointers

---

## 🗂️ Graph Representation

```python
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}
```

---

## 💻 Code Implementation

```python
def dfs(graph, start, goal, visited=None, parent=None):
    if visited is None:
        visited = set()
        parent = {start: None}

    visited.add(start)
    print(f"Visiting node: {start}")

    if start == goal:
        print(f"\nGoal '{goal}' found!")
        return True, parent

    for neighbor in graph[start]:
        if neighbor not in visited:
            parent[neighbor] = start
            found, parent = dfs(graph, neighbor, goal, visited, parent)
            if found:
                return True, parent
            else:
                print(f" Backtracking from {neighbor} to {start}")

    return False, parent
```

---

## ▶️ Example Usage

```python
found, parent = dfs(graph, 'A', 'F')

if found:
    path = []
    node = 'F'
    while node is not None:
        path.append(node)
        node = parent[node]
    
    path.reverse()
    print("\nDFS Path from A to F:", " -> ".join(path))
```

---

## 📊 Sample Output

```
Visiting node: A
Visiting node: B
Visiting node: D
 Backtracking from D to B
Visiting node: E
Visiting node: F

Goal 'F' found!

DFS Path from A to F: A -> B -> E -> F
```

---

## 🎯 Applications of DFS

* Path finding in graphs
* Topological sorting
* Detecting cycles in graphs
* Solving puzzles (maze, Sudoku)
* AI search algorithms

---

## 🛠️ Requirements

* Python 3.x

---

## 📌 Conclusion

This project demonstrates how DFS works using recursion and backtracking. It helps build a strong foundation in graph traversal and algorithm design.

---

## 🙌 Author

Developed as part of learning Data Structures & Algorithms.
