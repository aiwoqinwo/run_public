## reference
* [ByteByteGo_LinkedIn_PDF](https://bytebyte-go.s3.amazonaws.com/ByteByteGo_LinkedIn_PDF.pdf)
* [Grokking the Object Oriented Design Interview](https://akshay-iyangar.github.io/system-design/)
* [system-design-primer](https://github.com/donnemartin/system-design-primer/blob/master/README-zh-Hans.md)
* [1point3acres](https://www.1point3acres.com/bbs/thread-889046-1-1.html)
* [substack](https://quastor.substack.com/)
* [bytebytego](https://bytebytego.com/)
* [star-method](https://lethain.com/star-method/)

## 刷题套路总结
* 做题目先把想法画出来, 然后过一边例子
* 刷题本质是怎么遍历
* [[721](https://leetcode.com/problems/accounts-merge/)] graph 的建立`key: val` vs `val: key` 取决于如何弄 dfs
* [[827](https://leetcode.com/problems/making-a-large-island/)] graph 的题目看看是否可以更改 grid 来 (取代`visited`) 避免用额外的空间
* [[827](https://leetcode.com/problems/making-a-large-island/), [721](https://leetcode.com/problems/accounts-merge/)] graph 的题目信息获取可用原 array 的 index, 尽量不要创造新的 hashset 来增加工作量
* [[1905](https://leetcode.com/problems/count-sub-islands/), [417](https://leetcode.com/problems/pacific-atlantic-water-flow/), [130](https://leetcode.com/problems/surrounded-regions/)] graph 的题目可以考虑遍历两次搞定
* [[1584](https://leetcode.com/problems/min-cost-to-connect-all-points/), [323](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/), [305](https://leetcode.com/problems/number-of-islands-ii/)] union find 的关键是主函数怎么 union 以及 union 函数需要什么功能(目前为止只需要改变 parent, 没有用过 rank)
* [[269](https://leetcode.com/problems/alien-dictionary/), [207](https://leetcode.com/problems/course-schedule/), [Compress 2D Array](https://leetcode.com/discuss/interview-question/326564/Google-or-Onsite-interview-or-Compress-2D-Array/302395)] 拓扑排序的做题顺序: 建图, 然后看看有没有环
* [[1514](https://leetcode.com/problems/path-with-maximum-probability/)] Dijkstra 的实现是通过 graph + heap. `heappush` 是有条件的(通常用一个 array 来维护最短路径), 否则 heap 不可能为空(通过 heap 为空来判断不可行的 case)
* [[518](https://leetcode.com/problems/coin-change-2/), [322](https://leetcode.com/problems/coin-change/), [935](https://leetcode.com/problems/knight-dialer/)] dp/dfs + memo 的重点是: 如何初始化 (dp)/dfs + memo(base case) (base 跟初始化往往是两个极端) 以及如何定义转移方程(根据题意)/如何递归(至触发base case). dp的值或dfs所求往往即为题目所求. 想好函数的输入是啥(要不要加 index 看题目要求)
* [[516](https://leetcode.com/problems/longest-palindromic-subsequence/), [5](https://leetcode.com/problems/longest-palindromic-substring/), [647](https://leetcode.com/problems/palindromic-substrings/)] DP 可用于解 Palindrome 的题目. 用一个二维矩阵储存状态. Palindrome 考虑 1. `dp[i][i]` 2. `dp[i][j]`. `dp[i][j]` 状态取决于`dp[i + 1][j - 1]`. 一般地, 对于`i`的遍历应该从后向前；对于`j`的遍历应该从前向后. 此类问题还可以考虑创建一个`expandFromCenter`的函数, 遍历所有字符即可, 空间复杂度是O(1).
* [[1143](https://leetcode.com/problems/longest-common-subsequence/), [44](https://leetcode.com/problems/wildcard-matching/), [72](https://leetcode.com/problems/edit-distance/)] DP 亦可用于解 common subsequence 的题目, 同样用一个二维矩阵储存状态, 关键是判断什么时候走对角, 什么时候不走对角; 以及 base case 的定义和理解.
* [[300](https://leetcode.com/problems/longest-increasing-subsequence/), [1027](https://leetcode.com/problems/longest-arithmetic-subsequence/), [673](https://leetcode.com/problems/number-of-longest-increasing-subsequence/), [1696](https://leetcode.com/problems/jump-game-vi/)] subsequence 的 dp 需要有两个 pointer, 一个先走(即为所求), 后面那个遍历之前所有并判断与前面pointer的关系. 复杂度基本都为二次方
* [[309](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/), [188](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/), [1235](https://leetcode.com/problems/maximum-profit-in-job-scheduling/)] dfs + memo 往往通过画 decision tree 可想到
* [[212](https://leetcode.com/problems/word-search-ii/), [336](https://leetcode.com/problems/palindrome-pairs/)] 处理 list of strings, 考虑用 Trie: 先建立 TrieNode 和 Trie, 关键是怎么 traverse
* [[211](https://leetcode.com/problems/design-add-and-search-words-data-structure/), [208](https://leetcode.com/problems/implement-trie-prefix-tree/)] `TrieNode` 跟 `Trie` 是两样东西, `TrieNode` 是数据结构, `Trie` 基于 `TrieNode` 且有各种函数
* [[1268](https://leetcode.com/problems/search-suggestions-system/)] Trie 的建立需要不断地调取 `root`, 因为(假设`node = root`) `node` 访问过 `child`, 就回不去了
* [[124](https://leetcode.com/problems/binary-tree-maximum-path-sum/), [450](https://leetcode.com/problems/delete-node-in-a-bst/)] Tree 的题目关键就是两个: 1) base case[复杂的情况需要分类讨论] 2) 怎么做递归[想好: 每一个 node, 函数的输入输出是什么, 是数值还是 boolean]
* [[146](https://leetcode.com/problems/lru-cache/), [143](https://leetcode.com/problems/reorder-list/), [706](https://leetcode.com/problems/design-hashmap/)] LinkedList 几个trick: 1)快慢指针 2)链表翻转 3)合并链表. 合并链表的时候要更改两个链表的指向
* [[560](https://leetcode.com/problems/subarray-sum-equals-k/)] Presum 可用来解决 subarray 的问题. 定义好 hashset 且初始化要记录 0 的情况
* [[939](https://leetcode.com/problems/minimum-area-rectangle/), [2013](https://leetcode.com/problems/detect-squares/)] detect squares / retangeles 的问题往往用到 hashmap, 遍历所有 pair, 通过查看对角线来判断能不能形成, 复杂度不会超过O(n^2)
* [[76](https://leetcode.com/problems/minimum-window-substring/), [1838](https://leetcode.com/problems/frequency-of-the-most-frequent-element/)] Sliding window 关键想好缩短 window 的条件是什么(往往伴有 at most `k` times 的限制, 即 budget)
* [[347](https://leetcode.com/problems/top-k-frequent-elements/), [274](https://leetcode.com/problems/h-index/), [75](https://leetcode.com/problems/sort-colors/)] 帮助建立 counting sort 的 hashmap 里, `{num: frequency}` (也可能反过来), 且需要考虑 tie 的情况
* [[215](https://leetcode.com/problems/kth-largest-element-in-an-array/)] quick sort 的要点是通过 pivot 把数组隔开, 然后通过递归求解. 例如 `[3, 2, 5, 1, 4]`
* [[388](https://leetcode.com/problems/longest-absolute-file-path/), [84](https://leetcode.com/problems/largest-rectangle-in-histogram/), [94](https://leetcode.com/problems/binary-tree-inorder-traversal/), [144](https://leetcode.com/problems/binary-tree-preorder-traversal/), [145](https://leetcode.com/problems/binary-tree-postorder-traversal/)] stack 的问题与最近的深度/高度或者先后次序有关(有待完善)
* [[45](https://leetcode.com/problems/jump-game-ii/), [55](https://leetcode.com/problems/jump-game/)] 贪心算法(Greedy algorithm): 从问题解题过程一步一步按照某个策略取当前的最优值, 并且达到全局最优结果
* 动态规划(DP): 在解决当前问题的时候考虑到之前所有的结果使得过去最优. 因此动态规划得到的是每时每刻的全局最优解, 并且逐步扩大问题规模. 动态规划的精髓是组合子问题.
* 贪心算法在每个阶段即可找出当前最优, 贪心算法也不会考虑当前选择对以后选择的影响. 贪心法比动态规划算法具有更快的运算速度(O(n), 而 DP 则是二次方)
* [[347](https://leetcode.com/problems/top-k-frequent-elements/), [274](https://leetcode.com/problems/h-index/), [407](https://leetcode.com/problems/trapping-rain-water-ii/)] 队列题一般的数据结构 queue 或者 heap, 具体看题目要求(有序/无序等)
* [[126](https://leetcode.com/problems/word-ladder-ii/), [797](https://leetcode.com/problems/all-paths-from-source-to-target/)] bfs 求所有队列的问题的关键是要存好可能的路径和路径最后一个元素
* [[127](https://leetcode.com/problems/word-ladder/)] bfs 也是可以画出树来的, 关键有两个 一设置queue/list, 二别做回头路
* [[199](https://leetcode.com/problems/binary-tree-right-side-view/), [317](https://leetcode.com/problems/shortest-distance-from-all-buildings/)] bfs 的实现可以通过 deque 或者 list 实现, 他们稍有不同
* [[698](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/), [37](https://leetcode.com/problems/sudoku-solver/), [51](https://leetcode.com/problems/n-queens/)] dfs/backtrack 函数如果返回的是boolean, 那么前缩进的代码往往是 1. 定义base case 2. 如果缩进的条件 + 剩余部分的递归函数:`True` 3. 其余情况皆视为`False`
* [[90](https://leetcode.com/problems/subsets-ii/), [47](https://leetcode.com/problems/permutations-ii/), [18](https://leetcode.com/problems/4sum/)] dfs 有两种 1. 选或者不选(start index会变) 2. 加什么数(长度不变)
* [[658](https://leetcode.com/problems/find-k-closest-elements/), [1060](https://leetcode.com/problems/missing-element-in-sorted-array/)] 二分法首先要搞定的是要猜的是什么和怎么找到二分的时间轴, 真做不出来的先写个 linear 的感受一下
* [[34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)] 二分法的另一个要关注的是什么: 1. 找到了目标要不要返回, 返回的条件是什么 2. 如果找不到, 返回的又是是什么
* [[240](https://leetcode.com/problems/search-a-2d-matrix-ii/)] 二分的写法按照模板 1. `l = 0; r = len(nums); while l < r` 2. `l = 0; r = len(nums) - 1; while l <= r`
* [[289](https://leetcode.com/problems/game-of-life/), [130](https://leetcode.com/problems/surrounded-regions/)]省空间的题目, 往往利用原本的数组或者矩阵一小部分来储存原先的状态
* [[1366](https://leetcode.com/problems/rank-teams-by-votes/), [635](https://leetcode.com/problems/design-log-storage-system/)] `sort()` 是根据先后关系依次排序
* [[2002](https://leetcode.com/problems/maximum-product-of-the-length-of-two-palindromic-subsequences/)] bitmask(有待完善)
