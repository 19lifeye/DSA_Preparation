# DSA Roadmap for FAANG — Java Edition

> **Target timeline:** ~6 months | **Language:** Java | **Topics:** 35+

---

## Phase 1 — Foundations & Complexity
**Duration: Weeks 1–2**

### Big O — Time & Space Complexity

```java
// O(1) — Constant time
public int getFirst(int[] arr) {
    return arr[0]; // always one operation, regardless of arr size
}

// O(log n) — Logarithmic (Binary Search)
public int binarySearch(int[] arr, int target) {
    int lo = 0, hi = arr.length - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2; // avoids integer overflow
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1;
}

// O(n) — Linear
public int findMax(int[] arr) {
    int max = arr[0];
    for (int x : arr) max = Math.max(max, x); // n iterations
    return max;
}

// O(n²) — Quadratic (nested loops)
public boolean hasDuplicateSlow(int[] arr) {
    for (int i = 0; i < arr.length; i++)
        for (int j = i + 1; j < arr.length; j++)
            if (arr[i] == arr[j]) return true;
    return false;
}

// O(n) space — cloning array
public int[] cloneArray(int[] arr) {
    return arr.clone(); // new array of size n
}
```

### Complexity Cheat Sheet

| Notation | Name | Java Example |
|---|---|---|
| O(1) | Constant | `arr[i]`, `map.get(key)` |
| O(log n) | Logarithmic | Binary search, tree height |
| O(n) | Linear | For-each loop |
| O(n log n) | Linearithmic | `Arrays.sort()`, merge sort |
| O(n²) | Quadratic | Nested loops |
| O(2ⁿ) | Exponential | Naive recursion, subsets |
| O(n!) | Factorial | Brute-force permutations |

> **Tip:** In Java, `Arrays.sort()` uses dual-pivot quicksort for primitives — O(n log n) average. For objects it uses TimSort — also O(n log n).

---

## Phase 2 — Core Data Structures
**Duration: Weeks 3–6**

### Linked List

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; }
}

// Reverse a linked list — O(n) time, O(1) space
public ListNode reverse(ListNode head) {
    ListNode prev = null, curr = head;
    while (curr != null) {
        ListNode next = curr.next;
        curr.next = prev;
        prev = curr;
        curr = next;
    }
    return prev;
}

// Detect cycle — Floyd's algorithm — O(n) time, O(1) space
public boolean hasCycle(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow == fast) return true;
    }
    return false;
}

// Find middle node — O(n) time, O(1) space
public ListNode findMiddle(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow;
}
```

### Stack & Queue

```java
import java.util.*;

// Stack — Java uses Deque (ArrayDeque preferred over Stack class)
Deque<Integer> stack = new ArrayDeque<>();
stack.push(1);       // push
stack.pop();         // pop
stack.peek();        // top without removing

// Queue
Queue<Integer> queue = new LinkedList<>();
queue.offer(1);      // enqueue
queue.poll();        // dequeue
queue.peek();        // front without removing

// Monotonic stack — Next Greater Element
public int[] nextGreaterElement(int[] nums) {
    int n = nums.length;
    int[] result = new int[n];
    Arrays.fill(result, -1);
    Deque<Integer> stack = new ArrayDeque<>(); // stores indices

    for (int i = 0; i < n; i++) {
        while (!stack.isEmpty() && nums[stack.peek()] < nums[i]) {
            result[stack.pop()] = nums[i];
        }
        stack.push(i);
    }
    return result;
}
```

### Binary Tree

```java
class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int val) { this.val = val; }
}

// Inorder traversal — O(n) time, O(h) space (h = height)
public List<Integer> inorder(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    dfs(root, result);
    return result;
}
private void dfs(TreeNode node, List<Integer> result) {
    if (node == null) return;
    dfs(node.left, result);
    result.add(node.val);      // process node
    dfs(node.right, result);
}

// BFS Level-order traversal — O(n) time, O(n) space
public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> result = new ArrayList<>();
    if (root == null) return result;
    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);
    while (!queue.isEmpty()) {
        int size = queue.size();
        List<Integer> level = new ArrayList<>();
        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();
            level.add(node.val);
            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }
        result.add(level);
    }
    return result;
}

// Max depth — O(n) time, O(h) space
public int maxDepth(TreeNode root) {
    if (root == null) return 0;
    return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
}
```

### Heap / Priority Queue

```java
import java.util.*;

// Min-heap (default in Java)
PriorityQueue<Integer> minHeap = new PriorityQueue<>();

// Max-heap
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());

// Top K largest elements — O(n log k) time, O(k) space
public int[] topKLargest(int[] nums, int k) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    for (int num : nums) {
        minHeap.offer(num);
        if (minHeap.size() > k) minHeap.poll(); // remove smallest
    }
    int[] result = new int[k];
    for (int i = k - 1; i >= 0; i--) result[i] = minHeap.poll();
    return result;
}

// Kth largest element
public int findKthLargest(int[] nums, int k) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    for (int num : nums) {
        minHeap.offer(num);
        if (minHeap.size() > k) minHeap.poll();
    }
    return minHeap.peek();
}
```

### HashMap & HashSet

```java
import java.util.*;

// Common HashMap patterns
Map<Integer, Integer> freq = new HashMap<>();
for (int num : nums)
    freq.put(num, freq.getOrDefault(num, 0) + 1);

// Two Sum — O(n) time, O(n) space
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>(); // value -> index
    for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if (map.containsKey(complement))
            return new int[]{map.get(complement), i};
        map.put(nums[i], i);
    }
    return new int[]{};
}

// HashSet for O(1) lookup
Set<Integer> seen = new HashSet<>();
for (int num : nums) {
    if (!seen.add(num)) return true; // duplicate found
}
```

---

## Phase 3 — Core Algorithms
**Duration: Weeks 7–10**

### Binary Search

```java
// Classic binary search — O(log n)
public int search(int[] nums, int target) {
    int lo = 0, hi = nums.length - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] == target) return mid;
        else if (nums[mid] < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1;
}

// Find leftmost position — O(log n)
public int lowerBound(int[] nums, int target) {
    int lo = 0, hi = nums.length;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] < target) lo = mid + 1;
        else hi = mid;
    }
    return lo;
}

// Binary search on answer space (e.g., Koko eating bananas)
public int minEatingSpeed(int[] piles, int h) {
    int lo = 1, hi = Arrays.stream(piles).max().getAsInt();
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (canFinish(piles, h, mid)) hi = mid;
        else lo = mid + 1;
    }
    return lo;
}
private boolean canFinish(int[] piles, int h, int speed) {
    int hours = 0;
    for (int p : piles) hours += (p + speed - 1) / speed;
    return hours <= h;
}
```

### Two Pointers

```java
// Valid palindrome — O(n) time, O(1) space
public boolean isPalindrome(String s) {
    int lo = 0, hi = s.length() - 1;
    while (lo < hi) {
        while (lo < hi && !Character.isAlphanumeric(s.charAt(lo))) lo++;
        while (lo < hi && !Character.isAlphanumeric(s.charAt(hi))) hi--;
        if (Character.toLowerCase(s.charAt(lo)) !=
            Character.toLowerCase(s.charAt(hi))) return false;
        lo++; hi--;
    }
    return true;
}

// Container with most water — O(n) time, O(1) space
public int maxArea(int[] height) {
    int lo = 0, hi = height.length - 1, max = 0;
    while (lo < hi) {
        max = Math.max(max, Math.min(height[lo], height[hi]) * (hi - lo));
        if (height[lo] < height[hi]) lo++;
        else hi--;
    }
    return max;
}

// 3Sum — O(n²) time, O(1) space
public List<List<Integer>> threeSum(int[] nums) {
    Arrays.sort(nums);
    List<List<Integer>> result = new ArrayList<>();
    for (int i = 0; i < nums.length - 2; i++) {
        if (i > 0 && nums[i] == nums[i - 1]) continue; // skip duplicates
        int lo = i + 1, hi = nums.length - 1;
        while (lo < hi) {
            int sum = nums[i] + nums[lo] + nums[hi];
            if (sum == 0) {
                result.add(Arrays.asList(nums[i], nums[lo], nums[hi]));
                while (lo < hi && nums[lo] == nums[lo + 1]) lo++;
                while (lo < hi && nums[hi] == nums[hi - 1]) hi--;
                lo++; hi--;
            } else if (sum < 0) lo++;
            else hi--;
        }
    }
    return result;
}
```

### Sliding Window

```java
// Longest substring without repeating characters — O(n) time, O(1) space
public int lengthOfLongestSubstring(String s) {
    Map<Character, Integer> map = new HashMap<>();
    int max = 0, left = 0;
    for (int right = 0; right < s.length(); right++) {
        char c = s.charAt(right);
        if (map.containsKey(c))
            left = Math.max(left, map.get(c) + 1);
        map.put(c, right);
        max = Math.max(max, right - left + 1);
    }
    return max;
}

// Maximum sum subarray of size k (fixed window) — O(n) time
public int maxSumSubarray(int[] nums, int k) {
    int sum = 0;
    for (int i = 0; i < k; i++) sum += nums[i];
    int max = sum;
    for (int i = k; i < nums.length; i++) {
        sum += nums[i] - nums[i - k]; // slide: add new, remove old
        max = Math.max(max, sum);
    }
    return max;
}
```

### Backtracking

```java
// Subsets — O(2^n) time
public List<List<Integer>> subsets(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    backtrack(nums, 0, new ArrayList<>(), result);
    return result;
}
private void backtrack(int[] nums, int start, List<Integer> curr,
                        List<List<Integer>> result) {
    result.add(new ArrayList<>(curr));
    for (int i = start; i < nums.length; i++) {
        curr.add(nums[i]);
        backtrack(nums, i + 1, curr, result);
        curr.remove(curr.size() - 1); // undo choice
    }
}

// Permutations — O(n!) time
public List<List<Integer>> permute(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    boolean[] used = new boolean[nums.length];
    backtrack(nums, used, new ArrayList<>(), result);
    return result;
}
private void backtrack(int[] nums, boolean[] used, List<Integer> curr,
                        List<List<Integer>> result) {
    if (curr.size() == nums.length) { result.add(new ArrayList<>(curr)); return; }
    for (int i = 0; i < nums.length; i++) {
        if (used[i]) continue;
        used[i] = true;
        curr.add(nums[i]);
        backtrack(nums, used, curr, result);
        curr.remove(curr.size() - 1);
        used[i] = false;
    }
}
```

### Prefix Sums

```java
// Range sum query — O(1) per query after O(n) preprocessing
int[] prefix = new int[nums.length + 1];
for (int i = 0; i < nums.length; i++)
    prefix[i + 1] = prefix[i] + nums[i];

// Sum of nums[l..r]
int rangeSum(int l, int r) { return prefix[r + 1] - prefix[l]; }

// Subarray sum equals k — O(n) time, O(n) space
public int subarraySum(int[] nums, int k) {
    Map<Integer, Integer> prefixCount = new HashMap<>();
    prefixCount.put(0, 1);
    int sum = 0, count = 0;
    for (int num : nums) {
        sum += num;
        count += prefixCount.getOrDefault(sum - k, 0);
        prefixCount.put(sum, prefixCount.getOrDefault(sum, 0) + 1);
    }
    return count;
}
```

---

## Phase 4 — Dynamic Programming
**Duration: Weeks 11–14**

### 1D DP

```java
// Climbing stairs — O(n) time, O(1) space
public int climbStairs(int n) {
    if (n <= 2) return n;
    int prev2 = 1, prev1 = 2;
    for (int i = 3; i <= n; i++) {
        int curr = prev1 + prev2;
        prev2 = prev1;
        prev1 = curr;
    }
    return prev1;
}

// House robber — O(n) time, O(1) space
public int rob(int[] nums) {
    int prev2 = 0, prev1 = 0;
    for (int num : nums) {
        int curr = Math.max(prev1, prev2 + num);
        prev2 = prev1;
        prev1 = curr;
    }
    return prev1;
}

// Coin change — O(amount * coins) time
public int coinChange(int[] coins, int amount) {
    int[] dp = new int[amount + 1];
    Arrays.fill(dp, amount + 1); // fill with "infinity"
    dp[0] = 0;
    for (int i = 1; i <= amount; i++)
        for (int coin : coins)
            if (coin <= i)
                dp[i] = Math.min(dp[i], dp[i - coin] + 1);
    return dp[amount] > amount ? -1 : dp[amount];
}
```

### 2D DP

```java
// Unique paths — O(m*n) time, O(m*n) space
public int uniquePaths(int m, int n) {
    int[][] dp = new int[m][n];
    for (int[] row : dp) Arrays.fill(row, 1); // top row & left col = 1
    for (int i = 1; i < m; i++)
        for (int j = 1; j < n; j++)
            dp[i][j] = dp[i-1][j] + dp[i][j-1];
    return dp[m-1][n-1];
}

// Longest common subsequence — O(m*n) time
public int longestCommonSubsequence(String text1, String text2) {
    int m = text1.length(), n = text2.length();
    int[][] dp = new int[m + 1][n + 1];
    for (int i = 1; i <= m; i++)
        for (int j = 1; j <= n; j++)
            if (text1.charAt(i-1) == text2.charAt(j-1))
                dp[i][j] = dp[i-1][j-1] + 1;
            else
                dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
    return dp[m][n];
}

// Edit distance — O(m*n) time
public int minDistance(String word1, String word2) {
    int m = word1.length(), n = word2.length();
    int[][] dp = new int[m + 1][n + 1];
    for (int i = 0; i <= m; i++) dp[i][0] = i;
    for (int j = 0; j <= n; j++) dp[0][j] = j;
    for (int i = 1; i <= m; i++)
        for (int j = 1; j <= n; j++)
            if (word1.charAt(i-1) == word2.charAt(j-1))
                dp[i][j] = dp[i-1][j-1];
            else
                dp[i][j] = 1 + Math.min(dp[i-1][j-1],
                                Math.min(dp[i-1][j], dp[i][j-1]));
    return dp[m][n];
}
```

### Knapsack

```java
// 0/1 Knapsack — O(n*W) time, O(n*W) space
public int knapsack(int[] weights, int[] values, int W) {
    int n = weights.length;
    int[][] dp = new int[n + 1][W + 1];
    for (int i = 1; i <= n; i++)
        for (int w = 0; w <= W; w++) {
            dp[i][w] = dp[i-1][w]; // don't take item i
            if (weights[i-1] <= w)
                dp[i][w] = Math.max(dp[i][w],
                                    dp[i-1][w - weights[i-1]] + values[i-1]);
        }
    return dp[n][W];
}

// Longest Increasing Subsequence — O(n log n) with patience sorting
public int lengthOfLIS(int[] nums) {
    List<Integer> tails = new ArrayList<>();
    for (int num : nums) {
        int lo = 0, hi = tails.size();
        while (lo < hi) {
            int mid = lo + (hi - lo) / 2;
            if (tails.get(mid) < num) lo = mid + 1;
            else hi = mid;
        }
        if (lo == tails.size()) tails.add(num);
        else tails.set(lo, num);
    }
    return tails.size();
}
```

---

## Phase 5 — Graphs & Advanced Trees
**Duration: Weeks 15–18**

### Graph Representation

```java
// Adjacency list — most common in interviews
int n = 5; // number of nodes
List<List<Integer>> adj = new ArrayList<>();
for (int i = 0; i < n; i++) adj.add(new ArrayList<>());
adj.get(0).add(1); // edge 0 -> 1
adj.get(1).add(2); // edge 1 -> 2

// From edge list
int[][] edges = {{0,1},{1,2},{2,3}};
for (int[] e : edges) {
    adj.get(e[0]).add(e[1]);
    adj.get(e[1]).add(e[0]); // undirected
}
```

### BFS on Graph

```java
// Number of islands — O(m*n) time
public int numIslands(char[][] grid) {
    int count = 0;
    for (int i = 0; i < grid.length; i++)
        for (int j = 0; j < grid[0].length; j++)
            if (grid[i][j] == '1') { bfs(grid, i, j); count++; }
    return count;
}
private void bfs(char[][] grid, int r, int c) {
    Queue<int[]> queue = new LinkedList<>();
    queue.offer(new int[]{r, c});
    grid[r][c] = '0';
    int[][] dirs = {{0,1},{0,-1},{1,0},{-1,0}};
    while (!queue.isEmpty()) {
        int[] curr = queue.poll();
        for (int[] d : dirs) {
            int nr = curr[0] + d[0], nc = curr[1] + d[1];
            if (nr >= 0 && nr < grid.length && nc >= 0 &&
                nc < grid[0].length && grid[nr][nc] == '1') {
                grid[nr][nc] = '0';
                queue.offer(new int[]{nr, nc});
            }
        }
    }
}
```

### Topological Sort

```java
// Kahn's BFS topological sort — O(V + E)
public int[] topoSort(int numCourses, int[][] prerequisites) {
    int[] inDegree = new int[numCourses];
    List<List<Integer>> adj = new ArrayList<>();
    for (int i = 0; i < numCourses; i++) adj.add(new ArrayList<>());

    for (int[] pre : prerequisites) {
        adj.get(pre[1]).add(pre[0]);
        inDegree[pre[0]]++;
    }

    Queue<Integer> queue = new LinkedList<>();
    for (int i = 0; i < numCourses; i++)
        if (inDegree[i] == 0) queue.offer(i);

    int[] order = new int[numCourses];
    int idx = 0;
    while (!queue.isEmpty()) {
        int node = queue.poll();
        order[idx++] = node;
        for (int neighbor : adj.get(node))
            if (--inDegree[neighbor] == 0) queue.offer(neighbor);
    }
    return idx == numCourses ? order : new int[]{}; // empty if cycle
}
```

### Union Find

```java
class UnionFind {
    int[] parent, rank;

    UnionFind(int n) {
        parent = new int[n];
        rank = new int[n];
        for (int i = 0; i < n; i++) parent[i] = i;
    }

    public int find(int x) {
        if (parent[x] != x)
            parent[x] = find(parent[x]); // path compression
        return parent[x];
    }

    public boolean union(int x, int y) {
        int px = find(x), py = find(y);
        if (px == py) return false; // already connected
        if (rank[px] < rank[py]) { int t = px; px = py; py = t; }
        parent[py] = px;
        if (rank[px] == rank[py]) rank[px]++;
        return true;
    }
}

// Number of connected components
public int countComponents(int n, int[][] edges) {
    UnionFind uf = new UnionFind(n);
    int components = n;
    for (int[] e : edges)
        if (uf.union(e[0], e[1])) components--;
    return components;
}
```

### Dijkstra's Algorithm

```java
// Shortest path — O((V + E) log V) time
public int[] dijkstra(int n, int[][] edges, int src) {
    List<int[]>[] adj = new List[n];
    for (int i = 0; i < n; i++) adj[i] = new ArrayList<>();
    for (int[] e : edges) {
        adj[e[0]].add(new int[]{e[1], e[2]});
        adj[e[1]].add(new int[]{e[0], e[2]});
    }
    int[] dist = new int[n];
    Arrays.fill(dist, Integer.MAX_VALUE);
    dist[src] = 0;
    PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[1] - b[1]);
    pq.offer(new int[]{src, 0});
    while (!pq.isEmpty()) {
        int[] curr = pq.poll();
        int node = curr[0], d = curr[1];
        if (d > dist[node]) continue;
        for (int[] nei : adj[node]) {
            int newDist = dist[node] + nei[1];
            if (newDist < dist[nei[0]]) {
                dist[nei[0]] = newDist;
                pq.offer(new int[]{nei[0], newDist});
            }
        }
    }
    return dist;
}
```

### Trie

```java
class Trie {
    TrieNode root = new TrieNode();

    class TrieNode {
        TrieNode[] children = new TrieNode[26];
        boolean isEnd;
    }

    public void insert(String word) {
        TrieNode node = root;
        for (char c : word.toCharArray()) {
            int idx = c - 'a';
            if (node.children[idx] == null)
                node.children[idx] = new TrieNode();
            node = node.children[idx];
        }
        node.isEnd = true;
    }

    public boolean search(String word) {
        TrieNode node = root;
        for (char c : word.toCharArray()) {
            int idx = c - 'a';
            if (node.children[idx] == null) return false;
            node = node.children[idx];
        }
        return node.isEnd;
    }

    public boolean startsWith(String prefix) {
        TrieNode node = root;
        for (char c : prefix.toCharArray()) {
            int idx = c - 'a';
            if (node.children[idx] == null) return false;
            node = node.children[idx];
        }
        return true;
    }
}
```

---

## Phase 6 — Advanced & FAANG Patterns
**Duration: Weeks 19–24**

### Greedy Algorithms

```java
// Meeting rooms II — minimum conference rooms — O(n log n)
public int minMeetingRooms(int[][] intervals) {
    Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
    PriorityQueue<Integer> ends = new PriorityQueue<>(); // min-heap of end times
    for (int[] interval : intervals) {
        if (!ends.isEmpty() && ends.peek() <= interval[0])
            ends.poll(); // reuse room
        ends.offer(interval[1]);
    }
    return ends.size();
}

// Jump game — O(n) time, O(1) space
public boolean canJump(int[] nums) {
    int maxReach = 0;
    for (int i = 0; i < nums.length; i++) {
        if (i > maxReach) return false;
        maxReach = Math.max(maxReach, i + nums[i]);
    }
    return true;
}
```

### Bit Manipulation

```java
// Count set bits — Brian Kernighan's — O(log n)
public int hammingWeight(int n) {
    int count = 0;
    while (n != 0) { n &= (n - 1); count++; } // clears lowest set bit
    return count;
}

// Single number (XOR trick) — O(n) time, O(1) space
public int singleNumber(int[] nums) {
    int result = 0;
    for (int num : nums) result ^= num; // a ^ a = 0, a ^ 0 = a
    return result;
}

// Power of two check
public boolean isPowerOfTwo(int n) {
    return n > 0 && (n & (n - 1)) == 0;
}

// Get / Set / Clear a bit
int getBit(int n, int i)   { return (n >> i) & 1; }
int setBit(int n, int i)   { return n | (1 << i); }
int clearBit(int n, int i) { return n & ~(1 << i); }
```

### Design Data Structures

```java
// LRU Cache — O(1) get and put using LinkedHashMap
class LRUCache extends LinkedHashMap<Integer, Integer> {
    private int capacity;

    public LRUCache(int capacity) {
        super(capacity, 0.75f, true); // accessOrder = true
        this.capacity = capacity;
    }

    public int get(int key) { return super.getOrDefault(key, -1); }

    public void put(int key, int value) { super.put(key, value); }

    @Override
    protected boolean removeEldestEntry(Map.Entry<Integer, Integer> eldest) {
        return size() > capacity;
    }
}

// LRU Cache — manual implementation with HashMap + Doubly Linked List
class LRUCacheManual {
    private final int capacity;
    private final Map<Integer, Node> map = new HashMap<>();
    private final Node head = new Node(0, 0);
    private final Node tail = new Node(0, 0);

    class Node {
        int key, val;
        Node prev, next;
        Node(int k, int v) { key = k; val = v; }
    }

    public LRUCacheManual(int capacity) {
        this.capacity = capacity;
        head.next = tail;
        tail.prev = head;
    }

    public int get(int key) {
        if (!map.containsKey(key)) return -1;
        Node node = map.get(key);
        remove(node);
        insertFront(node);
        return node.val;
    }

    public void put(int key, int value) {
        if (map.containsKey(key)) remove(map.get(key));
        Node node = new Node(key, value);
        insertFront(node);
        map.put(key, node);
        if (map.size() > capacity) {
            Node lru = tail.prev;
            remove(lru);
            map.remove(lru.key);
        }
    }

    private void remove(Node node) {
        node.prev.next = node.next;
        node.next.prev = node.prev;
    }

    private void insertFront(Node node) {
        node.next = head.next;
        node.prev = head;
        head.next.prev = node;
        head.next = node;
    }
}

// Find median from data stream — O(log n) add, O(1) find
class MedianFinder {
    PriorityQueue<Integer> lo = new PriorityQueue<>(Collections.reverseOrder()); // max-heap
    PriorityQueue<Integer> hi = new PriorityQueue<>(); // min-heap

    public void addNum(int num) {
        lo.offer(num);
        hi.offer(lo.poll());
        if (lo.size() < hi.size()) lo.offer(hi.poll());
    }

    public double findMedian() {
        return lo.size() > hi.size() ? lo.peek() : (lo.peek() + hi.peek()) / 2.0;
    }
}
```

### String Algorithms

```java
// KMP — pattern search — O(n + m) time
public int kmpSearch(String text, String pattern) {
    int n = text.length(), m = pattern.length();
    int[] lps = computeLPS(pattern);
    int i = 0, j = 0;
    while (i < n) {
        if (text.charAt(i) == pattern.charAt(j)) { i++; j++; }
        if (j == m) return i - j; // found
        else if (i < n && text.charAt(i) != pattern.charAt(j)) {
            if (j != 0) j = lps[j - 1];
            else i++;
        }
    }
    return -1;
}
private int[] computeLPS(String pattern) {
    int m = pattern.length();
    int[] lps = new int[m];
    int len = 0, i = 1;
    while (i < m) {
        if (pattern.charAt(i) == pattern.charAt(len)) lps[i++] = ++len;
        else if (len != 0) len = lps[len - 1];
        else lps[i++] = 0;
    }
    return lps;
}
```

---

## Java-Specific Interview Tips

### Key Java Collections

```java
// Common imports you'll always need
import java.util.*;
import java.util.stream.*;

// Sorted structures
TreeMap<Integer, Integer> sortedMap = new TreeMap<>();  // O(log n) ops
TreeSet<Integer> sortedSet = new TreeSet<>();           // O(log n) ops

// Deque as both stack and queue
Deque<Integer> deque = new ArrayDeque<>();
deque.offerFirst(x);  // push front
deque.offerLast(x);   // push back
deque.pollFirst();    // pop front
deque.pollLast();     // pop back

// Sort arrays and collections
Arrays.sort(arr);                                    // O(n log n)
Arrays.sort(arr, (a, b) -> b - a);                  // reverse — for Integer[]
Collections.sort(list, Comparator.reverseOrder());   // collections

// Useful utility methods
Collections.max(list);
Collections.min(list);
Collections.frequency(list, val);
Arrays.fill(dp, Integer.MAX_VALUE);
Arrays.copyOfRange(arr, lo, hi);
```

### Common Interview Pitfalls in Java

| Pitfall | Wrong | Correct |
|---|---|---|
| Integer overflow | `lo + (hi - lo) / 2` — wait, this IS correct | `(lo + hi) / 2` overflows — use `lo + (hi - lo) / 2` |
| Comparing Integer objects | `a == b` | `a.equals(b)` or use `int` |
| Modifying list while iterating | `for (x : list) list.remove(x)` | Use `Iterator` or collect to remove |
| Stack class | `Stack<>` (legacy, synchronized) | `Deque<>` (ArrayDeque preferred) |
| Null in PriorityQueue | `pq.offer(null)` | Not allowed — throws NullPointerException |

---

## Top 20 Must-Know LeetCode Problems (Java)

| # | Problem | Concept | Difficulty |
|---|---|---|---|
| 1 | Two Sum | HashMap | Easy |
| 2 | Best Time to Buy/Sell Stock | Sliding window | Easy |
| 3 | Longest Substring Without Repeating | Sliding window | Medium |
| 4 | Merge Intervals | Sorting + greedy | Medium |
| 5 | Top K Frequent Elements | Heap / bucket sort | Medium |
| 6 | Valid Parentheses | Stack | Easy |
| 7 | Binary Tree Level Order | BFS | Medium |
| 8 | Clone Graph | BFS / DFS | Medium |
| 9 | Course Schedule | Topological sort | Medium |
| 10 | Number of Islands | BFS / DFS | Medium |
| 11 | Coin Change | 1D DP | Medium |
| 12 | House Robber | 1D DP | Medium |
| 13 | Longest Common Subsequence | 2D DP | Medium |
| 14 | Word Break | DP + Trie | Medium |
| 15 | Find Median from Data Stream | Two heaps | Hard |
| 16 | LRU Cache | HashMap + DLL | Medium |
| 17 | Trapping Rain Water | Two pointers / stack | Hard |
| 18 | Word Ladder | BFS | Hard |
| 19 | Serialize/Deserialize Binary Tree | BFS / DFS | Hard |
| 20 | Merge K Sorted Lists | Min-heap | Hard |

---

## Practice Plan

| Phase | Weeks | LeetCode Target |
|---|---|---|
| Foundations + Data Structures | 1–6 | 30–40 problems |
| Core Algorithms | 7–10 | 30–40 problems |
| Dynamic Programming | 11–14 | 25–35 problems |
| Graphs & Advanced Trees | 15–18 | 20–30 problems |
| Advanced Patterns + Mocks | 19–24 | 40–50 problems |

**Total target: 150–200 problems over 6 months**

---

*DSA Roadmap — Java Edition*
