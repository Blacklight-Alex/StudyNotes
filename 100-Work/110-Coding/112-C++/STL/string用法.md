# string 用法
1. 头文件  `#include <string>`，放在命名空间 std 下；
2. 构造函数，初始化 string
	- `string str`：声明一个空的 string 对象，长度为0，默认构造函数，后面给 str 赋值时，能够自动调整 str 的长度，比字符串数组安全
	- `string str(const char *s)`：例如 `string str("Hello")` ，将 string 对象初始化为指向 s 指向的字符串
	- `string str(size_type n, char c)`：例如 `string str(10, 'c')`，创建一个包含10个元素的 string 对象，每个元素都为字符 c
	- `string str(const string &str)`：例如 `string str2(str)`，初始化 str2，与对象 str 相等，复制构造函数
	- `string str = "Hello"`：使用 C 语言风格初始化 string 对象
3. 大小函数
	- `int len = string.length()`：获取 string 长度，C 语言风格
	- `int len = string.size()`：获取 string 长度，兼容 STL 风格
	- `string.empty()`：判断 string 对象是否为空，为空返回 true，否则返回 false
4. 复制 string  
		使用=直接复制，string 会自动调整对象的长度，不会出现目标对象长度不够的问题
	```c++
	    string str1("Hello");
	    string str2;
	    str2 = str1;
	```
5. string 对象的拼接
	- 使用 + 拼接两个 string 对象
	```c++
	    string str1("Hello");
	    string str2("World");
	    string str = str1 + str2;
	```
	- 使用 += 操作符可以在 string 对象后面追加内容，追加 string 对象或 C 风格的字符串
	```c++
	    str1 += str2;
	    str1 += "world";
	```
	- 使用 `string.append()` 函数，追加一个 string 对象或 C 风格的字符串
	```c++
	    string.append(str1);
	    string.append("world");
	```
	- 使用 string.push_back ()函数追加1个字符，不能追加 string 对象
	```c++
	    string.push_back('a');
	```
6. string 对象字符串的截取   
		`string substr(size_t pos = 0, size_t len = npos) const`：pos 是字符串起始位置，len 是被截取的字符串的长度，函数的作用是将一个 string 对象从 pos 位置开始后面 len 长度的字符串复制到另一个 string 对象中，并返回该 string 对象；npos 表示的是 string 对象末尾位置，因此 len 不主动赋值时，默认从 pos 起始拷贝到 string 对象的末尾
	```c++
	    string str("hello world");
	    // 从e开始，复制4个字符，截取“ello”
	    string str2 = str.substr(1, 4);
	    // 从e开始，截取后面所有的字符，截取“ello world”
	    string str3 = str.substr(1);
	```
7. 字符串替换，只能替换某个位置连续的字符串
	- 替换指定字符串从指定位置开始一定长度的字符
	```c++
	    string str = "hello world";
	    str = str.replace(1, 1, "ab");   // habllo world
	```
	- 替换指定字符串从迭代器起始位置到迭代器结束位置之间的字符
	```c++
	    string str = "hello world";
	    str = str.replace(str.begin(), str.begin() + 2, "ab");   // abllo world
	```
8. 访问 string 对象中的元素
	- 使用数组下标形式访问 string 对象中的元素
	```c++
	    string str("hello world");
	    cout << str[1] << endl;
	```
	- 使用 at 索引访问 string 中的元素
	```c++
	    string str("hello world");
	    cout << str.at(1) << endl;
	```
9. 查找函数
	- `size_type find (const string& str, size_type pos = 0) const`：  
		从前往后查找字符串，从字符串的 pos 位置开始（若不指定，默认从0开始），从前往后，查找子串 str （也可查找单个字符），若找到，则返回 str 首次出现时首字符的位置索引，若未找到，则返回 string::npos
	- `size_type rfind (const string& str, size_type pos = 0) const`： 
		从后往前查找字符串，用法与 find 函数类似，只不过是从字符串的 pos 位置开始（默认为字符串末尾），从后往前，查找子串 str 出现的位置
	- `string.find_first_of(string &str, size_type pos = 0);`  
		`string.find_first_of(char ch, size_type pos = 0) `:  
		从前往后，从字符串的 pos 位置开始（默认从位置0开始），从前往后，查找子串 str 中的任何一个字符（或者字符 ch）在字符串 string 中第一次出现的位置，若找到，则返回位置索引，若未找到，则返回 string::npos
	- `string.find_last_of(string &str, size_type pos = 0);`  
		从字符串的 pos 位置开始（默认从字符串的末尾开始），从后往前，查找子串 str 中的任何一个字符在字符串 string 中第一次出现的位置，若找到，则返回位置索引，若未找到，则返回 string::npos
	- `string.find_first_not_of(string &str, size_type pos = 0);`  
		从 pos 位置开始，从前往后，在字符串 string 中查找第一个不包含在子串 str 中的字符元素第一次出现的位置索引
	- `string.find_last_not_of(string &str, size_type pos = 0);`  
		从 pos 位置开始，从后往前，在字符串 string 中查找第一个不包含在子串 str 中的字符元素第一次出现的位置索引
10. 插入元素
	- `string &insert (size_t pos，const string &str);`  
		在位置 pos 处插入字符串 str
	- `string &insert (size_t pos, const string &str, size_t subpos, size_t sublen);`  
		在位置 pos 处插入字符串 str 从位置索引 subpos 开始的连续 sublen 个字符
	- `string &insert (size_t pos, const char *s);`  
		在位置索引 pos 处插入字符串 s
	- `string &insert (size_t pos, const char *s, size_t n);`  
		在位置索引 pos 处插入字符串 s 的前 n 个字符
	- `string &insert (size_t pos, size_t n, char c);`  
		在位置索引 pos 处插入 n 个字符 c
	- `iterator insert (const_iterator p, size_t n, char c);`  
		在索引 p 处插入 n 个字符 c，并返回插入后的迭代器的位置
	- `iterator insert (const_iterator p, char c);`  
		在位置 p 处插入字符 c，并返回插入后的迭代器的位置
11. 删除元素
	- `string &erase (size_t pos = 0, size_t len = npos);`   
		删除从 pos 开始的 n 个字符
	- `iterator erase (const_iterator p);`   
		删除 p 处的一个字符，并返回删除后迭代器的位置
	- `iterator erase (const_iterator first, const_iterator last);`   
		删除从迭代器 first 到 last 之间的字符，并返回删除后迭代器的位置
	- `string.pop_back();`   
		删除 string 字符串的最后一个元素
	- `string.clear();`   
		清空 string 的所有元素
12. 反转字符串
		`reverse(str.begin(), str.end());`   
		reverse 函数声明在头文件 `<algorithm>` 中，可以用来反转 string 字符串
13. 交换字符串
		`string.swap(string &str);`   
		交换两个 string 对象中的数据，不用考虑两个 string 大小是否一致，会不会溢出
	```c++
	    cout << "嗨客网(www.haicoder.net)\n" << endl;
	    string str1 = "Hello HaiCoder";
	    string str2 = "Hello World";
	    str1.swap(str2);
	```
---
参考资料：
1. [C++ string类详解](https://www.cnblogs.com/tongye/p/10760154.html)
2. [C++ string swap字符串交换](https://haicoder.net/cpp/cpp-string-swap.html)
3. [C++ string replace函数用法详解](https://blog.csdn.net/haha294182852/article/details/77567437)