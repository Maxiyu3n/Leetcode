[leetcode: 704.Binary Search](https://leetcode.com/problems/binary-search/description/)

Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

Key Points:
* The array is a sorted array
* The array contains no duplicate elements

These conditions are the prerequisites for using the binary search method.

The loop invariant rule:
* Every adjustment of the boundaries in the while loop must adhere strictly to the definition of the interval

### Boundary Condition 1: ***[left, right]***

```
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0 
        right = len(nums) - 1

        while left <= right:
            middle = (left+right)//2
            if nums[middle] > target:
                right = middle - 1
            elif nums[middle] < target:
                left = middle + 1
            else:
                return middle
        return -1
```


### Boundary Condition 2: ***[left, right)***
```
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0 
        right = len(nums) 

        while left < right:
            middle = (left+right)//2
            if nums[middle] > target:
                right = middle 
            elif nums[middle] < target:
                left = middle + 1
            else:
                return middle
        return -1

```











## 课程笔记（源自: 代码随想录）
### 思路:
* 这道题⽬的前提是数组为有序数组，同时题⽬还强调数组中⽆重复元素，因为⼀旦有重复元素，使⽤⼆分查找法返回的元素下标可能不是唯⼀的，这些都是使⽤⼆分法的前提条件，当⼤家看到题⽬描述满⾜如上条件的时候，可要想⼀想是不是可以⽤⼆分法了
* ⼤家写⼆分法经常写乱，主要是因为对区间的定义没有想清楚，区间的定义就是不变量。要在⼆分查找的过程中，
保持不变量，就是在while寻找中每⼀次边界的处理都要坚持根据区间的定义来操作，这就是循环不变量规则

### 精华笔记:
* 最重要的就是分类讨论好二分，二分看着好写边界 case 还是需要测试的哈
* 什么是区间不变量？ 比如 区间取左闭右闭的话 那么每次区间二分 范围都是新区间的左闭右闭  后面做判断时  要一直基于这个左闭右闭的区间
* 其实区间定义成开或者闭都没有什么关系  只是要明确每次收缩范围后 范围内的元素是哪些  注意会不会漏掉边界就好
* 大家需要注意二分的几种情况:
  * 当l = 0, r = n的时候因为r这个值我们在数组中无法取到,while(l < r) 是正确写法
  * 当l = 0, r = n - 1的时候因为r这个值我们在数组中可以取到,while(l <= r) 是正确写法 主要看能不能取到这个值
* 二分法有多种写法，末尾是开区间闭区间都可以解出寻找单个元素和寻找边界的题目，只需要注意相应的是l < r还是l <= r,每次取mid还是取mid加减一即可。建议理解后背熟一套模板，不要搞混。
* 其实二分还有很多应用场景，有着许多变体，比如说查找第一个大于target的元素或者第一个满足条件的元素，都是一样的，根据是否满足题目的条件来缩小答案所在的区间，这个就是二分的本质。另外需要注意，二分的使用前提：有序数组
* 二分的最大优势是在于其时间复杂度是O(logn)，因此看到有序数组都要第一时间反问自己是否可以使用二分。
* 关于二分mid溢出问题解答： 
  * mid = (l + r) / 2时，如果l + r 大于 INT_MAX(C++内，就是int整型的上限)，那么就会产生溢出问题（int类型无法表示该数）
  * 所以写成 mid = l + (r - l) / 2或者 mid = l + ((r - l) >> 1) 可以避免溢出问题
* 对于二进制的正数来说，右移x位相当于除以2的x几次方，所以右移一位等于➗2，用位运算的好处是比直接相除的操作快