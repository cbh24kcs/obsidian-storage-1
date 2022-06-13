
例子：
```c++
#include <iostream>
using namespace std;

void fun1(int x) 
{
    x = 4;
    cout << "fun1: 里面x的地址:" << &x << endl;
}

void fun2(int &x) 
{
    x = 4;
    cout << "fun2: 里面x的地址:" << &x << endl;
}

void fun3(int* px) 
{
    *px = 4;
    cout << "fun3: 里面px的地址:" << &px << endl;
    cout << "fun3: 里面px存储的地址:" << px << endl;
}


int main()
{
    int x = 3;
    // 按值传递
    // 相当于复制了内存中的值
    // 实参与形参的地址不同
    // 实参与形参使用的内存也不同
    cout << "fun1: 外面的x的地址:" << &x << endl;
    fun1(x);
    cout << "x = " << x << endl;

    cout << "====================================" << endl;

    // 按引用传递
    // 实参与形参的地址其实是一样的
    // 实参与形参引用的内存也是一样的
    x = 3;
    cout << "fun2: 外面的x的地址:" << &x << endl;
    fun2(x);
    cout << "x = " << x << endl;

    cout << "====================================" << endl;

    // 按共享传递（传递地址）
    // C++中其实没有按共享传递，但是可以用指针模拟
    // 实参与形参的地址不同
    // 形参保存了实参的地址
    // 所以实参与形参可以访问同一个内存区域
    // 修改共享本身的值，不会影响实参
    x = 3;
    cout << "fun3: 外面的x的地址:" << &x << endl;
    fun3(&x);
    cout << "x = " << x << endl;


    return 0;
}

```