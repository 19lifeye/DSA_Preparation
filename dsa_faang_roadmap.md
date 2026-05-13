# DSA Roadmap for FAANG Companies

> **Target timeline:** ~6 months | **Topics:** 35+ | **Phases:** 6

---

## Phase 1 — Foundations & Complexity
**Duration: Weeks 1–2**

|    | Topic | Key Concepts |
|    |---|---|
| [] |  Big O notation | Time & space complexity, best/average/worst case |
| [] |  Arrays & strings | Basic operations, in-place edits, two-pointer patterns |
| [] |  Recursion basics | Base cases, call stack, tail recursion |
| [] |  Hashing | HashMap, HashSet, collision handling |

> **Tip:** Build a habit of always analyzing time & space before coding a solution.

---

## Phase 2 — Core Data Structures
**Duration: Weeks 3–6**

| Topic | Key Concepts | Frequency |
|---|---|---|
| Linked lists | Singly, doubly, cycle detection (Floyd's) | 🔥 High |
| Stacks & queues | Monotonic stacks, deque, implementation | 🔥 High |
| Trees | Binary tree, DFS/BFS traversals, height, diameter | 🔥 High |
| BST | Insert, delete, search, successor/predecessor | Core |
| Heaps / Priority Queue | Min/max heap, heapify, top-K problems | 🔥 High |
| Hash maps & sets | Collision, open addressing, chaining | 🔥 High |

> **Tip:** Implement each structure from scratch at least once. FAANG often asks you to build, not just use them.

---

## Phase 3 — Core Algorithms
**Duration: Weeks 7–10**

| Topic | Key Concepts | Frequency |
|---|---|---|
| Binary search | On sorted array, on answer space, tricky edge cases | 🔥 High |
| Two pointers | Opposite ends, fast/slow pointers | 🔥 High |
| Sliding window | Fixed & variable size windows | 🔥 High |
| Sorting algorithms | Merge sort, quicksort, counting sort, radix sort | Core |
| DFS | Recursive & iterative, graph and tree variants | 🔥 High |
| BFS | Level order, shortest path in unweighted graphs | 🔥 High |
| Backtracking | Permutations, combinations, subsets, N-Queens | 🔥 High |
| Prefix sums | Range queries, difference arrays | Core |

> **Tip:** Two pointers + sliding window + binary search alone solve ~25% of FAANG problems. Master these first.

---

## Phase 4 — Dynamic Programming
**Duration: Weeks 11–14**

| Topic | Key Concepts | Frequency |
|---|---|---|
| 1D DP | Climbing stairs, house robber, Fibonacci, coin change | 🔥 High |
| 2D DP | Grid paths, unique paths, edit distance, LCS | 🔥 High |
| Knapsack patterns | 0/1 knapsack, unbounded, subset sum | Core |
| Subsequences | LIS, LCS, palindromic subsequences | Core |
| Interval & string DP | Burst balloons, matrix chain multiplication | Core |
| Bitmask DP | State compression, traveling salesman | Advanced |

> **Tip:** Always think — "overlapping subproblems + optimal substructure?" Start with recursion + memoization, then optimize to tabulation.

---

## Phase 5 — Graphs & Advanced Trees
**Duration: Weeks 15–18**

| Topic | Key Concepts | Frequency |
|---|---|---|
| Graph basics | Adjacency list vs matrix, directed/undirected, weighted | 🔥 High |
| Topological sort | Kahn's BFS algorithm, DFS-based approach | 🔥 High |
| Union Find | Path compression, union by rank, connected components | 🔥 High |
| Shortest paths | Dijkstra, Bellman-Ford, Floyd-Warshall | Core |
| Minimum spanning tree | Kruskal's, Prim's algorithms | Core |
| Trie | Insert, search, prefix matching, autocomplete | 🔥 High |
| Segment tree | Range sum/min/max queries, lazy propagation | Advanced |
| Balanced BST | AVL, Red-Black trees (conceptual understanding) | Advanced |

> **Tip:** Graph problems dominate senior FAANG rounds. Model real-world problems as graphs — cities as nodes, roads as edges.

---

## Phase 6 — Advanced & FAANG Patterns
**Duration: Weeks 19–24**

| Topic | Key Concepts | Frequency |
|---|---|---|
| Greedy algorithms | Activity selection, interval scheduling, jump game | 🔥 High |
| Monotonic stack | Next greater element, largest rectangle in histogram | 🔥 High |
| Bit manipulation | XOR tricks, bitmasks, power of 2, counting set bits | 🔥 High |
| Math & number theory | GCD, Sieve of Eratosthenes, modular arithmetic | Core |
| Design data structures | LRU cache, LFU cache, MedianFinder, iterator | 🔥 High |
| Advanced graphs | SCC (Tarjan's/Kosaraju's), bridges, articulation points | Advanced |
| String algorithms | KMP, Z-algorithm, Rabin-Karp rolling hash | Advanced |
| System design basics | Relevant for mid/senior-level roles | Core |

> **Tip:** In the final 4 weeks, do timed mock interviews daily. Focus on communication — narrate your thinking out loud.

---

## Complexity Cheat Sheet

| Complexity | Name | Example | Rating |
|---|---|---|---|
| O(1) | Constant | Array index, hash lookup | Excellent |
| O(log n) | Logarithmic | Binary search | Great |
| O(n) | Linear | Linear scan, find max | Good |
| O(n log n) | Linearithmic | Merge sort, heap sort | Fair |
| O(n²) | Quadratic | Bubble sort, nested loops | Bad |
| O(2ⁿ) | Exponential | Naive Fibonacci, subsets | Terrible |
| O(n!) | Factorial | Brute-force permutations | Avoid |

---

## Key Interview Tips

1. **Always analyze complexity first** — state both time AND space before coding.
2. **Two pointers + sliding window + binary search** solve ~25% of problems alone.
3. **Implement data structures from scratch** — FAANG asks you to build, not just use.
4. **For DP** — start with recursion + memoization, then optimize to bottom-up tabulation.
5. **Graph problems dominate senior rounds** — practice modeling real problems as graphs.
6. **Narrate your thinking** — communication matters as much as the solution.
7. **Do timed mock interviews** — aim for 150–200 LeetCode problems before interviews.
8. **Practice by company** — filter LeetCode by Google / Meta / Amazon for targeted prep.

---

## Recommended Practice Plan

| Phase | LeetCode Target | Focus |
|---|---|---|
| Phases 1–2 | 20–30 problems | Arrays, strings, linked lists, trees |
| Phase 3 | 30–40 problems | Binary search, two pointers, BFS/DFS |
| Phase 4 | 25–35 problems | DP patterns — start easy, build up |
| Phase 5 | 20–30 problems | Graphs, union find, trie |
| Phase 6 | 30–40 problems | Mixed hard problems, mock interviews |

**Total target: 150–200 problems over 6 months**

---
