# 课程笔记（源自: 代码随想录）
## 思路
* 数组的元素在内存地址中是连续的，不能单独删除数组中的某个元素，只能覆盖。
* 双指针法（快慢指针法):通过⼀个快指针和慢指针在⼀个for循环下完成两个for循环的⼯作。
  * 快指针: 寻找新数组的元素，新数组就是不含有⽬标元素的数组
  * 慢指针: 指向更新新数组下标的位置

## 精华笔记
* 快指针可以理解成在旧数组中找非目标元素，然后赋值给慢指针指向的新数组，虽然都指向一个数组
* 关于二分法和移除元素的共性思考
* 这两题之间有点类似的，他们都是在不断缩小 left 和 right 之间的距离，每次需要判断的都是 left 和 right 之间的数是否满足特定条件。对于「移除元素」这个写法本质上还可以理解为，我们拿 right 的元素也就是右边的元素，去填补 left 元素也就是左边的元素的坑，坑就是 left 从左到右遍历过程中遇到的需要删除的数，因为题目最后说超过数组长度的右边的数可以不用理，所以其实我们的视角是以 left 为主，这样想可能更直观一点。用填补的思想的话可能会修改元素相对位置，这个也是题目所允许的



## 拓展
```
def removeElement(nums, val):
    # Initialize a pointer for the position of valid elements
    slow = 0

    # Iterate through the array
    for fast in range(len(nums)):
        # If the current element is not the target value
        if nums[fast] != val:
            # Copy the element to the 'slow' position
            nums[slow] = nums[fast]
            # Increment the 'slow' pointer
            slow += 1
    
    # Return the new length of the array
    return slow


```


Two Pointers:
* fast pointer: Traverses through the array.
* slow pointer: Tracks the position to overwrite valid elements.

Logic:
* If the current element (nums[fast]) is not equal to the target value val, it's considered valid. Copy this element to the position indicated by slow, then increment slow.

Final State:

* After the loop, all valid elements will be in the first slow positions of the array.
* The length of the modified array is slow.

Return Value:
* The function returns the new length (slow).
