[leetcode: squares-of-a-sorted-array](https://leetcode.com/problems/squares-of-a-sorted-array/description/)

Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

Key Points:
1. Initialization:
* left = 0: Starts at the beginning of the array.
* right = len(nums) - 1: Starts at the end of the array.
* res: An array of the same size as nums, initialized with zeros, to store the results.
* index = len(nums) - 1: Position to insert the largest square in res (we fill it from the back).

2. Two-Pointer Approach:
* Since nums is sorted, the largest absolute values are at the ends of the array. Compare abs(nums[left]) and abs(nums[right]) to determine the larger square.
* Place the larger square at res[index].
* Move the left or right pointer inward, depending on which element was chosen.
* Decrease index to fill the next position in res.


3. Stopping Condition:
* The loop runs while left <= right. When left surpasses right, all elements have been processed.
```
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        left = 0 
        right = len(nums) - 1
        res  = [0] * len(nums)
        index = len(nums) - 1
        while left <= right:
            if abs(nums[left]) < abs(nums[right]):
                res[index] = nums[right]**2
                right = right - 1
            else:
                res[index] = nums[left]**2
                left = left + 1
            index = index - 1
        return res

```
Total time complexity:O(n)

Space Complexity:O(n).
No extra auxiliary space is used apart from the pointers and variables.

关于offset不太好理解：offset的意义在于 结束一圈后 起始位置向后移 结束位置向前移。可以画和n=4或者n=5的矩阵，会比较好理解。offset就是由于要去更向内的一圈，内圈元素更少的地方循环，所以循环的次数变少了
