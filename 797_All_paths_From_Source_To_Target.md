## Question : All Paths From Source To Target

Given a directed acyclic graph (DAG) of n nodes labeled from 0 to n - 1, find all possible paths from node 0 to node n - 1, and return them in any order. The graph is given as follows: graph[i] is a list of all nodes you can visit from node i (i.e., there is a directed edge from 
node i to node graph[i][j]).

## Solution :

```python3
class Solution:
    def util(self, graph, curr, path, target, paths):
        path.append(curr)
        if curr == target:
            return path
        to_visit = graph[curr]
        for node in to_visit:
            new_path = path.copy()
            curr_path = self.util(graph, node, new_path, target, paths)
            if curr_path:
                paths.append(curr_path)

    def allPathsSourceTarget(self, graph: List[List[int]]) -> List[List[int]]:
        paths = []
        self.util(graph, 0, [], len(graph)-1, paths)
        return paths
```
