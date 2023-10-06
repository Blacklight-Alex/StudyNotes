# stack 栈的用法
1. Stack（栈）是一种先进后出的数据结构，也就是 LIFO（last in first out），最后加入栈的元素会被最先取出来，在栈的同一端进行数据的插入和取出，这一端叫做栈顶
2. 使用栈需要包含头文件 `#include <stack>`
3. stack 栈常用基本操作如下图：![stack基本操作](stack基本操作.jpg)
4. 构造函数
    默认构造函数为 `template <class T, class Container = deque<T> > class stack`，其中包含2个参数，第1个参数是存储对象的类型，例如建立 int 类型的栈，则第1个参数设置为 int，第2个参数是底层容器的类型，stack 默认的底层容器是 deque 双边队列容器，也可换为其他类型的底层容器，只要他们支持 back ()、push_back ()、pop_back ()、empty ()、size ()等操作
	- 创建空的 stask 对象
	```c++
	    stack<int> myStack;
	```
	- 创建 stack 时，不能使用初始化列表初始化 stack，但可以用另一个容器来初始化
	```c++
	    std::list<double> values {1.414, 3.14159265, 2.71828};
	    std::stack<double,std::list<double>> my_stack (values);
	```
5. `T = stack.top()`：返回栈顶元素，即最后入栈的元素，如果栈为空，返回结果位置
6. `stack.push(const T& obj)`：将新的对象 obj 的副本压入栈顶
7. `stack.pop()`：弹出栈顶元素，即最后入栈的元素，弹出后，栈的大小改变
8. `size_t = stack.size()`：返回栈中元素的个数
9. `bool = stack.empty()`：栈内没有元素返回 true，有元素则返回 false
10. `swap(stack<T> & other_stack)`：将当前栈中的元素和参数中的元素交换。参数所包含元素的类型必须和当前栈的相同
---
参考资料：
1. [C++ STL stack用法](https://blog.51cto.com/u_15077556/4689972)
2. [C++ STL stack用法详解](http://c.biancheng.net/view/478.html)