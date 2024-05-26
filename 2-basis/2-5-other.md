# 其他

## 枚举
枚举（Enum）是一种特殊的数据类型，用于定义一组命名的常量值，在代码中进行引用和使用。通过使用`enum`关键字可以定义枚举。枚举中包含一组有意义的常量值，每个常量值都有一个相关联的名称。
枚举类型可以使用`values`属性，获取枚举中所有常量值的列表。

```dart
enum Weekday {
  Monday,
  Tuesday,
  Wednesday,
  Thursday,
  Friday,
  Saturday,
  Sunday
}
void main() {
  Weekday today = Weekday.Wednesday;
  print('Today is ${today.toString().split('.').last}');
}

void main() {
  for (var day in Weekday.values) {
    print(day);
  }
}
```

## 泛型

泛型允许我们在定义类、函数和接口时使用参数化类型，从而实现对不同类型的数据进行操作。我们可以编写更加灵活和通用的代码，同时提高代码的类型安全性和可重用性。
通过使用尖括号`<T>`可以定义泛型，其中`T`是类型参数，表示任意类型。
```dart
class Box<T> {
  T value;
  Box(this.value);
}
class Pair<T, U> {
  T first;
  U second;
  Pair(this.first, this.second);
}
```

泛型有以下特性：
* **类型安全**：泛型可以提高代码的类型安全性，因为它们允许我们在编译时就能够确定类型的一致性；
* **代码重用**：泛型允许我们编写更加通用和灵活的代码，可以在不同类型之间进行操作，而不必重复编写相似的代码；
* **提高性能**：泛型在编译时会进行类型检查，因此可以更好地优化代码，提高性能；
