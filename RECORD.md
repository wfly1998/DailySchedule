# 重点知识笔记

## AcWing 算法基础课

### 动态规划

#### 背包 dp

##### 01 背包

*每个物品最多用一次*

DP：

* 状态表示 *f(i, j)*：决定需要几个维度表示一个状态
  * 状态集合：所有状态构成的集合
    * 所有选法的集合
	* 条件
	  1. 只从前 *i* 个物品里选
	  2. 总体积 <= *j*
  * 状态属性：**最大值**、最小值、数量
* 状态计算 *f(N, V)*：集合划分
  * 不包含第 *i* 个物品：*f(i-1, j)*
  * 包含第 *i* 个物品：*f(i-1, j-v[i]) + w[i]*
  * => *f(i, j) = max( f(i-1,j), f(i-1,j-v[i])+w[i] )*

DP 优化：对状态做等价变形

状态：未知数

##### 完全背包

*每个物品可以用无限次*

* 状态计算：
  * 不包含第 *i* 个物品：*f(i-1, j)*
  * 包含第 *i* 个物品 *k* 个：*f(i-1, j-k\*v[i]) + k\*w[i]*
  * => *f(i, j) = max( f(i-1,j), f(i-1,j-v[i])+w[i] )*

##### 多重背包

*每个物品最多用 Si 次*

##### 分组背包

*每组最多选 Si 个*

#### 线性 dp

#### 区间 dp

#### 计数 dp

#### 数位 dp

#### 状压 dp
