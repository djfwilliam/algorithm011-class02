# 学习笔记 #
# 1 深度优先搜索、广度优先搜索 #
**树或图的遍历   **  
- 每个节点都要访问一次  
- 每个节点仅访问一次  
- 对于节点的访问顺序不限  
- 深度优先  
- 广度优先  
- 其他 如优先级搜索  

## 1.1 深度优先搜索 ##
### 模版代码：###
- 递归写法  

```
void dfs(Node node, List<Node> visited) {
    if (visited.contains(node)) {
        // 已经访问过
        return;
    }

    visited.add(node);

    // 处理当前节点
    process(node);

    for (Node nextNode : node.children()) {
        // 如果没有访问过 递归到下一层
        if (!visited.contains(nextNode)) {
            dfs(nextNode, visited);
        }
    }
}```

- 非递归写法

```
void dfs(Node tree) {
    if (tree.root == null) {
        return;
    }
    // 手动维护一个栈
    Stack<Node> stack = new Stack<>();
    stack.push(tree.root);

    while (!stack.empty()) {
        // 出栈 访问节点
        Node node = stack.pop();
        visited.add(node);

        // 处理节点
        process(node);

        // 获取相邻节点 分别压入栈中
        List<Node> nodes = generateRelatedNodes(node);
        for (Node node : nodes) {
            stack.push(node);
        }
    }
}

```

## 1.2 广度优先 ##
由于使用的是队列方式实现，所以没有递归的方法。  

- 模版代码：

```
void bfs(Node graph) {
  if (graph.start == null) {
    return;
  }

  // 维护一个队列
  Queue<Node> queue = new LinkedList<>();
  queue.put(graph.start);

  while (!queue.empty()) {
    // 出队 访问节点
    Node node = queue.poll();
    visited.add(node);

    // 处理节点
    process(node);

    // 获取相邻节点 添加到队列中
    List<Node> nodes = generateRelatedNodes(node);
    for (Node node : nodes) {
      queue.put(node);
    }
  }
}

```

# 2 贪心算法 #
在每一步选择中都采取当前状态下最优的选择，但不一定能得到全局最优解。

贪心算法与动态规划不同的是不能回退，只能做当前局部最优判断。

贪心算法需要证明可以得到全局最优解。

对于贪心算法的题目，可以转化成多种形式，既可以从前向后贪心，也可以从后向前贪心。

# 3 二分查找 #
- 二分查找的前提：

1. 目标函数单调性  
2. 存在上下界  
3. 能够通过索引访问

- 模版代码：

```
public int binarySearch(int[] nums, int target) {
  int left = 0;
  int right = nums.length - 1;
  while (left <= right) {
    int mid = (left + right) / 2;
    if (nums[mid] == target) {
      return mid;
    } else if (nums[mid] < target) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }
  return -1;
}

```
# 4 作业 #
使用二分查找，寻找一个半有序数组中间无序的地方，如输入[4, 5, 6, 7, 0, 1, 2]，输出4  
相似题目：[链接](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/)   

```

public int search(int[] nums) {
    int left = 0;
    int right = nums.length - 1;
    while (left < right) {
        int mid = (right - left) / 2 + left;
        if (nums[mid] <= nums[right]) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    return left;
}

```