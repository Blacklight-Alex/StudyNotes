# queue 的用法
1. queue（队列）是一种先进先出 FIFO (first in first out)的数据结构，queue 是单边队列，只能在容器的末尾添加新元素，只能从头部移除元素，是一个典型的数据缓冲构造
2. 使用 queue 需要包含头文件 `#include <queue>`
3. queue 常见操作如下图：![queue 基本操作](pic/queue基本操作.jpg)
4. 构造函数
    默认构造函数为 `template <class T, class Container = deque<T> > class queue`，其中包含2个参数，第1个参数是存储对象的类型，例如建立 int 类型的栈，则第1个参数设置为 int，第2个参数是底层容器的类型，queue 默认的底层容器是 deque 双边队列容器，也可替换为其他类型的容器
	- 创建空的 squeue 对象
	```c++
	    // 使默认的deque容器
	    queue<int> myQueue;
	    // 初始化空队列，shiyognlist容器
	    queue<int, std::list<int>> newQueue;
	```
	- 复制另一个容器来初始化 queue
	```c++
	    std::deque<int> mydeck(3, 100);        // 双端队列里初始化3个元素，都是100
	    std::queue<int> myQueue(mydeck);        // 复制 mydeck 的内容初始化队列
	```
5. `bool queue.empty() const`：判断队列元素是否为空，为空，则返回 true
	```c++
	    std::queue<int> myqueue1;
	    bool empty1 = myqueue1.empty(); // true
	    std::queue<int> myqueue2({100,100});
	    bool empty2 = myqueue2.empty(); // false
	```
7. `size_t queue.size() const`：返回队列中元素的个数
8. `reference& queue.front()`：返回队列第一个元素的引用，这个元素是最先加入队列的元素，也是下次 pop 出队的元素；如果 queue 为空，返回值是未定义的
	```c++
	    std::queue<int> myqueue3;
	    myqueue3.push(77);
	    myqueue3.push(66);
	    int& a1 = myqueue3.front(); // 77
	    int a2 = myqueue3.front(); // 77
	    myqueue3.front() = 88; // 给头元素77赋值为88
	    std::cout << "front:" << myqueue3.front() << std::endl; // 输出：88
	```
9. `reference& queue.back()`：返回队列最后一个元素的引用，这个元素是刚 push 进入队列的元素；如果 queue 为空，返回值是未定义的
10. `void queue.push(const value_type& val)`：将一个元素添加的队列的末尾，入队只能从容器尾部入队
11. `void queue.emplace()`：c++11新语法，另一种入队方法，底层调用了 emplace_back 方法
12. `void queue.pop()`：删除队列的第一个元素，出队只能从容器头部出队
13. `void queue.swap(queue& T)`：c++11新语法，交换2个容器
	```c++
	    std::queue<int> teeth;
	    teeth.emplace(4); teeth.emplace(7);
	    std::queue<int> bags;
	    bags.emplace(4); bags.emplace(7); bags.emplace(7);
	    bags.swap(teeth);
	    std::cout << teeth.size() << std::endl; //输出：3
	    std::cout << bags.size() << std::endl; //输出：2
	```
14. 遍历元素：没有迭代器，访问元素的唯一方法是遍历容器内容，并移除访问过得每一个元素
---
1. [C++ queue用法详解](https://zhuanlan.zhihu.com/p/138612411)
2. [C++ STL queue 用法详解](http://c.biancheng.net/view/479.html)
3. [C++ queue使用方法详细介绍](https://blog.csdn.net/weixin_45826022/article/details/103297257)