[![](https://img.shields.io/github/stars/LeetCode-in-Elixir/LeetCode-in-Elixir?label=Stars&style=flat-square)](https://github.com/LeetCode-in-Elixir/LeetCode-in-Elixir)
[![](https://img.shields.io/github/forks/LeetCode-in-Elixir/LeetCode-in-Elixir?label=Fork%20me%20on%20GitHub%20&style=flat-square)](https://github.com/LeetCode-in-Elixir/LeetCode-in-Elixir/fork)

## 136\. Single Number

Easy

Given a **non-empty** array of integers `nums`, every element appears _twice_ except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

**Example 1:**

**Input:** nums = [2,2,1]

**Output:** 1

**Example 2:**

**Input:** nums = [4,1,2,1,2]

**Output:** 4

**Example 3:**

**Input:** nums = [1]

**Output:** 1

**Constraints:**

*   <code>1 <= nums.length <= 3 * 10<sup>4</sup></code>
*   <code>-3 * 10<sup>4</sup> <= nums[i] <= 3 * 10<sup>4</sup></code>
*   Each element in the array appears twice except for one element which appears only once.

## Solution

```elixir
defmodule Solution do
  @spec single_number(nums :: [integer]) :: integer
  def single_number(nums) do
    nums
    |> Enum.frequencies()
    |> Enum.find(fn {k, v} -> v == 1 end)
    |> elem(0)
  end
end
```