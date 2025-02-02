[![](https://img.shields.io/github/stars/LeetCode-in-Elixir/LeetCode-in-Elixir?label=Stars&style=flat-square)](https://github.com/LeetCode-in-Elixir/LeetCode-in-Elixir)
[![](https://img.shields.io/github/forks/LeetCode-in-Elixir/LeetCode-in-Elixir?label=Fork%20me%20on%20GitHub%20&style=flat-square)](https://github.com/LeetCode-in-Elixir/LeetCode-in-Elixir/fork)

## 46\. Permutations

Medium

Given an array `nums` of distinct integers, return _all the possible permutations_. You can return the answer in **any order**.

**Example 1:**

**Input:** nums = [1,2,3]

**Output:** [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

**Example 2:**

**Input:** nums = [0,1]

**Output:** [[0,1],[1,0]]

**Example 3:**

**Input:** nums = [1]

**Output:** [[1]]

**Constraints:**

*   `1 <= nums.length <= 6`
*   `-10 <= nums[i] <= 10`
*   All the integers of `nums` are **unique**.

## Solution

```elixir
defmodule Solution do
  @spec permute(nums :: [integer]) :: [[integer]]
  def permute([]),   do: [[]] 
  def permute(nums), do: for h <- nums, t <- permute(nums -- [h]), do: [h | t]
end
```