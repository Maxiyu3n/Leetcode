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

The time complexity of the binarySearch function is O(logn).