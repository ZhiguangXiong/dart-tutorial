# 继承与多态

## 继承
通过使用`extends`关键字可以实现类的继承，子类会继承父类可见的属性和方法，并在此基础上进行扩展。在子类中，通过`super`关键字可以调用父类的方法和构造方法，因此我们可以在子类中复写父类的方法、`getter`和`setter`。

```dart
class Animal {
  void makeSound() {
    print('Animal makes sound');
  }
}
class Dog extends Animal {
  // 复写方法
  void makeSound() {
    super.makeSound();
    print('Dog barks');
  }
  // 扩展方法
  void bark() {
    print('Dog barks');
  }
}
```

当子类继承父类时，构造方法的继承需要注意：
* 默认情况下，子类会继承父类的默认构造方法。即如果父类有一个无参数的默认构造方法，子类会自动继承它；
* 如果父类没有默认构造方法，或者想要调用父类的带参数的构造方法，就需要手动调用父类的构造方法；

```dart
// 默认构造方法
class Animal {
  Animal() {
    print('Animal constructor');
  }
}
class Dog extends Animal {
  Dog() : super() {
    print('Dog constructor');
  }
}
// 手动调用父类构造方法
class Animal {
  String name;
  Animal(this.name) {
    print('Animal constructor');
  }
}
class Dog extends Animal {
  Dog(String name) : super(name) {
    print('Dog constructor');
  }
}
```
当创建一个子类的对象时，会按照以下顺序执行构造方法：
* **父类构造方法**：调用父类的构造方法，以初始化父类的状态；
* **子类构造方法初始化列表**：执行子类构造方法的初始化列表，在初始化列表中，可以对子类的属性进行初始化，也可以调用父类的构造方法；
* **子类构造方法函数体**：执行子类构造方法的函数体，执行进一步的初始化逻辑；
```dart
var dog = new Dog();
// 输出：Animal constructor
// 输出：Dog constructor
```

## 抽象类
抽象类是一种特殊类型的类，它不能被实例化，只能被用作其他类的基类。抽象类通常用于定义一组方法的接口，而不提供方法的具体实现。
Dart中通过`abstract`关键字可以定义抽象类，抽象类中可以包含抽象方法，也可以包含普通方法。
> 抽象方法：在抽象类中声明但没有提供实现的方法，子类必须重写抽象方法来提供具体的实现
```dart
abstract class Shape {
  // 抽象方法
  double area();
  // 普通方法
  void draw() {
    print('Drawing shape');
  }
}
class Circle extends Shape {
  double radius;
  Circle(this.radius);
  // 实现抽象方法
  @override
  double area() {
    return 3.14 * radius * radius;
  }
}
```
抽象类有以下特性：
* **不能被实例化**：抽象类不能被直接实例化，只能用作其他类的基类；
* **包含抽象方法**：抽象类中可以包含抽象方法，这些方法没有具体的实现；
* **用作接口**：抽象类可以用作接口，定义一组方法的接口，而不提供具体的实现；
* **提供默认实现**：抽象类中可以包含普通方法，这些方法有具体的实现，子类可以选择性地重写这些方法；

## 接口
Dart中的接口是一种抽象的概念，用于定义类的行为规范，而不关心具体的实现细节。接口定义了一组方法的签名，而类则实现了这些方法。
* 通过使用`abstract`关键字可以定义接口。接口中可以包含方法、属性或者`getter`、`setter`等成员，但不提供具体的实现；
* 通过使用`implements`关键字，可以让类实现一个或多个接口，类需要提供接口中定义的所有方法的具体实现；
```dart
abstract class Shape {
  double area();
  void draw();
}
class Circle implements Shape {
  double radius;
  Circle(this.radius);
  @override
  double area() {
    return 3.14 * radius * radius;
  }
  @override
  void draw() {
    print('Drawing Circle');
  }
}
```
接口有以下特性：
* **定义行为规范**：接口定义了一组方法的签名，用于规定类的行为规范；
* **实现多态性**：通过实现相同的接口，不同的类可以具有相似的行为；
* **与抽象类的区别**：接口只定义方法的签名，而抽象类可以提供方法的部分实现；

## Mixins
Mixins是一种非常强大的特性，允许在类中引入方法和属性，以实现代码的复用，同时保持代码的模块化和可维护性。
Mixins是Dart中一种特殊的类，它不能被实例化，也不能被继承，主要通过`with`关键字来与类进行混入。
```dart
mixin Jumping {
  void jump() {
    print('Jumping...');
  }
}
class Animal with Jumping {
  // Animal 类混入 Jumping Mixin
}
void main() {
  var animal = Animal();
  animal.jump();
}
```
Mixins有以下特性：
* **代码复用**：Mixins允许我们将代码逻辑封装到可重用的模块中，并在多个类中共享；
* **无需继承**：与继承不同，Mixins不会形成类的层次结构，因此可以避免继承链的复杂性和耦合度；
* **多Mixins组合**：一个类可以混入多个Mixins，从而实现更加灵活的代码复用；
```dart
class Hero with Jumping, Flying {
  // Hero 类混入了 Jumping 和 Flying Mixins
}
```
与继承的区别：
* **单继承 vs 多Mixins组合**：Dart中的类只能单继承，而Mixins允许类混入多个Mixins，从而避免了单继承的限制；
* **代码复用方式**：继承是一种纵向的代码复用方式，而Mixins是一种横向的代码复用方式，它们解决了不同的问题；


