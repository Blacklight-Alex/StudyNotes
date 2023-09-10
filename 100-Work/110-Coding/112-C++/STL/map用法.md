# map 用法
1. 包含头文件 `#include <map>`
2. map 是 STL 的一个关联容器，提供一对一的映射关系：第一个成为关键字(key)，每个关键字只能在 map 中出现一次，第二个成为关键字的值(value)。map 内部实现是红黑树，因此很多方法的时间复杂度是 logN。map 中默认对元素按照 key 从小到大进行升序排序 
3. 构造函数 `map<int, string> myMap`
4. 数据插入操作  
	* insert 插入 pair 数据，如果关键字已存在，则插入失败，新的插入操作不生效
	```c++
	    map<int, string> myMap;
	    myMap.insert(pair<int, sring>(1, "one"));
	    myMap.insert(pair<int, sring>(2, "two"));
	    myMap.insert(make_pair(3, "three"));
	    // 判断插入是否成功,pair的第二个变量表示插入是否成功
	    Pair<map<int, string>::iterator, bool> insertPair;
	    insertPair = myMap.insert(pair<int, sring>(2, "two"));
	    if (insertPair.second == true) {
	    // 插入成功
	    }
	```
	*  insert 插入 value_type 数据，用法和上一种 insert 相同
	```c++
	    map<int, string> myMap;
	    myMap.insert(map<int, string>::value_type (1, "one"));
	    myMap.insert(map<int, string>::value_type (2, "two"));
	```
	- 用数组的方式插入，如果关键字已存在，会进行覆盖
	```c++
	    map<int, string> myMap;
	    myMap[1] = "one";
	    myMap[2] = "two";
	```
1. 取值  
	map 中元素取值只要有 at 和[ ]两种操作，at 会检查下标，而[ ]不会
	```c++
	    map<int, string> myMap;
	    myMap.insert(pair<int, sring>(1, "one"));
	    myMap.insert(pair<int, sring>(2, "two"));
	    cout << myMap[3] << endl;        // 不会报错，但打印为空
	    cout << myMap.at(3) << endl;     // at会检查关键字，报错
	```
6. 容量查询
	-  `bool empty`: 查询是否为空
	- `size_t size()`: 查询 map 中键值对的数量
	- `size_t max_size()`: 查询 map 所能包含的最大键值对数量，和系统应用库有关
	- `size_t count(key)`: 查询关键字为key的元素的个数，在map里非0即1，可用于判断数据是否存在
7. 查找元素  
	`iterator find(const key_type& k)`: 关键字查询，找到则返回指向该关键字的迭代器，否则则指向 end 的迭代
8. 数据删除
	-  `iterator erase(iterator pos)`: 删除迭代器指向位置的键值对，并返回一个指向下一个元素的迭代器
	- `iterator erase(iterator first, iterator end)`: 删除一定范围内的元素，并返回指向下一个元素的迭代器
	- `size_t erase(const key_type& key)`: 根据 key 进行删除，返回删除的元素数量，非0即1
	- `void clear()`: 清空 map，清空后 size 为0
	- `void swap(map &other)`: 交换两个 map 中的内容
9. 数据的遍历
	- 应用前向迭代器
	```c++
	    map<int, string> myMap;
	    map<int, string>::iterator iter;
	    for(iter = myMap.begin(); iter != myMap.end(); iter++) {
	        cout << iter->first << "," << iter->second << endl;
	    }
	    for (auto iter : myMap) {
	        cout << iter->first << "," << iter->second << endl;
	    }
	```
	- 应用反向迭代器
	```c++
	    map<int, string> myMap;
	    map<int, string>::reverse_iterator iter;
	    for(iter = myMap.rbegin(); iter != myMap.rend(); iter++) {
	        cout << iter->first << "," << iter->second << endl;
	    }
	```
	- 用数组方式，特定情况下才能使用
	```c++
	    map<int, string> myMap;
	    for (int i = 0; i < myMap.size(); i++) {
	        cout<< myMap[i] << endl;
	    }
	```
10. 排序
	- 默认按照 key 的升序排序，value 随机，默认排序函数 `less<key>`
	- 按照 key 的降序排序 `map<int, string, greater<int>> myMap`
	- 按照结构体排序，自定义排序函数
	```c++
	    typedef struct student {
	        int num;
	        int score;
	    } Student;
	    strcut Cmp {
	        bool operator () (Student const &a, Student const &b) const {
	        // 按照num升序排序，num相等，按照socre升序排序
	            if (a.num != b.num) {
	                return a.num < b.num;
	            } else {
	                return a.score < b.score;
	            }
	        }
	    }
	    map<Student, int, Cmp> myMap;
	```
	- 按照结构体排序，重载<运算符
	```c++
	    typedef struct student {
	        int num;
	        int score;
	        bool operator < (student const &a) const {
	            if (num != a.num) {
	                return num < a.num;
	            } else {
	                return score < a.score;
	            }
	        }
	    } Student;
	    map<Student, int> myMap;
	```
	- 不能使用 sort 进行排序，sort 只能对线性容器排序，不能对关联容器排序