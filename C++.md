C++

头文件

**stl的万能头文件#include <bits/stdc++.h>**

数学文件，#include<cmath>



~~~c++
#include<iostream>
using namespace std;

int main(){
	int a,b;
	cout<<"hello world"<<endl;//输出 
	printf("你好\n");
	cin>>a>>b;//输入 
	cout<<"a="<<a<<endl;
	cout<<"b="<<b<<endl;
	cout<<"a++="<<a++<<endl;
	a--;
	cout<<"++a="<<++a<<endl;
	cout<<setw(5)<<setprecision(8)<<3.14159265354<<endl;//输出3.14，setprecision保留小数点的位数（包括小数点），比如此处输出3.14 。
										//setw（n）表示域宽，总共几位数 .主要权力还是在setprecision
	return 0; 
} 
~~~

~~~

~~~

setw()和setprecision()需要头文件声明#include<iomanip>

## 指针与数组

直接看C语言就行了。输出时用C语言的就行。不必c++。

## 数据结构和算法再看看



## int等等表示范围

## STL

### 容器

**使用不同容器，头文件包含不同容器名**

~~~c++
#include<vector>
#include<deque>
#include<list>
#include<set>
#include<map>
~~~



顺序容器

向量(vector)、双端队列(deque)、列表(list)、队列（queue）



关联容器

集合(set)、多重集合(multiset)、映射(map)、多重映射(multimap)

### 迭代器

使用独立于stl的迭代器，头文件#include<iterator>，相当于指针用法。



### 函数对象

使用stl的函数对象，需要包含头文件#include<functional>







### 算法

使用stl的算法，需要包含头文件#include<algorithm>



栈，#include<stack>

队列，#include<queue>

**辗转相减法比辗转相除法简单**

~~~c++
#include<iostream>
using namespace std;
/*最小公倍数*/
short least_common_multiple(short a, short b){
   short s = a*b;
   while(a != b)
	{
		if(a>b)
		{
			a = a - b;
		}
		else 
		{
			b = b - a;
		}
	}
   
   return s/a;
}
int main()
{
    short a, b, c;
    short t1, t2;//最大公约数
    scanf("%d %d %d", &a, &b, &c);
    t1 = least_common_multiple(a, b);
    t2 = least_common_multiple(t1, c);
    printf("%d", t2);
    return 0;
}
~~~





如何把地图数据放入代码中是一个问题，一般用文本替换。就是一道经典的寻路问题，比赛的时候用的 DFS，程序运行了近 1 小时都没得出答案。。。最后还爆栈了，这么大的数据量早该想到的，换用 BFS，因为 BFS 得到的解总是最优解，即步数最少的解，那么我们在遍历的时候按照字典序从小到大的顺序进行四个方向遍历进行了：



数据结构和算法分析看看。

## 二叉树



## 深度和广度优先遍历

## STL的常见用法

### 1、选择C++刷算法的理由

- C++速度快
- C++有STL--使用很方便的类库
- 如何使用STL进行高效刷算法
- 刷算法，成本极低
- 如何从C到C++（仅基础语法到刷算法程度）

~~~
俗话说：磨刀不误砍柴工
不会c++仍然可以做，但是效率低
~~~



### 2、输入输出

C++保留了C的scanf和printf，增加了额外的cin与cout

例子

#### 2.1、C程序中输入输出

~~~c
int a;
scanf("%d",&a);
printf("%d",a);
~~~

#### 2.2、c++输入输出

~~~c++
int a;
cin>>a;
cout<<a;
~~~

#### 2.3、连续输入输出变量

~~~c++
int a,b,c;
cin>>a>>b>>c;
cout<<a<<b<<c;
~~~

#### 2.4、优雅地换行

~~~c++
cout<<1;
cout<<endl;
cout<<2;
cout<<3<<endl<<endl;
~~~

好处：

1.少写了很多东西

2.连续输入输出变量

3.换行优雅

~~~
注意：cin、cout比scanf、printf慢，有时候刷算法超时，可能因为使用了cin、cout

输入输出的数量(>1000)特别多，刷算法用cin，cout容易超时
~~~

### 3、STL(Standard Template Library)与algorithm头文件

STL是一些“容器”的集合，这些“容器”有list,vector,set,map等，STL也是算法和其他一些组件的集合。

algorithm是对容器继承的一些算法函数，辅助刷算法题

sort函数位于algorithm头文件中

概念：**迭代器——理解为指针**

~~~c++
#include <iostream>
#include <algorithm>

using namespace std;

int main()
{
    int a[]={2,1,5,0,-1,5,9};
    sort(a,a+7);//第一个是头指针
    for(int i=0;i<7;i++)
        cout<<a[i]<<" ";
    cout<<endl;
    system("pause");
    return 0;
}
~~~

### 4、STL——string(*)

概念：相当于char*的封装，理解为字符串

#### 4.1、简单使用

~~~c++
/**C中定义字符串以及打印*/
char *ch="asdkajbf";
for(int i=0;ch[i]!='\0';i++) cout<<*(ch+i);
/**C++中*/
string s="ssadaffw";
cout<<s<<endl;
~~~

#### 4.2、获取一行字符串

hello world

C中：

~~~c
scanf("%s",ch);//1.仅获取一个单词，空格结束 2.ch[100]得设置初始大小
~~~

C++中：

~~~c++
string s;
getline(cin,s);//获取一行数据
cout<<s;
~~~

#### 4.3、+=运算符

+=对于字符串，字符有效，数字会转为asc码

~~~c++
string s;
s+="hello";
s+=" world";
s+='5';
s+=10;//10对应的asc码是换行
int a=5;//想把a加入字符串
s+=(a+'0');
cout<<s;
~~~

#### 4.4、排序（使用algorithm）

~~~c++
string s="5418340";
sort(s.begin(),s.end());
cout<<s;
~~~

#### 4.5、erase函数

~~~c++
/**begin是头迭代器，end是尾迭代器*/
string s="5418340";
s.erase(s.begin());//删除第一个
s.erase(--s.end());//删除最后一个
cout<<s;
~~~

**c++中所有指向end的都是指向end的下一个数。**

#### 4.6、substr函数

~~~c++
/**begin是头迭代器，end是尾迭代器*/
string s="5418340";
s=s.substr(1,3);//取418,取索引为1，往后截断3个
s=s.substr(1,-1);//索引为1，截断到最后
cout<<s;
~~~

#### 4.7、循环（3种）

1.for循环

~~~c++
string s="5418340";
for(int i=0;i<s.length();i++) cout<<s[i];
~~~

2.迭代器（**把它看作指针，下面的it**）

~~~c++
for(string::iterator it=s.begin();it!=s.end();it++) cout<<*it;
~~~

3.迭代器化简

~~~c++
for(auto it=s.begin();it!=s.end();it++) cout<<*it;
~~~

4.利用C++11新特性for循环

~~~c++
for(auto x:s) cout<<x;
~~~

### 5、STL——vector(*)

概念：vector相当于数组，模板类型相当于存放的内容

1.vector构造

~~~c++
vector<int> v;//定义一个空vector
vector<int> v2(4);//定义一个4个大小的vector，初始为0
vector<int> v3(4,6);//定义一个4个大小的vector，初始为6
vector<int> v{1,2,3,4,5};//定义一个vector，数字为1,2，3,4,5
for(auto x:v3) cout<<x;
~~~

2.用at或者[]获取元素

~~~c++
vector<int> v{1,2,3,4,5};
cout<<v[1];//取索引为1的
cout<<v.at(2);//取索引为2的
~~~

3.方法

- push_back追加内容

  

  ~~~c++
  vector<int> v;
  v.push_back(5);
  v.push_back(5);
  v.push_back(5);
  v.push_back(5);
  v.push_back(6);
  for(auto x:v) cout<<x;
  ~~~

  resize进行重置大小

~~~c++
v.resize(10);//不赋值默认为0
~~~

- erase删除元素，复杂度为O(n)

  ~~~c++
  v.erase(v.begin());//删除第一个元素
  v.erase(--v.end());//删除最后一个元素
  ~~~

  获取第一个元素，获取最后一个元素

~~~C++
/**获取第一个元素*/
cout<<v.front();
cout<<v[0];
cout<<*v.begin();
/**获取最后一个元素*/
cout<<v.back();
cout<<v[v.size()-1];//size是获取大小
cout<<*--v.end();
~~~

4.排序

第三个参数为比较器，不写默认为less<int>()

~~~C++
vector<int> v{5,1,2,5,4,0,-1};
sort(v.begin(),v.end(),less<int>());//从小到大
sort(v.begin(),v.end(),greater<int>());//从大到小排序
for(auto x:v) cout<<x;
~~~

5.循环

~~~C++
vector<int> v{5,1,2,5,4,0,-1};
for(int i=0;i<v.size();i++) cout<<v[i];//for循环
cout<<endl;
for(vector<int>::iterator it=v.begin();it!=v.end();it++) cout<<*it;//迭代器循环
cout<<endl;
for(auto it=v.begin();it!=v.end();it++) cout<<*it;//迭代器简化循环
cout<<endl;
for(auto x:v) cout<<x;//c++11新特性
~~~

### 6、STL——stack(*)

概念：栈

​	构造

~~~c++
stack<int> s;
~~~

- push、pop、size、empty
- push 入栈一个元素
- pop 出栈一个元素，pop无返回值
- top 取栈顶元素,返回栈顶元素
- size 查看元素个数

~~~C++
s.push(2);
s.push(3);
cout<<s.top()<<endl;
s.pop();
cout<<s.top()<<endl;
cout<<s.size()<<endl;
~~~

**进制转换(十进制转二进制)**

~~~C++
int itob(int decimal){
    stack<int> s;int res=0;
    while(decimal!=0){
        s.push(decimal%2);
        decimal/=2;
    }
    while(!s.empty()){
        res=res*10+s.top();
        s.pop();
    }
    return res;
}
~~~

**逆序单词**（拓展sstream，stoi，itoa）

输入一行字符串，将字符串逆序打印

输入：hello world my name is steve yu

输出：yu steve is name my world hello

~~~C++
#include <iostream>
#include <stack>
#include <sstream>

using namespace std;

int main(){
    string str;
    stack<string> s;
    getline(cin,str);
    stringstream ss;
    ss<<str;
    while(ss>>str)
        s.push(str);
    while(!s.empty()){
        cout<<s.top();
        s.pop();
        if(s.size()!=0) cout<<" ";
    }
    return 0;
}
~~~

- 字符串转数字

方法1:

~~~C++
string s="1234";
 int i;
 stringstream ss;
 ss<<s;
 ss>>i;
 cout<<i;
~~~

方法2:

~~~C++
string s="1234";
int i=stoi(s);
cout<<i;
~~~

- 数字转字符串

方法1:

~~~c++
int a=1234;
string out;
stringstream ss;
ss<<a;
ss>>out;
cout<<out<<endl;

~~~

方法2:(c++ 11)

~~~C++
int a=1234;
cout<<to_string(a)<<endl;
~~~

### 7、STL——queue

概念：队列

构造

~~~c++
queue<int> q;
~~~

push、back

~~~C++
q.push(5);
q.push(6);
cout<<q.front()<<endl;
q.pop();
cout<<q.front()<<endl;
cout<<q.size()<<endl;
~~~

### 8、STL——map(unordered_map pair)

概念：映射（map为树状表，unorderedmap为哈希表）

map树状表

~~~C++
map<int,int> m;//有序的，树状结构（底层）
m[6]=3;
m[5]=8;
m[4]=9;
for(auto it=m.begin();it!=m.end();it++)
	cout<<it->first<<" "<<it->second<<endl;
for(auto tmp:m){
	cout<<tmp.first<<" "<<tmp.second<<endl;
}
~~~

unordered_map哈希表

~~~C++
unordered_map<int,int> m;//无序的，哈希结构（底层）
m[6]=3;
m[5]=8;
m[4]=9;
for(auto it=m.begin();it!=m.end();it++)
	cout<<it->first<<" "<<it->second<<endl;
for(auto tmp:m){
	cout<<tmp.first<<" "<<tmp.second<<endl;
}
~~~

pair的用法(map转成vector进行排序)

~~~c++
bool cmp(pair<int,int> a,pair<int,int> b){
    return a.first>b.first;
}
int main(){
    unordered_map<int,int> m;//无序的，哈希结构（底层）
    m[6]=3;
    m[5]=8;
    m[4]=9;
    vector<pair<int,int>> v(m.begin(),m.end());
    sort(v.begin(),v.end(),cmp);
    for(auto tmp:v){
        cout<<tmp.first<<tmp.second<<endl;
    }
    return 0;
}
~~~

### 9、set(unordered_set)

概念：集合

应用计数、去重

~~~C++
set<int> s;//树状结构，有序
unordered_set<int> s2;//哈希结构，无序，快
s.insert(3);
s.insert(4);
s.insert(4);
s.insert(4);
cout<<s.size()<<endl;
for(auto tmp:s)
	cout<<tmp<<" ";
cout<<endl;
for(auto it=s.begin();it!=s.end();it++)
	cout<<*it<<" ";
cout<<endl;
~~~

### 10、STL——deque

概念：双端队列

~~~C++
deque<int> d;
// 4 9 1 2
d.push_back(1);
d.push_back(2);
d.push_front(9);
d.push_front(4);
d.pop_back();
d.pop_front();
for(auto tmp:d) cout<<tmp<<endl;
for(auto it=d.begin();it!=d.end();it++) cout<<*it<<endl;
~~~

排序

~~~C++
sort(d.begin(),d.end(),greater<int>());
~~~

### 11、STL——list

概念：双向链表

~~~C++
list<int> li;
li.push_back(6);
li.push_front(5);
li.emplace_front(9);
li.emplace_back(10);
li.insert(++li.begin(),2);
for(auto tmp:li) cout<<tmp<<endl;
for(auto it=li.begin();it!=li.end();it++) cout<<*it<<endl;
~~~

### 12.文档

英文：

~~~
http://www.cplusplus.com/reference/stl/
~~~

中文：

~~~
http://c.biancheng.net/stl/map/
~~~

