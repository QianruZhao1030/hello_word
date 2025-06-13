### 两数之和

```javascript
// 哈希表：新建Map，遍历数组nums，map中包含target-nums[i]，返回结果。否则加入map
// new Map([ ["num", 下标]， 。。。 ]);
var twoSum = function(nums, target) {
    const map = new Map()
    for(let i=0; i<nums.length; i++){
        if(map.has(target-nums[i])){
            return [map.get(target-nums[i]), i]
        }else {
            map.set(nums[i], i)
        }
    }
    return []
};
```

### 三数之和 = 0

```javascript
// 排序+双指针O（N2）
var threeSum = function(nums) {
     const res = []
    nums.sort((a,b) => a-b)
    for(let i = 0; i < nums.length; i++) {
        if(nums[i] > 0) break
        if(nums[i] == nums[i-1]) continue //当前数和上一个一样，重重复了
        let L = i + 1
        let R = nums.length - 1
        while(L < R) {
            const sum = nums[i]+nums[L]+nums[R]
            if(sum == 0){
                res.push([nums[i], nums[L], nums[R]])
                if(nums[L+1] == nums[L]) L++
                if(nums[R-1] == nums[R]) R--
                L++
                R--
            }
            else if(sum<0)L++
            else if(sum>0)R--
        }
    }
    return res
};
```

### 数组去重

```javascript
// Set ， 对象无法去重 O(n)
const unique = arr => [...new Set(arr)];

// Map, 可区分引用对象 O(n)
const unique = arr => {
  const map = new Map();
  return arr.filter(item => !map.has(item) && map.set(item, true));
};

// filter + indexOf O(n²) 
const unique = arr => arr.filter((item, index) => arr.indexOf(item) === index);

// reduce 
const unique = arr => arr.reduce((acc, cur) => 
  acc.includes(cur) ? acc : [...acc, cur], []
);

// Object 键值， 可区分类型
function unique(arr) {
  const map = {};
  return arr.filter(item => 
    map.hasOwnProperty(item) ? false : (map[item] = true)
  );
}

// 排序后相邻去重
const unique = arr => {
  arr.sort();
  return arr.filter((item, index) => item !== arr[index - 1]);
};

// 对象数组按属性去重
const uniqueBy = (arr, key) => {
  const seen = new Set();
  return arr.filter(item => 
    !seen.has(item[key]) && seen.add(item[key])
  );
};
```

**reduce：循环遍历**

`arr.reduce((previousValue, item, index, arr) => { **** }, initialValue) `

previousValue：上一次调用回调返回的值，或initialValue 

### 数组扁平化

```javascript
// flat
console.log(arr.flat(Infinity)); // [1, 2, 3, 4, 5]

// 递归
function flatten(arr) {
  return arr.reduce((acc, cur) => 
    Array.isArray(cur) 
      ? [...acc, ...flatten(cur)] 
      : [...acc, cur]
  , []);
}

// toString 仅数字或字符串
const result = arr.toString().split(',').map(Number);
```

### 反转字符串(s是数组)

```javascript
// 左右指针，O(n) 
var reverseString = function(s) {
    let left = 0, right = s.length - 1;
    while (left < right) {
        [s[left], s[right]] = [s[right], s[left]]; //调换位置
        left++;
        right--;
    }
};

// reverse(), 
s.reverse()

```

### 最长无重复子串

给定一个字符串 `s` ，请你找出其中不含有重复字符的 **最长 子串** 的长度。

```javascript
// 滑动窗口（双指针）+ Set ，O(N)
var lengthOfLongestSubstring = function(s) {
    let left=0,right=0, len=0, maxLen =0 
    let set = new Set()
    while(right< s.length){ //右指针滑动范围是字符串长度
        if(!set.has(s[right])){ //set里没有右指针数字，添加到set
            set.add(s[right])
            right++
            len++
            maxLen = Math.max(len, maxLen)
        }else{			//set中有右指针，滑动左指针
            while(set.has(s[right])){ //set中有右指针就滑动左，滑动左会删除set中的值，直到没重复
                set.delete(s[left])
                left++
                len--
            }
            set.add(s[right])
            right++
            len++
        }
    }
    return maxLen
};
```

### 验证回文字符串

大写字符转换为小写字符，移除所有非字母数字字符之后，正着读和反着读一样

```javascript
// 双指针
var isPalindrome = function(s) {
    let left=0, right = s.length-1
    const reg = /[a-zA-Z0-9]/
    while(left< right){
        if(!reg.test(s[left])){ //非字母数字
            left++
            continue
        }
        if(!reg.test(s[right])){ //非字母数字
            right--
            continue
        }
        if(s[left].toLowerCase() !== s[right].toLowerCase()){
            return false
        }  
        left++
        right--    
    }
    return true
};
```

### 最长回文字串

```javascript
// O(n²)中心扩散法，找起始位置和最大长度
var longestPalindrome = function(s) {
    const len = s.length
    if(s.length<2)return s
    let start = 0
    let maxLen = 0
    for(let i=0;i<s.length;i++){
        let L, R
        L = R = i  //奇数    
        while(L>=0 && R<=s.length && s[L] === s[R]){
            if(maxLen< R-L+1){
                start = L
                maxLen = R-L+1
            }            
            L--
            R++
        }
       
        L = i, R = i+1 //偶数 
        while(L>=0 && R<=s.length && s[L] === s[R]){
                if(maxLen< R-L+1){
                start = L
                maxLen = R-L+1
            }            
            L--
            R++
        }
        
    }
    return s.slice(start, start+maxLen)
};
```



### 最大子数组之和

```javascript
// 分治，dp是以每项为结尾的max 
var maxSubArray = function(nums) {
    let dp = [], max = 0;
    dp[0] = nums[0]
    max = dp[0]
    for(let i=1;i<nums.length;i++){
        if(dp[i-1]<0){ // 前一项和为负数，最大就是当前项
            dp[i] = nums[i]
        }else {			// 前一项和为正数数，最大就是当前项+dp[i-1]
            dp[i] = nums[i] + dp[i-1]
        }
        max = Math.max(dp[i], max)
    }
    return max
};
```

### 合并区间

```javascript
// 排序+双指针
var merge = function(intervals) {
    const sortInterval = intervals.sort((a,b) => a[0]-b[0])
    let [left, right] = sortInterval[0]
    const res = []
    for(let i=1;i<sortInterval.length;i++){
        const [newLeft ,newRight] = sortInterval[i]
        if(newLeft>right){ //无重叠，把前面算出来的加入res
            res.push([left, right])
            left = newLeft
            right = newRight      
        }else if(newLeft<=right){ // 有重叠，更新right
            right = Math.max(right, newRight)
        } // 包含，不更新
    }
    res.push([left, right])
    return res
};
```

### 反转链表

```javascript
// 迭代
var reverseList = function(head) {
    let pre = null
    let curr = head
    while(curr){
        const next = curr.next
        curr.next = pre
        pre = curr
        curr = next
    }
    return pre
};

// 递归
var reverseList = function(head) {
    if (head == null || head.next == null) {
        return head;
    }
    const newHead = reverseList(head.next);
    head.next.next = head;
    head.next = null;
    return newHead;
};
```

```javascript
// 部分反转
var reverseBetween = function(head, left, right) {
    const p0 = new ListNode(-1)
    p0.next = head
    let pre = p0
    for(let i = 0;i<left-1; ++i){
        pre = pre.next  //找到left的前一个
    }
    let curr = pre.next
    // 头插法
    for(let i=0;i<right-left; ++i){
        const next = curr.next
        curr.next = next.next
        next.next = pre.next
        pre.next = next
    }
    return p0.next

};
```

![image-20250609114959627](/Users/burst/Library/Application Support/typora-user-images/image-20250609114959627.png)

### 合并两个有序链表

```javascript
// 递归O(n+m)，O(n+m)
var mergeTwoLists = function(list1, list2) {
    if(list1 === null){
        return list2
    }else if(list2 === null){
        return list1
    }else if(list1.val< list2.val){
        list1.next = mergeTwoLists(list1.next, list2)
        return list1
    }else {
        list2.next = mergeTwoLists(list1, list2.next)
        return list2
    }
};

//迭代O(n+m)， O(1)
var mergeTwoLists = function(list1, list2) {
    const p0 = new ListNode(-1)
    let pre = p0
    while(list1!== null && list2 !== null){
        if(list1.val< list2.val){
            pre.next = list1
            list1 = list1.next
        }else {
            pre.next = list2
            list2 = list2.next
        }
        pre = pre.next
    }
    pre.next = list1 === null ? list2 : list1
    return p0.next
};

```

### 爬楼梯dp

```javascript
//O(n)
// 爬上 n−1 阶楼梯的方法数量。因为再爬1阶就能到第n阶
// 爬上 n−2 阶楼梯的方法数量，因为再爬2阶就能到第n阶
var climbStairs = function(n) {
   const dp = []
    dp[0] = 1
    dp[1] = 1
    for(let i = 2;i<=n;i++){
        dp[i] = dp[i-1]+ dp[i-2]
    } 
    return dp[n]
};
```

```javascript
// 最小花费爬，一次1个或2个台阶
var minCostClimbingStairs = function(cost) {
  const dp = []
  dp[0] = dp[1] = 0 //从下标为 0 或下标为 1 的台阶开始爬楼梯。
  for(i=2;i<=cost.length;i++){
    dp[i] = Math.min(dp[i-1]+cost[i-1], dp[i-2]+cost[i-2])
  }
  return dp[cost.length]
};
```



### 打家劫舍dp

```javascript
// 动态规划 ，抢当前+dp[i-2] ｜ 不抢当前
var rob = function(nums) {
    const n = nums.length
    if(n===0) return 0
    if(n===1) return nums[0]
    const dp = [] 
    dp[0] = 0
    dp[1] = nums[0]
    for(let i=2;i<=n;i++){
        dp[i] = Math.max(nums[i-1]+dp[i-2], dp[i-1])
    }
    return dp[n]
};
```

### 最长递增子序列dp

```javascript
// 递归 O(n²)，dp[i]以i项为结尾的最长子序列长度
var lengthOfLIS = function(nums) {
    const dp = new Array(nums.length).fill(1)
    let max = 1
    for(let i = 1;i<nums.length;i++){
       for(let j=0;j<i;j++){
        if(nums[j]< nums[i]){ //能连接成上升子序列
            dp[i] = Math.max(dp[i], dp[j]+1)
        }
       }
       max = Math.max(dp[i], max)
    }
    return max
};
```

### 验证二叉搜索树

```javascript
// 前序 O(n) ，根左右，根左边<根，右边>根，有范围值
var isValidBST = function(root, left = -Infinity, right = Infinity) {
     if(root == null){
        return true
    }else {
        const val = root.val
        return left < val && val < right 
                && isValidBST(root.left, left, val)
                && isValidBST(root.right, val, right)
    }
};

// 中序是递增的 ，左根右， O(n)
var isValidBST = function(root) {
    let pre = -Infinity //前一个指针
    function dfs(node){
        if(!node)return true
        if(!dfs(node.left))return false // 左
        if(node.val<= pre)return false // 中
        pre = node.val
        return dfs(node.right) //右
    }
    return dfs(root)
};

//后序， 左右根 ，O(n)
var isValidBST = function(root) {
  	//dfs 返回子树的最小值和最大值
    function dfs(node){
        if(!node)return [Infinity, -Infinity] //一定不成立的
        const [l_min, l_max] = dfs(node.left)
        const [r_min, r_max] = dfs(node.right)
        const x = node.val
        if(x<= l_max || x>=r_min)return [-Infinity, Infinity]
        return [Math.min(l_min,x), Math.max(r_max, x)]
   }
   return dfs(root)[1] !== Infinity // 无穷大就不是搜索树 
};
```

### 深拷贝

```javascript
function deepCopy(obj, cache = new WeakMap()) {
  if (typeof obj !== 'object' || obj === null) return obj;
  
  // 处理循环引用
  if (cache.has(obj)) return cache.get(obj);
  
  const copy = Array.isArray(obj) ? [] : {};
  cache.set(obj, copy); // 缓存当前对象
  
  for (const key in obj) {
    if (obj.hasOwnProperty(key)) {
      copy[key] = deepCopy(obj[key], cache); // 递归并传递缓存
    }
  }
  
  return copy;
}
```

### dfs深度优先遍历树

```javascript
function dfs(node, visited = new Set()) {
    if (!node || visited.has(node)) return;
    // 处理当前节点
		console.log(node.value);
		visited.add(node);

		// 递归访问所有相邻节点
    for (const neighbor of node.neighbors) {
        dfs(neighbor, visited);
    }
}
```

### LRU(最近最少使用) 缓存

最近最少使用的淘汰，Map.set是在后面加，所以时间最长没用的就是map的第一个元素

```javascript
// 使用 Map保插入顺序，Map 的 key 迭代顺序和生成顺序一致
var LRUCache = function(capacity) {
    this.cache = new Map()
    this.limit = capacity
};

// 访问的时候，删除 key, 然后再次赋值以达到更新该 key 的目的
LRUCache.prototype.get = function(key) {
    let num
    if(this.cache.has(key)){
        num = this.cache.get(key)
        this.cache.delete(key)
        this.cache.set(key, num)
    }
    return num ?? -1
};

// 添加的时候，如果超出容量，利用迭代器获取最早的 key，然后删除
LRUCache.prototype.put = function(key, value) {
    if(this.cache.get(key)){
        this.cache.delete(key)
    }
    this.cache.set(key, value)
    if(this.cache.size > this.limit){
        //keys迭代，next返回第一个{value: 'key2', done: false}
        this.cache.delete(this.cache.keys().next().value) 
    }
};
```

