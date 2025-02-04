# Lua Iteration Order Bug

This repository demonstrates a potential issue with Lua's `pairs` iterator when used with nested tables.  The bug arises from modifying the table structure during iteration which can lead to unexpected iteration results.

## Bug Description

The `pairs` iterator in Lua does not guarantee a specific iteration order. When you modify a table during iteration, particularly with nested tables, the results become unpredictable.  The code in `bug.lua` showcases this behavior. The function `foo` recursively iterates through a nested table, but because of the implicit modification during the iteration the order of iteration is not predictable.

## Solution

The solution involves creating a copy of the table before iteration, ensuring the original table remains unchanged, and eliminating the potential for unexpected behavior.  This approach, shown in `bugSolution.lua`, guarantees predictable iteration, even with nested structures.

## How to Reproduce

1. Clone this repository.
2. Run `bug.lua` using a Lua interpreter (e.g., `lua bug.lua`). Observe that the order may vary between runs.
3. Run `bugSolution.lua`. This version produces the predictable result.