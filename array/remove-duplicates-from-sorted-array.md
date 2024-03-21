# 26.删除排序数组中的重复项(3.21)

## 题目

给你一个 **非严格递增排列** 的数组 `nums` ，请你**[ 原地](http://baike.baidu.com/item/原地算法)** 删除重复出现的元素，使每个元素 **只出现一次** ，返回删除后数组的新长度。元素的 **相对顺序** 应该保持 **一致** 。然后返回 `nums` 中唯一元素的个数。

考虑 `nums` 的唯一元素的数量为 `k` ，你需要做以下事情确保你的题解可以被通过：

- 更改数组 `nums` ，使 `nums` 的前 `k` 个元素包含唯一元素，并按照它们最初在 `nums` 中出现的顺序排列。`nums` 的其余元素与 `nums` 的大小不重要。
- 返回 `k` 。

## 思路

### 双指针

非严格递增排列是指一个序列中的元素从小到大排列，但是可以有相同的元素。
如果数组长度为0，则直接返回0
如果数组长度大于0，则删除后的数组至少有一个元素，所以数组的第一个元素维持原状即可，所以可以从第二个元素进行筛选删除。
可以声明一个fast指针和一个slow指针都指向第二个元素，fast指针依次遍历数组第二个元素到最后一个元素，来检查元素是不是第一次出现，若元素第一次出现，则将该元素赋给slow指针指向位置，并递增slow指针。（快指针用来检索第一次出现元素，慢指针用来把这些元素排列在一起）

## C

```c
int removeDuplicates(int* nums, int numsSize) {
    int fast = 1,slow = 1;
    if(numsSize == 0)
        return 0;
    while(fast < numsSize)
    {
        if(nums[fast] != nums[fast - 1])
        {
            nums[slow] = nums[fast];
            slow++;
        }
        fast++;
    }
    return slow;
}
```



## 