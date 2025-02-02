[![](https://img.shields.io/github/stars/LeetCode-in-Elixir/LeetCode-in-Elixir?label=Stars&style=flat-square)](https://github.com/LeetCode-in-Elixir/LeetCode-in-Elixir)
[![](https://img.shields.io/github/forks/LeetCode-in-Elixir/LeetCode-in-Elixir?label=Fork%20me%20on%20GitHub%20&style=flat-square)](https://github.com/LeetCode-in-Elixir/LeetCode-in-Elixir/fork)

## 64\. Minimum Path Sum

Medium

Given a `m x n` `grid` filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

**Note:** You can only move either down or right at any point in time.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/05/minpath.jpg)

**Input:** grid = \[\[1,3,1],[1,5,1],[4,2,1]]

**Output:** 7

**Explanation:** Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.

**Example 2:**

**Input:** grid = \[\[1,2,3],[4,5,6]]

**Output:** 12

**Constraints:**

*   `m == grid.length`
*   `n == grid[i].length`
*   `1 <= m, n <= 200`
*   `0 <= grid[i][j] <= 100`

## Solution

```elixir
defmodule Solution do
    @spec min_path_sum(grid :: [[integer]]) :: integer
    def min_path_sum(grid) do
        traverse(grid, [0 | List.duplicate(20000, 199)])
    end

    defp traverse([], prev_row), do: Enum.at(prev_row, -1)
    defp traverse([[first | row] | rows], [prev_row_head | prev_row]) do
        prev_row = traverse_row(row, prev_row, [first + prev_row_head])
        traverse(rows, prev_row)
    end

    defp traverse_row([], _prev_row, acc), do: Enum.reverse(acc)
    defp traverse_row([head | tail], [top | prev_row], [prev | _rest] = acc) do
        traverse_row(tail, prev_row, [head + min(prev, top) | acc])
    end
end
```