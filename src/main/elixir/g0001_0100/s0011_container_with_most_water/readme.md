[![](https://img.shields.io/github/stars/LeetCode-in-Elixir/LeetCode-in-Elixir?label=Stars&style=flat-square)](https://github.com/LeetCode-in-Elixir/LeetCode-in-Elixir)
[![](https://img.shields.io/github/forks/LeetCode-in-Elixir/LeetCode-in-Elixir?label=Fork%20me%20on%20GitHub%20&style=flat-square)](https://github.com/LeetCode-in-Elixir/LeetCode-in-Elixir/fork)

## 11\. Container With Most Water

Medium

Given `n` non-negative integers <code>a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub></code> , where each represents a point at coordinate <code>(i, a<sub>i</sub>)</code>. `n` vertical lines are drawn such that the two endpoints of the line `i` is at <code>(i, a<sub>i</sub>)</code> and `(i, 0)`. Find two lines, which, together with the x-axis forms a container, such that the container contains the most water.

**Notice** that you may not slant the container.

**Example 1:**

![](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)

**Input:** height = [1,8,6,2,5,4,8,3,7]

**Output:** 49

**Explanation:** The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49. 

**Example 2:**

**Input:** height = [1,1]

**Output:** 1 

**Example 3:**

**Input:** height = [4,3,2,1,4]

**Output:** 16 

**Example 4:**

**Input:** height = [1,2,1]

**Output:** 2 

**Constraints:**

*   `n == height.length`
*   <code>2 <= n <= 10<sup>5</sup></code>
*   <code>0 <= height[i] <= 10<sup>4</sup></code>

## Solution

```elixir
defmodule Solution do
  @spec max_area(height :: [integer]) :: integer
  def max_area(height) do
    left = 0
    right = length(height) - 1

    height
    |> List.to_tuple()
    |> solve(left, right, 0)
  end

  def solve(_, l, r, ans) when l == r, do: ans
  def solve(height, l, r, ans) do
    lh = elem(height, l)
    rh = elem(height, r)

    ans = max(min(lh, rh) * (r - l), ans)
    cond do
      lh >= rh -> solve(height, l, r - 1, ans)
      lh < rh -> solve(height, l + 1, r, ans)
    end
  end
end
```