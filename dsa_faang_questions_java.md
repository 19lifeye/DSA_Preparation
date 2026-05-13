# DSA Question Bank — FAANG Edition (Java)
> 300+ curated problems | Organized by pattern | With Java solution hints

---

## 1. Arrays & Strings

### Easy
| # | Problem | Key Idea | Java Hint |
|---|---|---|---|
| 1 | Two Sum | HashMap complement | `map.getOrDefault()` |
| 2 | Best Time to Buy & Sell Stock | Track min so far | One pass |
| 3 | Contains Duplicate | HashSet | `set.add()` returns false if duplicate |
| 4 | Maximum Subarray (Kadane's) | DP / greedy | `max = Math.max(num, max + num)` |
| 5 | Move Zeroes | Two pointers | In-place, maintain order |
| 6 | Merge Sorted Array | Three pointers from end | Avoid extra space |
| 7 | Remove Duplicates from Sorted Array | Two pointers | `slow/fast` pointer |
| 8 | Plus One | Carry propagation | Handle `999` edge case |
| 9 | Single Number | XOR trick | `a ^ a = 0`, `a ^ 0 = a` |
| 10 | Missing Number | XOR or Gauss sum | `n*(n+1)/2 - sum` |
| 11 | Palindrome Number | Reverse half | No string conversion |
| 12 | Majority Element | Boyer-Moore voting | O(1) space |
| 13 | Pascal's Triangle | DP row by row | `List<List<Integer>>` |
| 14 | Intersection of Two Arrays II | HashMap frequency | `map.getOrDefault()` |
| 15 | Rotate Array | Reverse trick | Reverse all, then parts |

### Medium
| # | Problem | Key Idea | Java Hint |
|---|---|---|---|
| 16 | 3Sum | Sort + two pointers | Skip duplicates carefully |
| 17 | Container With Most Water | Two pointers | Move shorter side |
| 18 | Product of Array Except Self | Prefix + suffix | No division, O(1) space |
| 19 | Spiral Matrix | Boundary simulation | `top, bottom, left, right` |
| 20 | Rotate Image | Transpose + reverse | In-place |
| 21 | Set Matrix Zeroes | Use first row/col as marker | O(1) space trick |
| 22 | Longest Consecutive Sequence | HashSet + expand | O(n) using set |
| 23 | Subarray Sum Equals K | Prefix sum + HashMap | `map.put(0, 1)` initially |
| 24 | Find All Duplicates in Array | Negate visited index | Index as hash |
| 25 | Sort Colors (Dutch National Flag) | 3-way partition | `lo, mid, hi` pointers |
| 26 | Jump Game | Greedy max reach | Track `maxReach` |
| 27 | Jump Game II | Greedy BFS-like | Track current/next level |
| 28 | Merge Intervals | Sort by start | `curr[1] < next[0]` check |
| 29 | Insert Interval | Find overlap range | Binary search or linear |
| 30 | Next Permutation | Find pivot + swap | Reverse suffix |
| 31 | Search in Rotated Sorted Array | Binary search variants | Determine sorted half |
| 32 | Find Minimum in Rotated Sorted Array | Binary search | Compare mid to right |
| 33 | Group Anagrams | Sorted string as key | `Arrays.sort(chars)` |
| 34 | Top K Frequent Elements | Heap or bucket sort | `PriorityQueue` |
| 35 | Encode and Decode Strings | Length prefix | `"4#word"` encoding |

### Hard
| # | Problem | Key Idea | Java Hint |
|---|---|---|---|
| 36 | Trapping Rain Water | Two pointers or stack | `min(leftMax, rightMax) - height[i]` |
| 37 | Sliding Window Maximum | Monotonic deque | `ArrayDeque` stores indices |
| 38 | First Missing Positive | Cyclic sort / index | Place `nums[i]` at index `nums[i]-1` |
| 39 | Median of Two Sorted Arrays | Binary search on partition | O(log(min(m,n))) |
| 40 | Largest Rectangle in Histogram | Monotonic stack | Stack of indices |

---

## 2. Two Pointers & Sliding Window

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 41 | Valid Palindrome | Alphanumeric filter, lo/hi |
| 42 | Squares of a Sorted Array | Two pointers from ends |
| 43 | Is Subsequence | Fast/slow pointers |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 44 | Longest Substring Without Repeating | HashMap + sliding window |
| 45 | Minimum Size Subarray Sum | Variable window, shrink left |
| 46 | Fruit Into Baskets | At most 2 distinct, sliding window |
| 47 | Permutation in String | Fixed window + char freq |
| 48 | Longest Repeating Character Replacement | Window + max freq char |
| 49 | Max Consecutive Ones III | Sliding window with k flips |
| 50 | 4Sum | Sort + two outer loops + two pointers |
| 51 | 3Sum Closest | Sort + two pointers, track diff |
| 52 | Remove Nth Node From End of List | Two pointers, n gap |
| 53 | Minimum Window Substring | Sliding window + HashMap |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 54 | Minimum Window Substring | Two HashMaps, expand/shrink |
| 55 | Substring with Concatenation of All Words | Sliding window + HashMap |
| 56 | Longest Substring with At Most K Distinct | Sliding window + TreeMap |

---

## 3. Binary Search

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 57 | Binary Search | Classic `lo + (hi-lo)/2` |
| 58 | First Bad Version | `lo < hi`, `hi = mid` |
| 59 | Search Insert Position | Lower bound variant |
| 60 | Count Negative Numbers in Matrix | Binary search per row or staircase |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 61 | Find Peak Element | Binary search, compare mid to mid+1 |
| 62 | Search a 2D Matrix | Treat as 1D sorted array |
| 63 | Koko Eating Bananas | Binary search on answer space |
| 64 | Time Based Key-Value Store | Binary search in list of values |
| 65 | Capacity To Ship Packages Within D Days | Binary search on capacity |
| 66 | Find K Closest Elements | Binary search + two pointers |
| 67 | Single Element in Sorted Array | Binary search on even indices |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 68 | Median of Two Sorted Arrays | Partition both arrays |
| 69 | Split Array Largest Sum | Binary search on answer |
| 70 | Find in Mountain Array | Binary search peak then halves |

---

## 4. Linked Lists

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 71 | Reverse Linked List | Iterative: prev/curr/next |
| 72 | Merge Two Sorted Lists | Dummy node + merge |
| 73 | Linked List Cycle | Floyd's slow/fast |
| 74 | Palindrome Linked List | Find mid, reverse second half |
| 75 | Remove Linked List Elements | Dummy head |
| 76 | Middle of Linked List | Slow/fast pointers |
| 77 | Intersection of Two Linked Lists | Align lengths |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 78 | Remove Nth Node From End | Two pointers, n gap |
| 79 | Swap Nodes in Pairs | Recursive or iterative |
| 80 | Add Two Numbers | Carry propagation, dummy head |
| 81 | Odd Even Linked List | Separate odd/even then merge |
| 82 | Reorder List | Find mid, reverse, merge |
| 83 | Rotate List | Find length, k mod len |
| 84 | Copy List with Random Pointer | HashMap old->new node |
| 85 | Sort List | Merge sort on linked list |
| 86 | Partition List | Two dummy heads (less, greater) |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 87 | Reverse Nodes in k-Group | Count k nodes, reverse, recurse |
| 88 | Merge K Sorted Lists | Min-heap of (val, node) |

---

## 5. Stacks & Queues

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 89 | Valid Parentheses | Stack, match pairs |
| 90 | Implement Queue using Stacks | Two stacks (in/out) |
| 91 | Implement Stack using Queues | Single queue rotate |
| 92 | Min Stack | Stack of (val, currentMin) |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 93 | Daily Temperatures | Monotonic stack, store indices |
| 94 | Next Greater Element I | Monotonic stack + HashMap |
| 95 | Next Greater Element II (circular) | Stack, traverse 2n |
| 96 | Evaluate Reverse Polish Notation | Operand stack |
| 97 | Decode String | Stack for count and string |
| 98 | Asteroid Collision | Stack simulation |
| 99 | Remove K Digits | Monotonic stack, greedy |
| 100 | Largest Rectangle in Histogram | Monotonic stack |
| 101 | Car Fleet | Sort by position, stack of speeds |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 102 | Sliding Window Maximum | Monotonic deque |
| 103 | Basic Calculator | Stack for signs + values |
| 104 | Trapping Rain Water | Stack or two pointers |

---

## 6. Trees

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 105 | Maximum Depth of Binary Tree | Recursive DFS |
| 106 | Symmetric Tree | Recursive check mirror |
| 107 | Invert Binary Tree | Swap children recursively |
| 108 | Same Tree | Recursive equality check |
| 109 | Path Sum | DFS, subtract target |
| 110 | Count Complete Tree Nodes | Count left/right height |
| 111 | Diameter of Binary Tree | Track global max in DFS |
| 112 | Balanced Binary Tree | DFS returns height or -1 |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 113 | Binary Tree Level Order Traversal | BFS with size loop |
| 114 | Binary Tree Zigzag Level Order | BFS + alternate direction |
| 115 | Right Side View | BFS last element per level |
| 116 | Validate Binary Search Tree | Pass min/max bounds |
| 117 | Kth Smallest Element in BST | Inorder = sorted |
| 118 | Lowest Common Ancestor BST | Compare val to lo/hi |
| 119 | Lowest Common Ancestor Binary Tree | DFS: found in left or right |
| 120 | Construct Tree from Preorder+Inorder | Recursion + HashMap index |
| 121 | Populating Next Right Pointers | BFS or O(1) space traversal |
| 122 | Flatten Binary Tree to Linked List | Reverse postorder |
| 123 | Binary Tree Maximum Path Sum | DFS, track global max |
| 124 | House Robber III | DP on tree: rob/skip pair |
| 125 | Path Sum II | DFS backtracking |
| 126 | Count Good Nodes | DFS with max so far |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 127 | Binary Tree Maximum Path Sum | Post-order, global max |
| 128 | Serialize and Deserialize Binary Tree | BFS or DFS + delimiters |
| 129 | Vertical Order Traversal | BFS + TreeMap by column |

---

## 7. Heaps / Priority Queue

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 130 | Last Stone Weight | Max-heap |
| 131 | Kth Largest Element in Stream | Min-heap of size k |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 132 | Kth Largest Element in Array | Min-heap or quickselect |
| 133 | Top K Frequent Elements | Min-heap of size k |
| 134 | K Closest Points to Origin | Max-heap of size k |
| 135 | Task Scheduler | Max-heap + greedy |
| 136 | Reorganize String | Max-heap, greedy interleave |
| 137 | Meeting Rooms II | Sort + min-heap of end times |
| 138 | Single Threaded CPU | PriorityQueue by processing time |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 139 | Find Median from Data Stream | Two heaps (lo max, hi min) |
| 140 | Merge K Sorted Lists | Min-heap of (val, node) |
| 141 | Smallest Range Covering K Lists | Max-heap + track min |
| 142 | IPO | Two heaps: available projects |

---

## 8. Hashing

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 143 | Two Sum | HashMap |
| 144 | Valid Anagram | Char frequency array |
| 145 | Isomorphic Strings | Two HashMaps s->t, t->s |
| 146 | Word Pattern | Split + two maps |
| 147 | Happy Number | HashSet cycle detection |
| 148 | Contains Duplicate II | HashMap val->index |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 149 | Group Anagrams | Sorted key in HashMap |
| 150 | 4Sum II | Two-pass HashMap |
| 151 | Longest Arithmetic Subsequence | HashMap dp[i][diff] |
| 152 | Subarray Sum Equals K | Prefix sum HashMap |
| 153 | Continuous Subarray Sum | Prefix sum mod k |
| 154 | LRU Cache | LinkedHashMap or DLL+HashMap |

---

## 9. Dynamic Programming — 1D

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 155 | Climbing Stairs | Fibonacci pattern |
| 156 | House Robber | `dp[i] = max(dp[i-1], dp[i-2]+nums[i])` |
| 157 | Min Cost Climbing Stairs | DP from bottom |
| 158 | Fibonacci Number | DP or math |
| 159 | N-th Tribonacci Number | DP 3 variables |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 160 | Coin Change | Bottom-up DP, min coins |
| 161 | Coin Change II (combinations) | Unbounded knapsack |
| 162 | Word Break | DP boolean array |
| 163 | Decode Ways | DP, handle '0' edge cases |
| 164 | Jump Game | Greedy max reach |
| 165 | House Robber II (circular) | Run robber on [0..n-2] and [1..n-1] |
| 166 | Longest Palindromic Substring | Expand around center |
| 167 | Palindromic Substrings | Count expand around center |
| 168 | Maximum Product Subarray | Track min and max |
| 169 | Perfect Squares | DP min squares |
| 170 | Integer Break | DP or math (3s and 2s) |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 171 | Concatenated Words | DP + Trie |
| 172 | Scramble String | Memoized recursion |

---

## 10. Dynamic Programming — 2D

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 173 | Unique Paths | `dp[i][j] = dp[i-1][j] + dp[i][j-1]` |
| 174 | Unique Paths II (obstacles) | Skip obstacles |
| 175 | Minimum Path Sum | `dp[i][j] = min(up, left) + grid[i][j]` |
| 176 | Longest Common Subsequence | Match or max of skip |
| 177 | Edit Distance | Insert/delete/replace |
| 178 | Maximal Square | `dp[i][j] = min(up,left,diag)+1` |
| 179 | Triangle | Bottom-up DP |
| 180 | Target Sum | DP or DFS with memo |
| 181 | Partition Equal Subset Sum | 0/1 knapsack boolean |
| 182 | Ones and Zeroes | 2D knapsack on m,n |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 183 | Burst Balloons | Interval DP `dp[i][j]` |
| 184 | Strange Printer | Interval DP |
| 185 | Regular Expression Matching | 2D DP with `.*` handling |
| 186 | Wildcard Matching | 2D DP with `?*` handling |
| 187 | Distinct Subsequences | 2D DP count |
| 188 | Dungeon Game | Bottom-right to top-left DP |
| 189 | Cherry Pickup | 3D DP or two simultaneous paths |

---

## 11. Backtracking

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 190 | Subsets | Backtrack include/exclude |
| 191 | Subsets II (duplicates) | Sort + skip same sibling |
| 192 | Permutations | Backtrack with `used[]` array |
| 193 | Permutations II (duplicates) | Sort + skip used duplicate |
| 194 | Combinations | Backtrack with start index |
| 195 | Combination Sum | Allow reuse, start index |
| 196 | Combination Sum II | No reuse, skip duplicates |
| 197 | Combination Sum III | Digits 1-9, size k |
| 198 | Letter Combinations of Phone Number | DFS digit map |
| 199 | Palindrome Partitioning | DFS + isPalindrome check |
| 200 | Generate Parentheses | Track open/close counts |
| 201 | Word Search | DFS + in-place visited mark |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 202 | N-Queens | Row by row, col+diag sets |
| 203 | Sudoku Solver | Backtrack with valid check |
| 204 | Word Search II | Trie + DFS |
| 205 | Expression Add Operators | DFS with prev operand |

---

## 12. Graphs

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 206 | Number of Islands | DFS/BFS flood fill |
| 207 | Max Area of Island | DFS return area |
| 208 | Clone Graph | BFS + HashMap old->new |
| 209 | Pacific Atlantic Water Flow | BFS from both oceans |
| 210 | Course Schedule I | Cycle detection (topological) |
| 211 | Course Schedule II | Topological sort order |
| 212 | Number of Connected Components | Union Find |
| 213 | Graph Valid Tree | Union Find / DFS |
| 214 | Redundant Connection | Union Find |
| 215 | Surrounded Regions | BFS from border 'O's |
| 216 | Rotting Oranges | Multi-source BFS |
| 217 | Walls and Gates | Multi-source BFS |
| 218 | Shortest Path in Binary Matrix | BFS |
| 219 | Open the Lock | BFS state space |
| 220 | Word Ladder | BFS word transformations |
| 221 | Keys and Rooms | DFS/BFS reachability |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 222 | Word Ladder II | BFS + backtrack paths |
| 223 | Alien Dictionary | Topological sort from char pairs |
| 224 | Critical Connections (Bridges) | Tarjan's DFS |
| 225 | Minimum Cost to Connect Points | Kruskal's MST |
| 226 | Network Delay Time | Dijkstra |
| 227 | Swim in Rising Water | Dijkstra or binary search+BFS |
| 228 | Find the City With Fewest Reachable | Floyd-Warshall |

---

## 13. Trie

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 229 | Implement Trie | TrieNode[26] + isEnd |
| 230 | Design Add and Search Words | Trie + DFS for '.' |
| 231 | Replace Words | Trie prefix matching |
| 232 | Map Sum Pairs | Trie with int value |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 233 | Word Search II | Trie + backtracking DFS |
| 234 | Maximum XOR of Two Numbers | Bit Trie |
| 235 | Concatenated Words | Trie + DP |

---

## 14. Greedy

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 236 | Assign Cookies | Sort both, greedy match |
| 237 | Lemonade Change | Track 5s and 10s |
| 238 | Best Time to Buy & Sell Stock II | Collect every upslope |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 239 | Jump Game | Track max reach |
| 240 | Jump Game II | Greedy BFS levels |
| 241 | Gas Station | Total gas >= total cost |
| 242 | Task Scheduler | Max freq char + idle slots |
| 243 | Non-overlapping Intervals | Sort by end, count removals |
| 244 | Minimum Number of Arrows | Sort by end, merge overlaps |
| 245 | Meeting Rooms II | Sort + min-heap of ends |
| 246 | Partition Labels | Last occurrence + greedy |
| 247 | Hand of Straights | HashMap + sorted keys |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 248 | Jump Game III | BFS/DFS from index |
| 249 | Candy | Two-pass greedy |
| 250 | Trapping Rain Water | Two pointers |

---

## 15. Bit Manipulation

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 251 | Single Number | XOR all elements |
| 252 | Number of 1 Bits | `n & (n-1)` trick |
| 253 | Power of Two | `n > 0 && (n & n-1) == 0` |
| 254 | Reverse Bits | Shift and OR 32 times |
| 255 | Missing Number | XOR with indices |
| 256 | Counting Bits | `dp[i] = dp[i>>1] + (i&1)` |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 257 | Single Number II | Count bits mod 3 |
| 258 | Single Number III | XOR then split groups |
| 259 | Bitwise AND of Numbers Range | Find common prefix |
| 260 | Sum of Two Integers | XOR + carry |
| 261 | Subsets | Bitmask enumeration |
| 262 | Maximum XOR of Two Numbers | Bit Trie |

---

## 16. Math & Number Theory

### Easy
| # | Problem | Key Idea |
|---|---|---|
| 263 | Palindrome Number | Reverse half, compare |
| 264 | Happy Number | Floyd's cycle on digit sum |
| 265 | Excel Sheet Column Number | Base-26 |
| 266 | Fizz Buzz | Modulo |
| 267 | Sqrt(x) | Binary search |
| 268 | Count Primes | Sieve of Eratosthenes |

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 269 | Pow(x, n) | Fast exponentiation, handle neg n |
| 270 | Fraction to Recurring Decimal | HashMap remainder->position |
| 271 | Integer to Roman | Greedy subtraction |
| 272 | Roman to Integer | Add or subtract based on next |
| 273 | GCD of Strings | `gcd(len(s1), len(s2))` |
| 274 | Ugly Number II | Three pointers for 2,3,5 |

---

## 17. Design Problems

### Medium
| # | Problem | Key Idea |
|---|---|---|
| 275 | LRU Cache | LinkedHashMap or HashMap + DLL |
| 276 | Min Stack | Stack of (val, min) pairs |
| 277 | Implement Queue with Stacks | Two stacks |
| 278 | Implement Stack with Queues | Rotate queue on push |
| 279 | Design HashMap | Array of LinkedLists |
| 280 | Design HashSet | Array of booleans / LinkedLists |
| 281 | Implement Trie | TrieNode array[26] + isEnd |
| 282 | Design Add and Search Words | Trie + DFS wildcard |
| 283 | Snapshot Array | HashMap of (snap_id, val) per index |
| 284 | Time Based Key-Value Store | HashMap + binary search |

### Hard
| # | Problem | Key Idea |
|---|---|---|
| 285 | LFU Cache | Two HashMaps + freq tracking |
| 286 | Design Twitter | Heap + user follow sets |
| 287 | Serialize / Deserialize Binary Tree | BFS with null markers |
| 288 | Find Median from Data Stream | Two heaps |
| 289 | Design In-Memory File System | Trie of directories/files |
| 290 | Range Sum Query Mutable | Segment tree or BIT |

---

## 18. Sorting & Searching

| # | Problem | Key Idea |
|---|---|---|
| 291 | Sort Colors (Dutch Flag) | 3-way partition |
| 292 | Largest Number | Custom comparator `(b+a).compareTo(a+b)` |
| 293 | Wiggle Sort II | Sort + interleave |
| 294 | H-Index | Sort descending, find crossover |
| 295 | Kth Largest Element | Quickselect O(n) avg |
| 296 | Sort List | Merge sort on linked list |
| 297 | Find K Pairs with Smallest Sums | Min-heap |

---

## 19. Intervals

| # | Problem | Key Idea |
|---|---|---|
| 298 | Merge Intervals | Sort by start |
| 299 | Insert Interval | Find overlap, merge |
| 300 | Non-overlapping Intervals | Sort by end, greedy |
| 301 | Meeting Rooms I | Sort, check overlap |
| 302 | Meeting Rooms II | Min-heap of end times |
| 303 | Minimum Interval to Include Query | Sort + PriorityQueue |

---

## 20. Miscellaneous Hard Problems (Common in FAANG Finals)

| # | Problem | Key Idea |
|---|---|---|
| 304 | Longest Valid Parentheses | Stack or DP |
| 305 | Text Justification | Greedy space distribution |
| 306 | Skyline Problem | Sweep line + max-heap |
| 307 | Russian Doll Envelopes | Sort + LIS (binary search) |
| 308 | Maximum Profit in Job Scheduling | DP + binary search |
| 309 | Number of Ways to Reorder Array | Combinatorics + DFS |
| 310 | Count of Range Sum | Merge sort |

---

## Java Collections Quick Reference

```java
// Which collection to use:

// Fast lookup, no order      → HashMap / HashSet
// Sorted order               → TreeMap / TreeSet
// Insertion order            → LinkedHashMap / LinkedHashSet
// LIFO (stack)               → ArrayDeque  (NOT Stack class)
// FIFO (queue)               → LinkedList / ArrayDeque
// Priority / min-max         → PriorityQueue
// Frequency count            → HashMap<T, Integer>
// Fixed-size sliding window  → ArrayDeque (monotonic)
// Interval overlap           → TreeMap (floorKey / ceilingKey)
```

---

## Complexity Summary

```
O(1)      → HashMap get/put, array index, peek
O(log n)  → Binary search, heap ops, TreeMap ops
O(n)      → Single loop, BFS/DFS, two pointers
O(n log n)→ Sorting, heap sort, merge sort
O(n²)     → Nested loops, naive DP
O(2ⁿ)     → Subsets, recursion branching twice
O(n!)     → Permutations
```

---

## Interview Answer Template (Java)

```java
// 1. Clarify: input constraints, edge cases, return type
// 2. Think out loud: "My approach is..."
// 3. State complexity before coding: "This will be O(n log n) time, O(n) space"
// 4. Code cleanly:

public ReturnType solve(InputType input) {
    // edge case
    if (input == null || input.length == 0) return defaultValue;

    // core logic
    DataStructure ds = new DataStructure();

    for (Element e : input) {
        // process
    }

    return result;
}

// 5. Trace through example
// 6. Mention possible optimizations
```

---

*300+ DSA Questions — FAANG Edition | Java | *
