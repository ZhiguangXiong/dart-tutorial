# 基本类型

## Number
Dart中有两种数字类型：整数型`int`和双精度浮点型`double`。

```dart
int x = 1;
int hex = 0xDEADBEEF;
double y = 1.1;
double exponents = 1.42e5;
```

使用`double`定义的浮点型变量可以接收一个整数值（但不能接收一个整数型变量），但是使用`int`定义的整数型变量不能接受一个浮点数值。使用`num`定义的变量可以同时接收整数值和浮点数值。

```dart
double a = 1;
int b = 1.1; // ERROR: A value of type 'double' can't be assigned to a variable of type 'int'.
b = a;       // ERROR: A value of type 'double' can't be assigned to a variable of type 'int'.
a = b;       // ERROR: A value of type 'int' can't be assigned to a variable of type 'double'.
num c = 1;
c = 1.5;
```

常用属性：
* `isNaN`：用于检查数值是否为`NaN`（非数字）；
* `isInfinite`：用于检查数值是否为无穷大；
* `isNegative`：用于检查数值是否为负数；
* `isEven`（仅整数值可用）：用于检查整数是否为偶数；
* `isOdd`（仅整数值可用）：用于检查整数是否为奇数；

常用方法：
* `toInt()`：用于将浮点数值转化为整数值；
* `toDouble()`：用于将整数值转化为浮点数值；
* `toStringAsFixed(int digits)`：用于将双精度浮点数转换为固定小数位数的字符串；

## String
Dart中可以使用单引号或双引号来创建字符串，使用三重引号（`'''`或`"""`）来创建多行字符串，在字符串前加上`r`前缀可以创建原始字符串（原始字符串中的转义字符不生效）。使用`$`或`${}`语法可以在字符串中嵌入变量或表达式。

```dart
// 创建字符串
String str1 = 'Hello, Dart!';
String str2 = "Welcome to Dart!";
String multiline = '''
This is a multiline
string in Dart.
''';
String rawString = r'This is a raw string.\n'; // Output: "This is a raw string.\n"
// 字符串插值
String name = 'Alice';
int age = 30;
print('My name is ${name.toUpperCase()} and I am $age years old.');
```

Dart中提供了一系列字符串操作方法，以便于对字符串进行处理和操作：
| 方法 | 用途 |
| -- | -- |
| `length` | 获取字符串的长度 |
| `isEmpty` | 判断字符串是否为空 |
| `isNotEmpty` | 判断字符串是否不为空 |
| `toUpperCase()` | 将字符串转换为大写 |
| `toLowerCase()` | 将字符串转换为小写 |
| `trim()` | 移除字符串两端的空白字符 |
| `trimLeft()` | 移除字符串左端的空白字符 |
| `trimRight()` | 移除字符串右端的空白字符 |
| `substring(int start, [int end])` | 根据起始位置（包含）和结束位置（不包含）来截取子串 |
| `split(Pattern pattern)` | 根据指定的模式拆分字符串并返回子串数组 |
| `contains(Pattern pattern)` | 判断字符串是否包含指定的子串或模式 |
| `startsWith(Pattern pattern)` | 判断字符串是否以指定的子串或模式开始 |
| `endsWith(Pattern pattern)` | 判断字符串是否以指定的子串或模式结束 |
| `indexOf(Pattern pattern, [int start])` | 返回指定子串或模式在字符串中第一次出现的位置 |
| `lastIndexOf(Pattern pattern, [int start])` | 返回指定子串或模式在字符串中最后一次出现的位置 |
| `replaceFirst(Pattern pattern, String replace)` | 替换字符串中第一次出现的指定子串或模式 |
| `replaceAll(Pattern pattern, String replace)` | 替换字符串中所有出现的指定子串或模式 |

```dart
String str = 'Hello, Dart, Dart';
str.substring(7);                     // "Dart, Dart"
str.substring(7, 11);                 // "Dart"
List<String> parts = str.split(', '); // ["Hello", "Dart", "Dart"]
str.replaceFirst('Dart', 'World');    // "Hello, World, Dart"
str.replaceAll('Dart', 'World');      // "Hello, World, World"
```

## Boolean
布尔数据类型只有两个取值：`true`和`false`，常用于构建布尔表达式，并且支持常见的逻辑运算。

```dart
bool a = true;
bool b = false;
print(a && b); // false
print(a || b); // true
print(!a);     // false
```
