# set 用法
1. 包含头文件 `#include <set>`
2. 底层实现是采用了红黑树，一种特殊的平衡二叉搜索树，每个元素的值唯一，并且会根据元素的值自动排序
3. 创建对象
	```c++
    set<int> mySet;
	```
4. 插入元素
	* `insert(key)`: 将元素 key 插入到 set 集合中，默认按键值从小到大的顺序插入，返回值是 `pair<set<int>::iterator, bool>`, bool 标志插入是否成功，iterator 代表插入的位置，如果 key 已经存在集合中，则 iterator 表示 key 在集合中的位置，不会重复插入
	* `inset(begin, end)`: 将迭代器 begin 到 end 之间的元素插入到 set 中，返回值是 void
5. 删除元素
	* `erase(key)`: 删除键值 key 所指向的值
	* `erase(begin, end)`:  删除迭代器 begin 和 end 之间的值
	* `erase(iterator)`: 删除迭代器 iterator 指向的值
	* `clear()`: 删除集合中的所有元素
6. 元素检索
	* `find(key)`: 查找键值指向的元素，如果存在，返回所指向的迭代器，如果不存在，返回集合最后一个元素的后面一个位置，即 end ()
	* `count(key)`: 返回键值所代表的元素在集合中的个数，如果不存在，则返回0
	* `empty()`: 如果集合为空，返回 true
	* `max_size()`: 返回 set 集合所能包含的元素最大个数
	* `size()`: 返回当前 set 容器中的元素个数
7. 迭代器
	* `begin()`: 返回指向第一个元素的迭代器
	* `end()`: 返回指向最后一个元素的下一个迭代器
	* `lower_bound(key)`: 返回大于等于键值的第一个元素的迭代器
	* `upper_bound(key)`: 返回第一个大于键值的元素的迭代器
	* `rend`: 返回指向集合中第一个元素的反向迭代器
	* `rbegin()`: 返回指向集合中最后一个元素的反向迭代器
8. 自定义比较函数
	* 默认 less 函数，对键值进行从小到大升序排序
	* 元素不是结构体
	```c++
	    // 自定义比较函数，重载"()"运算符，从大到小排序
	    struct myComp {
	        bool operator() (const int &a, const int &b) {
	            return a > b;
	        }
	    }
	    set<int, myComp> mySet;
	    set<int, myComp>::iterator it;
	```
	- 元素是结构体
	```c++
	    // 重载"<"运算符，自定义排序规则，从大到小降序
	    struct Info {
	        float score;
	        bool operator < (const Info &a) const {
	            return score > a.score;
	        }
	    }
	    set<Info> mySet;
	```
9. 遍历元素
	```c++
    set<int> mySet;
    set<int>::iterator it;
    for (it = mySet.begin(); it != mySet.end(); it++) {
        cout << *it <<endl;
    }
	```