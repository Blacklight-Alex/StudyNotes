# Vector 用法
1. 包含头文件  `#include <vector>`
2. 构造函数，新建 vector
	-  `vector()`: 创建1个空 vector
	- `vector(int size)`: 创建1个 vector，元素个数为 size
	- `vector(int size, const T &t)`: 创建1个 vector，元素个数为 size，值均为 t
	- `vector(const vector&)`: 复制构造函数
	- `vector(begin, end)`: 复制 \[begin, end)区间内的元素到 vector
3. 增加函数
	- `void push_back(const T &t)`: 向尾部增加元素 t
	- `iterator insert(iterator it, const T &t)`:向迭代器指向元素前在增加1个元素
4. 删除元素
	-  `iterator erase(iterator it)`: 删除迭代器所指向的元素
	- `iterator erase(iterator begin, iterator end)`: 删除区间\[first,end)中的元素
	- `void pop_back()`: 删除向量中最后1个元素
	- `void clear()`: 清空所有元素（内存并未释放）
5. 遍历函数
	-  `reference front()`: 返回首元素的引用
	- `reference back()`: 返回尾元素的引用
	- `iterator begin()`: 返回头指针，指向首元素
	- `iterator end()`: 返回最后一个元素的下一个索引
	- `reference at(int pos)`: 返回pos位置元素的引用
6. 非空判断函数
	  -  `bool empty()`: 判断 vector 是否为空
7. 大小函数
	-  `int size()`: 返回 vector 种元素个数
	- `int capacity()`: 返回当前 vector 所能容纳的最大元素值
	- `resize(int n, const T &t)`: 改变 vector 中元素数目，如果 n 比当前元素数目小，则容量缩减，并删除多余元素，如果 n 比当前元素数目大，则扩充大小，新建元素值为 t，如果没有 t 这个参数，则默认0
	- `reserce(int n)`: 改变vector大小，如果n大于vector当前大小，则分配内存，反之，不做处理

8. 其他函数
	  -  `void swap(vector &)`: 交换两个同类型的 vector，可用来彻底释放内存
	  - `void assign(int n, const T &t)`: 设置vector中前n个元素的值为t
9. 迭代器
	```c++
    vector<int> array;
    vector<int>:: iterator it;
    for (it = array.begin(); it!= array.end(); it++) {
        cout << *it << endl;
    }
	```
10. 定义二维数组（例如5行6列）
	```c++
	// 方法1
	int row = 5, col = 6;
	vector<vector<int>> array(row);
	for (int i = 0; i < array.size(); i++) {
	    array[i].resize(col);
	}
	// 方法2
	vector<vector<int>> array(5, vector<int>(6));
	```
----
参考资料 [C++ Vector容器解析](https://www.runoob.com/w3cnote/cpp-vector-container-analysis.html)
