[![](https://img.shields.io/github/stars/LeetCode-in-Elixir/LeetCode-in-Elixir?label=Stars&style=flat-square)](https://github.com/LeetCode-in-Elixir/LeetCode-in-Elixir)
[![](https://img.shields.io/github/forks/LeetCode-in-Elixir/LeetCode-in-Elixir?label=Fork%20me%20on%20GitHub%20&style=flat-square)](https://github.com/LeetCode-in-Elixir/LeetCode-in-Elixir/fork)

## 206\. Reverse Linked List

Easy

Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)

**Input:** head = [1,2,3,4,5]

**Output:** [5,4,3,2,1]

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/02/19/rev1ex2.jpg)

**Input:** head = [1,2]

**Output:** [2,1]

**Example 3:**

**Input:** head = []

**Output:** []

**Constraints:**

*   The number of nodes in the list is the range `[0, 5000]`.
*   `-5000 <= Node.val <= 5000`

**Follow up:** A linked list can be reversed either iteratively or recursively. Could you implement both?

## Solution

```elixir
# Definition for singly-linked list.
#
# defmodule ListNode do
#   @type t :: %__MODULE__{
#           val: integer,
#           next: ListNode.t() | nil
#         }
#   defstruct val: 0, next: nil
# end

defmodule Solution do
  @spec reverse_list(head :: ListNode.t | nil) :: ListNode.t | nil
  def reverse_list(nil),                              do: nil
  def reverse_list(%ListNode{val: v, next: n}),       do: reverse_list(n, %ListNode{val: v, next: nil})
  def reverse_list(%ListNode{val: v, next: n}, acc),  do: reverse_list(n, %ListNode{val: v, next: acc})
  def reverse_list(nil, acc),                         do: acc
end
```