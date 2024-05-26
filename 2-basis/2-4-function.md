# 函数
在Dart中，函数可以通过以下语法定义：

```dart
返回类型 函数名(参数列表) {
  // 函数体
}
int add(int a, int b) {
  return a + b;
}
```

## 可选参数
函数中可以包含零个或多个可选参数，可选参数分为命名参数和位置参数两种类型：
* 命名参数：使用大括号`{}`包裹，并在调用时指定参数的名称；
* 位置参数：使用方括号`[]`包裹，并且在调用时按照参数的位置传递值；

也可以为可选参数设置默认值，这样在调用时可以不提供这些参数的值，而是使用默认值。

> 注意：如果存在必需参数，则可选参数要声明在必需参数后面

```dart
// 位置参数
int sum(int a, int b, [int c]) {
  if (c != null) {
    return a + b + c;
  }
  return a + b;
}
print(sum(3, 5, 7));
// 命名参数
int multiply({int a = 1, int b = 2}) {
  return a * b;
}
print(multiply(a: 3, b: 5));
```

## 函数作为对象

与JavaScript中类似，在Dart中函数也是一种特殊类型的对象（并且有具体类型`Function`）。因此函数可以分配给变量或者作为参数传递给其他函数，也可以创建匿名函数。

```dart
// 匿名函数
var multiply = (int a, int b) {
  return a * b;
};
multiply(3, 5);
// 函数作为参数
void executeFunction(int Function(int, int) func) {
  print(func(3, 5));
}
executeFunction(multiply);
// 函数作为返回值
Function getOperation(String operation) {
  if (operation == 'add') {
    return add;
  } else if (operation == 'multiply') {
    return multiply;
  }
  return null;
}
var operation = getOperation('multiply');
print(operation(3, 5));
```

## 作用域与闭包

Dart中作用域和闭包的概念和JavaScript中是相似的，它们影响着变量的可见性范围和生命周期。Dart中有以下几种作用域：
* **全局作用域（Global Scope）**：全局作用域中声明的变量在整个程序中都可以访问，在Dart中全局作用域是指在所有函数之外声明的变量。
* **局部作用域（Local Scope）**：局部作用域中声明的变量只能在声明它们的函数内部访问，这意味着这些变量对于函数外部是不可见的。
* **块级作用域（Block Scope）**：`if`语句、`for`循环、`while`循环等代码块可以形成一个块级作用域，在块级作用域中声明的变量只能在该代码块内部访问。

```dart
// 全局作用域
int globalVariable = 10;
void main() {
  // 局部作用域
  int localVariable = 20;
  if (true) {
    // 块级作用域
    int blockVariable = 30;
    print(globalVariable); // 可访问全局变量
    print(localVariable);  // 可访问局部变量
    print(blockVariable);  // 可访问块级变量
  }
  print(globalVariable); // 输出：10
  print(localVariable);  // 输出：20
  print(blockVariable);  // 编译错误：blockVariable 在此处不可见
}
```

函数闭包是指函数可以访问其所在作用域的变量，即使函数在其定义的作用域之外执行也可以访问这些变量。

```dart
Function makeCounter() {
  int count = 0;
  return () {
    count++;
    print(count);
  };
}
void main() {
  var counter = makeCounter();
  counter(); // 输出：1
  counter(); // 输出：2
  counter(); // 输出：3
}
```

