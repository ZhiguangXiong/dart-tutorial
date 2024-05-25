# 变量

## 使用`var`定义变量
类似于JavaScript中的`var`，使用它可以定义任意类型的变量。

> ⚠️注意：在Dart中，使用`var`定义的变量一旦被赋值，那么其数据类型便会确定，不能再修改其类型。

```dart
var t = 'hello world';
t = 1000; // ERROR: A value of type 'int' can't be assigned to a variable of type 'String'
```

## 使用`dynamic`和`Object`定义变量
在Dart中，`Object`是所有对象的根基类（即所有类型都是`Object`的子类，包括`Function`和`Null`），所以任何类型的数据都可以赋值给`Object`声明的对象。

```dart
dynamic t;
t = 'hello world';
t = 1000; // NO ERROR
```

`dynamic`与`Object`不同的是`dynamic`声明的对象编译器会提供所有可能的组合，而`Object`声明的对象只能使用`Object`的属性与方法，否则编译器会报错。

```dart
dynamic a;
Object b = '';
main() {
  a = '';
  printLengths();
}
printLengths() {
  print(a.length); // NO ERROR
  print(b.length); // ERROR: The getter 'length' isn't defined for the type 'Object'
}
```

## 空安全

JavaScript中最常见的错误就是“空指针错误”，在尝试访问`null`或`undefined`值的属性或方法时发生。

```js
var obj = null;
console.log(obj.property); // ERROR: Cannot read property 'property' of null
```

Dart在2.12版本中引入了空安全的概念，空安全是指在处理变量和对象时，确保它们的值不为`null`，从而减少代码中的空指针异常和其他相关错误。
如果一个变量可以为空，需要在类型声明的末尾添加`?`，不能在可空类型的表达式上访问属性或调用方法。Dart不会为非可空类型设置初始值，因此在使用之前需要设置初始值。

```dart
String? name  // Nullable type. Can be `null` or string
String name   // Non-nullable type. Cannot be `null` but can be string
print(name.length);  // ERROR: The property 'length' can't be unconditionally accessed because the receiver can be 'null'
print(name2.length); // ERROR: The non-nullable local variable 'name2' must be assigned before it can be used
```

Dart也提供了一些操作符来处理可空类型，避免因空值导致的异常：
* 安全调用操作符`?.`：用于在对象可能为空时安全地调用其方法或访问其属性。
* 非空断言操作符`!.`：用于在确定一个可空变量不为空时，将其转换为非空类型（如果断言错误，会抛出运行时异常）。
* 空合并操作符`??`：用于在变量为空时提供默认值。

```dart
String? name = 'Dart';
print(name!.length);
print(name ?? 'Default Name');
```

## 终值和常量
与变量不同，常量的值在程序执行期间不会改变，可以使用`final`或`const`关键字来声明常量。

> ⚠️注意：`final`声明的常量在运行时初始化，而`const`声明的是编译时常量。

```dart
final name = 'Bob';
final String nickname = 'Bobby';
const bar = 1000000;
const double atm = 1.01325 * bar;
```


