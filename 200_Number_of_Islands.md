## Question : Number of Islands

Given an `m x n` 2D binary grid `grid` which represents a map of `'1'`s (land) and `'0'`s (water), return the number of islands.

An **island** is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example:**
```
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
```

## Solution :

```python3
class Solution:
    def numIslands(self, grid):
        rows = len(grid)
        cols = len(grid[0])
        def markIslands(r, c):
            if 0 <= r < rows and 0 <= c < cols and grid[r][c] == "1":
                grid[r][c] = "v"
                markIslands(r+1, c)
                markIslands(r-1, c)
                markIslands(r, c+1)
                markIslands(r, c-1)
        result = 0
        for i in range(rows):
            for j in range(cols):
                if grid[i][j]== "1":
                    markIslands(i,j)
                    result += 1
        return result
```