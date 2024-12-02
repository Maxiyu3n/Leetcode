## Notes for Array

### Basic Concepts:
* Array is a collection of items of the same variable type that are stored at contiguous memory locations.
* Array Index: In an array, elements are identified by their indexes. Array index starts from 0. 
* Array element: Elements are items stored in an array and can be accessed by their index.
* Array Length: The length of an array is determined by the number of elements it can contain. 
* Time Complexity:
  * O(1) to insert a single element
  * O(N) to insert all the array elements [where N is the size of the array

### Advantage of Array
* Arrays allow random access to elements. This makes accessing elements by position faster.
* Arrays have better cache locality which makes a pretty big difference in performance.
* Arrays represent multiple data items of the same type using a single name.
* Arrays are used to implement the other data structures like linked lists, stacks, queues, trees, graphs, etc.

### Disadvantages of Array

* As arrays have a fixed size, once the memory is allocated to them, it cannot be increased or decreased, making it impossible to store extra data if required. An array of fixed size is referred to as a static array. 
* Allocating less memory than required to an array leads to loss of data.
* An array is homogeneous in nature so, a single array cannot store values of different data types. 
* Arrays store data in contiguous memory locations, which makes deletion and insertion very difficult to implement. This problem is overcome by implementing linked lists, which allow elements to be accessed sequentially.  

### Array-related problems
* Binary Search: [related problems] (https://algo.itcharge.cn/01.Array/03.Array-Binary-Search/)
* Two Pointers: [related problems] (https://algo.itcharge.cn/01.Array/04.Array-Two-Pointers/)
* sliding window: [related problems] (https://algo.itcharge.cn/01.Array/05.Array-Sliding-Window/)


### 数组理论基础

* ⾸先要知道数组在内存中的存储⽅式，这样才能真正理解数组相关的⾯试题
*  数组是存放在连续内存空间上的相同类型数据的集合。
* 需要注意的几点:
  * 数组下标都是从0开始的。
  * 数组内存空间的地址是连续的，所以我们在删除或者增添元素的时候，就难免要移动其他元素的地
  址。
  * 数组的元素是不能删的，只能覆盖。
*  数组可以⽅便的通过下标索引的⽅式获取到下标下对应的数据。
* 数组的读取时间复杂度为O(1)，插入的时间复杂度为O(n)

