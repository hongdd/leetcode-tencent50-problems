#### day5

##### 盛最多水的容器

> 给定 *n* 个非负整数 *a*1，*a*2，...，*a*n，每个数代表坐标中的一个点 (*i*, *ai*) 。在坐标内画 *n* 条垂直线，垂直线 *i* 的两个端点分别为 (*i*, *ai*) 和 (*i*, 0)。找出其中的两条线，使得它们与 *x* 轴共同构成的容器可以容纳最多的水。
>
> **说明：**你不能倾斜容器，且 *n* 的值至少为 2

```
输入: [1,8,6,2,5,4,8,3,7]
输出: 49
```

这道题真是一点思路都没有！！（主要问题是对题目没有充分理解）

```
垂直的两条线段将会与坐标轴构成一个矩形区域，较短线段的长度将会作为矩形区域的宽度，两线间距将会作为矩形区域的长度，而我们必须最大化该矩形区域的面积。
```

参考了官方的题解：

用双指针,maxarea 表示最大的面积，r从末尾开始向前移动，l从前向末尾移动。当l指向的高度小于r指向的高度的时候，l++，同理r--.

```c++
class Solution {
public:
    int maxArea(vector<int>& height) {
        
        if(height.empty()) return 0;
        int l = 0;
        int r = height.size()-1;
        int maxarea = 0;
        while(l<r)
        {
            maxarea = max(maxarea,min(height[l],height[r])*(r-l));
            if(height[l]<height[r])  l++;
            else r--;
           
        }
        return maxarea;
        
    }
};
```

