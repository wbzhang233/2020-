# const char* p与char const *p的辨析

> const char * arr = "123";

//字符串123保存在常量区，const本来是修饰arr指向的值不能通过arr去修改，但是字符串“123”在常量区，本来就不能改变，所以加不加const效果都一样

> char * brr = "123";

//字符串123保存在常量区，这个arr指针指向的是同一个位置，同样不能通过brr去修改"123"的值

> const char crr[] = "123";

//这里123本来是在栈上的，但是编译器可能会做某些优化，将其放到常量区

> char drr[] = "123";

//字符串123保存在栈区，可以通过drr去修改



```c++
//
// Created by wbzhang on 2020/9/15.
//
#include <iostream>
#include <vector>

using namespace std;

int main() {
    
//	int a = 2;
//	printf("%d",a++);
//	printf("%d",++a);

	// for循环判断 中间表达式 是否为真
	for(int i = 0; i + 20; i--)
		cout << "hello "<< i<< endl;

	const char *p = "123";
	// const修饰 char *p；表明以p所指向的字符串数组不可变
	// p为(字符串常量)的指针，p指向该字符串的首字母。并且所指向内容不可变(即*p代表的字符串为常量，*p不可变，但是p可变)
	char const *p1 = "456"; // 常量指针，p1所指向内容不可变;
	// const 修饰 *p1，其类型为char；

	char *const p2 = "369"; // 指针常量，p2本身不可变
	// const修饰 p2，p2为(指针常量)，指向一个字符串
	// 该指针的指向p2不可变；但所指向的内容*p2可变

	// before
	cout<<"-- before --"<<endl;
	cout<<"*p: "<<*p<<endl; // p指向该字符串的首字母，即*p=1
	cout<<"p: "<<p<<endl; // p为该字符串常量的指针，将输出 123

	cout<<"*p1: "<<*p1<<endl; // p1指向该字符串的首字母,即*p1=4
	cout<<"p1: "<<p1<<endl; //  p1为该字符串常量的指针，将输出 456

	cout<<"*p2: "<<*p2<<endl; // p2指向字符串常量的首字母，因此为3
	cout<<"p2: "<<p2<<endl; // p2为指针常量，将输出字符串常量 369

	// after
	cout<<"-- after --"<<endl;
	p = "5"; // p本身可变
//	*p = 'a'; //p所指向的内容不可变
//	*p = "abd";

	p1 = "678"; // p1本身可变
//	*p1 = 'p'; //p1所指向内容不可变
//	*p1 = "bcd"; //p1所指向内容不可变

	char str[100]="Hello World";
//	*p2 = str[1];
//	p2 = "a";  //p2不可变，
//	p2[0] = 'a'; //所指向内容可变,且 p2指向字符串中的第一个字符，将报错
//	(*p2) = 'a'; //所指向内容可变,且 p2指向字符串中的第一个字符,将报错
//	*p2 = "amd";  //所指向内容可变


	cout<<"*p: "<<*p<<endl;
	cout<<"p: "<<p<<endl;

	cout<<"*p1: "<<*p1<<endl;
	cout<<"p1: "<<p1<<endl;

	cout<<"*p2: "<<*p2<<endl;
	cout<<"p2: "<<p2<<endl;

	cout << "done" << endl;

}
```

