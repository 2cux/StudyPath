# 算法-Java

## 1. 数组

### 1.1. 二分查找

二分查找的基本写法

```java
 public static int binarySearch(int[] nums, int target) {
        // 1. 初始化查找区间：左边界left，右边界right（闭区间 [left, right]）
        int left = 0;
        int right = nums.length - 1;

        // 2. 循环查找：只要区间有效（left <= right）就继续
        while (left <= right) {
            // 3. 计算中间索引mid（安全写法，避免溢出）
            int mid = left + ((right - left) >> 1);

            // 4. 核心判断：根据mid值与target的关系缩小区间
            if (nums[mid] == target) {
                return mid; // 找到目标值，直接返回索引
            } else if (nums[mid] < target) {
                // 目标值在右半区间，更新左边界
                left = mid + 1;
            } else {
                // 目标值在左半区间，更新右边界
                right = mid - 1;
            }
        }
     	return -1;
 }
}
```

> 细节补充：>> 1表示右移一位的位运算，在正整数的运算中，等价于除以2向下取整
>
> 不使用left + right的原因是，两者相加的值太大可能会造成整数溢出

> 二分查找有两个前提条件：1. 数据必须是有序的且数据的存储地址是连续的 2. 数据如果重复，就不能区分是第几个数据被查找出来

> 二分查找的两种写法：
>
> 注意，这里的区间和题目所给的数据无关，而是人为编写的二分查找区间规则
>
> 1.左闭右闭区间：初始化right = nums.length - 1，循环条件是while(left <= right)，更新条件right = mid -1
>
> 2.左闭右开区间：初始化right = nums.length,循环条件是while(left < right)，更新条件right = mid

> 有关二分查找的题目：
>
> [704. 二分查找 - 力扣（LeetCode）](https://leetcode.cn/problems/binary-search/)比较简单，就是经典的二分查找题目
>
> [35. 搜索插入位置 - 力扣（LeetCode）](https://leetcode.cn/problems/search-insert-position/description/)就是在第一题的基础上多加了几种情况
>
> [69. x 的平方根 - 力扣（LeetCode）](https://leetcode.cn/problems/sqrtx/)想出用二分查找写并不是很难，但有很多细节需要注意的比如两个数相乘可能会导致整数溢出，在循环里面不能直接写return 不然会直接退出循环*
>
> [367. 有效的完全平方数 - 力扣（LeetCode）](https://leetcode.cn/problems/valid-perfect-square/description/)这题很考验基本功，比如Java中的/和%的意义
>
> [34. 在排序数组中查找元素的第一个和最后一个位置 - 力扣（LeetCode）](https://leetcode.cn/problems/find-first-and-last-position-of-element-in-sorted-array/)Java中返回数组要用 return new int[]{....}*
