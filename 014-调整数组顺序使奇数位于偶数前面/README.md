#题意

题目描述

输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，所有的偶数位于位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。

样例输入

5 1 2 3 4 5

样例输出

1 3 5 2 4

下面我们考虑算法复杂度的同时还会考虑其稳定性，（排序的稳定型则是指相同元素在数组中的相对位置是否发生变化），这里的稳定性我们理解为，顺序交换后，各个奇数（或者偶数）在数组中的相对位置是否发生变化

## 不影响顺序　=> 冒泡解法
最简单的思路就是从头到尾扫描一遍数组，每遇见一个偶数时，就拿出这个数字，并把位于这个数字之后的所有数字往前挪动一位,然后把当前这个偶数放到最后。

这样每次遇到一个偶数就要挪动$O(n)$个数字，因此总的时间复杂度是$O(n^2)$

但是这种方法不仅暴力而且还需要复杂的挪动工作，因此我们对比一下冒泡排序，每次循环前偶后奇就交换

同时我们设立一个标识，来标识数组是否已经符合要求

当再次循环时，发现没有要交换的数据，说明数组已经符合要求

## 高效但是影响顺序 => 双指针
由于题目中只要求记奇数在偶数之前，那么我们在扫描这个数组的时候，如果发现一个偶数出现在奇数之前就交换他们的位置，这样一趟后就满足要求了。

因此我们

维护两个索引或者指针，一个指向数组的第一个元素，并向后移动，一个指向数组的最后一个元素，并向前移动。

如果第一个指针指向的元素是偶数，而第二个指针指向的元素是奇数，说明偶数在奇数前面，那么就交换这两个数。

直到两个指针相遇为止