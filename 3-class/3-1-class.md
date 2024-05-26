# 类与对象

Dart是一种支持面向对象编程（OOP）的现代化编程语言，并且具有灵活的语法和强大的功能。

## 属性与方法
属性是类的成员变量，用于描述对象的状态。其中**实例属性**是每个类实例独有的，并且可以在类的构造方法中初始化。使用`static`关键字声明**静态属性**属于类本身，而不是类的实例。

```dart
class Person {
  // 实例属性
  String name;
  int age;
  void sayHello() {
    print('Hello, my name is $name and I am $age years old.');
  }
}
class MathUtils {
  // 静态属性
  static const double pi = 3.14;
}
```

Dart中的`getter`和`setter`方法允许我们控制属性的访问和修改。计算属性是一种特殊类型的属性，通过`getter`方法来定义，计算属性的值通常依赖于类中的其他属性或外部条件，每次访问计算属性时都会重新计算其值。

```dart
class Rectangle {
  double _width;
  double _height;
  // Getter方法
  double get width => _width;
  // Setter方法
  set width(double value) {
    if (value > 0) {
      _width = value;
    }
  }
  // 计算属性
  double get area => _width * _height;
}
```

## 构造方法
### 默认构造方法
在Dart中，构造方法的名称与类名称相同。构造方法可以用于初始化对象的状态，并执行一些预设的操作。

> 如果没有自定义构造方法，在生成实例时会使用默认构造方法

```dart
class Person {
  String name;
  int age;
  Person(this.name, this.age);
}
```

### 命名构造方法

命名构造方法允许为类定义多个不同的构造方法，每个方法有自己的名称。

```dart
class Rectangle {
  double width;
  double height;
  Rectangle.square(double side)
      : width = side,
        height = side;
}
```
### 常量构造方法

常量构造方法是一种特殊类型的构造方法，用于创建编译时常量对象。使用常量构造方法可以提高性能，并确保对象在程序运行期间的唯一性。

```dart
class Point {
  final double x;
  final double y;
  const Point(this.x, this.y);
}
```

### 工厂构造方法

工厂构造方法类似于设计模式中的工厂模式，是一种特殊类型的构造方法，用于返回一个类的实例，但不一定要创建一个新的实例。它允许我们使用自定义的逻辑来决定要返回的对象。

```dart
class Logger {
  final String name;
  static final Map<String, Logger> _cache = {};
  factory Logger(String name) {
    return _cache.putIfAbsent(name, () => Logger._internal(name));
  }
  Logger._internal(this.name);
}
```

## 其他
### 初始化列表
初始化列表是在构造方法体之前用冒号`:`引出的，它允许在对象创建时执行一些额外的初始化操作。初始化列表会在构造方法体执行之前执行。

```dart
class Person {
  String name;
  int age;
  Person(String name, int age) 
    : name = name.toUpperCase(),
      age = age + 1;
}
```

### 对象操作符
Dart中提供了一些特殊的操作符，用于简化对象的操作和处理：
* `?.`：条件成员访问，当左侧对象为`null`时，右侧不会执行；
* `??`：空值合并，当左侧对象为`null`时，使用右侧的默认值；
* `..`：级联操作，允许对同一个对象进行一系列操作；
* `is`和`!is`：类型检查运算符，用于检查一个对象是否是指定类型的实例或者不是指定类型的实例；

```dart
String? name;
print(name?.toUpperCase()); // 条件成员访问
print(name ?? 'Unknown');   // 空值合并

Person person = Person('Alice', 30);
person
  ..name = 'Bob'        // 级联操作
  ..age = 25;
print(person is Person) // 类型检查运算符
```

### 对象的call方法

在Dart中可以为类定义一个`call`方法，使得对象可以像函数一样被调用。

```dart
class Multiply {
  int call(int a, int b) {
    return a * b;
  }
}
void main() {
  var multiply = Multiply();
  print(multiply(3, 5));
}
```

