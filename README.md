# 实验名称
使用simd对sm3进行加速

# 实验思路
由于使用simd指令集实现的函数可以做到连续内存中的几个元素进行指令级的并行，所以我使用intrin.h中的
_mm_setr_epi32，_mm_xor_si128，_mm_and_si128，_mm_srli_epi32，_mm_or_si128对sm3算法进行加速

下面给出函数的作用：
_mm_setr_epi32 ():

_mm_xor_si128

_mm_and_si128

_mm_srli_epi32

_mm_or_si128
