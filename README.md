STL
------------
###1.输入输出

####1.1.C语言的输入输出

```cpp
	int a;
	scanf("%d\n", a);
	printf("%d", a);
```

####1.2.C++语言的输入输出

```cpp
	int a,b,c;
	cin>>a>>b>>c;
	cout<<a<<b<<c<<endl;
```

###2.STL与algorithm头文件

####2.1.sort()函数

#####2.1.1.迭代器
    迭代器————理解为指针，但是迭代器分为4种：
    1) 正向迭代器，定义方法如下：
    容器类名::iterator  迭代器名;
    2) 常量正向迭代器，定义方法如下：
    容器类名::const_iterator  迭代器名;
    3) 反向迭代器，定义方法如下：
    容器类名::reverse_iterator  迭代器名;
    4) 常量反向迭代器，定义方法如下：
    容器类名::const_reverse_iterator  迭代器名;

#####2.1.2.sort排序实例

sort()函数语法描述：sort(begin,end,cmp),cmp参数可以没有，如果没有默认非降序排序。
- 以int为例的基本数据类型的sort使用
	1. 升序：sort(begin,end,less<data-type>());
	2. 降序：sort(begin,end,greater<data-type>());

```cpp
#include<iostream>
#include<algorithm>

using namespace std;

int main(){
    int a[] = {1,5,4,8,10,6,3};
    sort(a,a+7);
    //sort(a,a+7,less<int>());
    //sort(a,a+7,graeter<int>());
    for(int i = 0; i < 7; i++){
        cout<<a[i]<<" ";
    }
    return 0;
}
```
运行结果：1 3 4 5 6 8 10

- 引用数据类型string的使用

1.使用迭代器可以完成顺序排序：

```cpp
#include<iostream>
#include<algorithm>
#include<string>

using namespace std;

int main(){

    string str = "hello world";
    sort(str.begin(),str.end(),less<int>());
    string :: iterator it;
    for(it=str.begin();it!=str.end();it++){
        cout<<*it;
    }
    cout<<endl;
    cout<<str<<endl;
    return 0;
}
```
运行结果：空格dehllloorw

2.使用反向迭代器可以完成逆向排序

```cpp
#include<iostream>
#include<algorithm>
#include<string>

using namespace std;

int main()
{
    string str("hello world");
    sort(str.rbegin(),str.rend());
    //sort(str.begin(),str.end(),greater<int>());
    cout<<str;
    return 0;
 }
```
运行结果：wroolllhde空格

3.以结构体为例的二级排序

```
#include<iostream>
#include<algorithm>
#include<string>

using namespace std;

struct link{
    int a,b;
};
bool cmp(link x,link y){
    if(x.a == y.a){
        return x.b > y.b;
    }
    return x.a > y.a;
}
int main(){
    link x[4];
    for (int i=0;i<4;i++){
        cin>>x[i].a>>x[i].b;
    }
    sort(x,x+4,cmp);
    for (int i=0;i<4;i++){
        cout<<x[i].a<<" "<<x[i].b<<endl;
    }
    cout<<endl;
    return 0;
}
```

###3.string()

概念：相当于char * 封装，理解为字符串

####3.1.简单使用

```cpp
int main(){
	//C中定义字符串以及打印
	char *ch="sdasfsfjg";
	for(int i = 0;ch[i] !='\0';i++){
	cout<<*(ch + i);
	}
	cout<<endl;
	//C++
	string s = "sadasdsfg";
	cout<<s<<endl;
	return 0;
}
```

####3.2.获得一行字符串

我想获取一行字符串
```cpp
hello world
```
C中：
```c
#include<stdio.h>
int main(){
    char ch[100];
    /*
    scanf()不能获取含有空格的字符串，遇到空格就会停止
    */
    gets(ch);//获取一行有空格的字符串
    for(int i = 0; ch[i] != '\0'; i++){
        printf("%s",ch[i]);
    }
    return 0;
}
```
