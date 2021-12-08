### 旋转数组
给你一个数组，将数组中的元素向右轮转 k 个位置，其中 k 是非负数

 

示例 1:

输入: nums = [1,2,3,4,5,6,7], k = 3
输出: [5,6,7,1,2,3,4]
解释:
向右轮转 1 步: [7,1,2,3,4,5,6]
向右轮转 2 步: [6,7,1,2,3,4,5]
向右轮转 3 步: [5,6,7,1,2,3,4]
示例 2:

输入：nums = [-1,-100,3,99], k = 2
输出：[3,99,-1,-100]
解释: 
向右轮转 1 步: [99,-1,-100,3]
向右轮转 2 步: [3,99,-1,-100]


提示：

```
1 <= nums.length <= 105
-231 <= nums[i] <= 231 - 1
0 <= k <= 105
```




进阶：

尽可能想出更多的解决方案，至少有 三种 不同的方法可以解决这个问题。
你可以使用空间复杂度为 O(1) 的 原地 算法解决这个问题吗？
相关标签
数组
数学
双指针

链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/x2skh7/
来源：力扣（LeetCode）

第一种：删尾补头
思路：每次循环将新数组的最后一个插入到数组的最前面完成K的一次的右轮
代码：
```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function(nums, k) {
    k %= nums.length
    for(let i=0;i<k;i++){
        nums.unshift(nums[nums.length-1])
        nums.pop();
    }
};

```
第二种：数组翻转
思路：先整体翻转，从k个元素后将数组划分左右两个子数组，最后再翻转一次。
解释：第一翻转为了向右轮动的子数组跑到最前面，第二次翻转为了复原数组顺序
代码：
```
    /**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
 var reverse = function(arr,start,end){
     while(start<end){
         [arr[start++],arr[end--]] = [arr[end],arr[start]]
     }
 }
var rotate = function(nums, k) {
    let len =nums.length;
    k %= len;
    if(len>1){
      reverse(nums,0,len-1);
      reverse(nums,0,k-1);
      reverse(nums,k,len-1);
    }else if(len =1){
        return nums
    } else{
        return 0
    }
    
};
```

