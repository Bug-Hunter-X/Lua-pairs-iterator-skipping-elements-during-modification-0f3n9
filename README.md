# Lua pairs iterator skipping elements during modification

This repository demonstrates a subtle bug in Lua where the `pairs` iterator might skip elements if the table being iterated over is modified within the loop. This can lead to unexpected behavior and incomplete traversal of the table.

## Bug Description

The `pairs` iterator in Lua does not guarantee a specific iteration order.  Furthermore, if a table is modified during iteration (e.g., elements are added or removed), the iterator's behavior can become unpredictable.  Elements might be skipped, leading to incomplete processing.

## Reproducing the Bug

The `bug.lua` file contains a simple example that showcases this issue. Running this script might not print all expected values.   The issue is exacerbated in nested tables, where changes in inner tables can affect the outer loop's behavior.

## Solution

The `bugSolution.lua` file offers a solution using a copy of the table to avoid modifying the original table during iteration.  This ensures that all elements are processed correctly.

## How to Run

1. Clone this repository.
2. Ensure you have Lua installed.
3. Navigate to the repository's directory in your terminal.
4. Run `lua bug.lua` to see the bug in action.
5. Run `lua bugSolution.lua` to see the corrected behavior.