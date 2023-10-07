# queue 的用法
1. queue（队列）是一种先进先出 FIFO (first in first out)的数据结构，queue 是单边队列，只能在容器的末尾添加新元素，只能从头部移除元素，是一个典型的数据缓冲构造
2. 使用 queue 需要包含头文件 `#include <queue>`
3. queue 常见操作如下图：![queue 基本操作](queue基本操作.jpg)
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
6. `size_t queue.size() const`：返回队列中元素的个数
7. `reference& queue.front()`：返回队列第一个元素的引用，这个元素是最先加入队列的元素，也是下次 pop 出队的元素；如果 queue 为空，返回值是未定义的
	```c++
	    std::queue<int> myqueue3;
	    myqueue3.push(77);
	    myqueue3.push(66);
	    int& a1 = myqueue3.front(); // 77
	    int a2 = myqueue3.front(); // 77
	    myqueue3.front() = 88; // 给头元素77赋值为88
	    std::cout << "front:" << myqueue3.front() << std::endl; // 输出：88
	```
8. `reference& queue.back()`：返回队列最后一个元素的引用，这个元素是刚 push 进入队列的元素；如果 queue 为空，返回值是未定义的
9. `void queue.push(const value_type& val)`：将一个元素添加的队列的末尾，入队只能从容器尾部入队
10. `void queue.emplace()`：c++11新语法，另一种入队方法，底层调用了 emplace_back 方法
11. `void queue.pop()`：删除队列的第一个元素，出队只能从容器头部出队
12. `void queue.swap(queue& T)`：c++11新语法，交换2个容器
	```c++
	    std::queue<int> teeth;
	    teeth.emplace(4); teeth.emplace(7);
	    std::queue<int> bags;
	    bags.emplace(4); bags.emplace(7); bags.emplace(7);
	    bags.swap(teeth);
	    std::cout << teeth.size() << std::endl; //输出：3
	    std::cout << bags.size() << std::endl; //输出：2
	```
13. 遍历元素：没有迭代器，访问元素的唯一方法是遍历容器内容，并移除访问过得每一个元素
---
1. [C++ queue用法详解](https://zhuanlan.zhihu.com/p/138612411)
2. [C++ STL queue 用法详解](http://c.biancheng.net/view/479.html)
3. [C++ queue使用方法详细介绍](https://blog.csdn.net/weixin_45826022/article/details/103297257)
---
# priority_queue 用法
1. priority_queue 是优先级队列，底层是用大小根堆实现的，队列内元素按照升序或降序排列，可以用 log (n)的时间动态的维护数据的有序性，适用于许多场景，例如简化哈夫曼树算法
2. 使用 queue 需要包含头文件 `#include <queue>`
3. 构造函数
    默认使用大顶堆初始化，即队首元素是最大的元素的容器
	- 默认初始化 `priority<typename> 容器名称`，即大顶堆
	```c++
	    // 储存int类型数据
	    priority_queue<int> q;
	    // 储存string类型数据
	    priority_queue<string> q;
	    // 储存结构体或者类
	    priority_queue<结构体类型> q;
	```
	- 使用大顶堆或小顶堆初始化 `priority_queue<typename, vector<typename>, 顶堆类型> 容器名`，顶堆类型为 greater，表示大顶堆，队首元素为最大值，顶堆类型为 less，表示小顶堆，队首元素为最小值
	```c++
	    // 使用大顶堆初始化
	    priority_queue<int, vector<int>, greater> q;            // 储存int类型数据
	    priority_queue<string, vector<string>, greater> q;      // 储存string类型数据
	    // 使用小顶堆初始化
	    priority_queue<int, vector<int>, less> q;            // 储存int类型数据
	    priority_queue<string, vector<string>, less> q;      // 储存string类型数据
	```
4. `bool priority_queue.empty() const`：判断队列元素是否为空，为空，则返回 true
	```c++
	    std::priority_queue<int> myqueue;
	    bool empty1 = myqueue.empty(); // true
	```
5. `size_t priority_queue.size() const`：返回队列中元素的个数
6. `const value_type& priority_queue.top() const`：返回队列队首元素的引用，如果是大顶堆，则是队列中元素的最大值，小顶堆则是最小值，时间复杂度为 O (1)
7. `void priority_queue.push(const value_type& val)`：将一个元素插入队列中，然后队列会自动排序，时间复杂度为 O (logN)
8. `void queue.pop()`：删除队列首元素，即堆顶元素，时间复杂度为 O (logN)
9. 存储结构体类型数据，并排序
    由于结构体默认是没有比较大小的功能的，所以不能直接使用优先级队列，需要先定义排序函数，共有两种防范，分别是重载运算符>和<，以及自定义比较函数，重载 () 运算符
	- 重载运算符>和<
	```c++
	    using namespace std;
	    struct fruit{
	        string name;
	        int price;
	        friend bool operator < (fruit f1,fruit f2) {
	            return f1.price > f2.price;
	        }
	     }f1,f2;
	     
	     int main(){
	         priority_queue<fruit> q;
	         f1.name = "桃子";
	         f1.price = 3;
	         f2.name = "梨子";
	         f2.price = 4;
	         q.push(f1);
	         q.push(f2);
	         cout<< q.top().name <<""<<q.top().price << endl;
	         return 0;
	     }
	```
	- 重载运算符>和<，使用 less<>和 greater<>切换大顶堆和小顶堆
	```c++
	     struct test { //定义一个结构体test
	         int val;
	         test(int v) { //构造函数
	             this->val=v;
	         }
	         bool operator > (const test t) const { //重载运算符>
	             return val>t.val;
	         }
	         bool operator < (const test t) const { //重载运算符
	             return val<t.val;
	         }
	     };
	     int main(){
	         priority_queue<test, vector<test>, less<test>> q1;//定义一个小顶堆q1
	         priority_queue<test, vector<test>, greater<test>> q2;//定义一个大顶堆q2
	     }
	```
	- 自定义比较函数，重载 () 运算符，类似 sort 中的自定义排序函数
	```c++
	    struct test { //定义一个结构体test
	         int val;
	         test(int v) { //构造函数
	             this->val=v;
	         }
	         // 默认运算符函数如下，不修改
	         bool operator > (const test t) const { //重载运算符>
	             return val>t.val;
	         }
	         bool operator < (const test t) const { //重载运算符
	             return val<t.val;
	         }
	     };
	     // 自定义比较函数
	     struct cmp{
	         bool operator () (const test t1, const test t2) const { //重载括号运算符
	             return t1.val < t2.val; // 小于号是大根堆，大于号是小根堆
	         }
	     };
	     
	     int main(){
	         //初始化结构体优先级队列
	         priority_queue<test, vector<test>, cmp> q1;
	     }
	```
---
1. [C++ priority_queue用法 入门必看](https://blog.csdn.net/weixin_52115456/article/details/127606811)
2. [C++ 优先队列 priority_queue 使用篇](https://blog.csdn.net/weixin_57761086/article/details/126802156)
3. [C++ 语言中 priority_queue 的常见用法详解 ](https://zhuanlan.zhihu.com/p/478887055)