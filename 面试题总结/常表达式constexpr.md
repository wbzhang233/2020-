# 常表达式constexpr

constexpr 说明符的作用是声明可以在编译时求得函数或变量的值，它的行为和 C 语言中的 const 关键字是一致的，会将变量结果直接编译到栈空间中。constexpr 还可以用来替换宏定义的常量，规避 [宏定义的风险](https://oi-wiki.org/lang/basic/#define)。

constexpr 修饰的是变量和函数，而 const 修饰的是类型。 

```c++
int frac(int x) { return x ? x * frac(x - 1) : 1; }
int main() {
  constexpr int a = frac(5);  // ERROR: 函数调用在常量表达式中必须具有常量值
  return 0;
}
```

 在 `int frac(int x)` 之前加上 `constexpr` 则编译通过。 

