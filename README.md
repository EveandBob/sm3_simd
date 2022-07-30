# 实验名称
使用simd对sm3进行加速

# 实验思路
由于使用simd指令集实现的函数可以做到连续内存中的几个元素进行指令级的并行，所以我使用intrin.h中的
_mm_setr_epi32，_mm_xor_si128，_mm_and_si128，_mm_srli_epi32，_mm_or_si128对sm3算法进行加速

在本次实验中我主要加速的地方为对W的赋值操作，部分代码如下：
![Screenshot 2022-07-31 065058](https://user-images.githubusercontent.com/104854836/182002900-69aad809-d5c9-4dbc-b4ca-2acbe6556a7f.jpg)
值得注意的是，由于对W进行赋值时，有一项为W[i-3],这样我们就需要提前算一项，虽然会带来时间开销，但是这与四路指令集优化带来的加速相比是值得的

#实验结果
在本次加密中我选择的明文为“abc”

结果如下：
![Screenshot 2022-07-31 065549](https://user-images.githubusercontent.com/104854836/182002939-5d451b02-6d0c-4fb7-ae4d-34b8594aa352.jpg)

可以看到SIMD实现和普通实现得到的结果是相同的，可以看出代码的正确性

可以看到SIMD优化带来了20%的加速
