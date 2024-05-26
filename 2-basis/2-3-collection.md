# 集合

## List（列表）
Dart中的`List`与JavaScript中的`Array`类似，是一种有序的集合，用于存储多个元素。

```dart
List<int> numbers = const [1, 2, 3, 4, 5];
numbers[1] = 1; // 编译时常量列表，修改时会报错
List<String> names = ['Alice', 'Bob', 'Charlie'];
names[1] = 'Tom';
```

Dart的`List`类提供了丰富的方法来操作`List`，包括添加、移除、查找、排序等：

| 方法 | 用途 |
| -- | -- |
| `length` | 获取List中元素的个数 |
| `isEmpty` | 判断列表是否为空 |
| `isNotEmpty` | 判断列表是否不为空 |
| `add(E element)` | 向列表末尾添加一个元素 |
| `addAll(Iterable<E> elements)` | 向列表末尾添加一个可迭代的集合中的所有元素 |
| `insert(int index, E element)` | 在指定索引处插入一个元素 |
| `remove(E element)` | 移除列表中第一个匹配指定值的元素 |
| `removeAt(int index)` | 移除指定索引处的元素 |
| `removeLast()` | 移除列表中的最后一个元素 |
| `removeRange(int start, int end)` | 移除列表中指定范围的元素 |
| `removeWhere(bool f(E element))` | 根据指定条件移除列表中的元素 |
| `retainWhere(bool f(E element))` | 根据指定条件保留列表中的元素 |
| `clear()` | 移除列表中的所有元素 |
| `contains(E element)` | 判断列表中是否包含指定元素 |
| `forEach(void f(E element))` | 对列表中的每个元素执行指定操作 |
| `map(T f(E element))` | 对列表中的每个元素执行指定的转换操作，并返回转换后的结果 |
| `sort(int f(E element1, E element2))` | 对列表中的元素进行排序 |
| `sublist(int start, [int end])` | 获取列表中指定范围的子列表 |
| `toList()` | 将可迭代对象转换为列表 |
| `join(String separator)` | 将列表中的元素连接成一个字符串 |
| `indexOf(E element, [int start])` | 返回列表中第一次出现指定元素的索引 |
| `lastIndexOf(E element, [int start])` | 返回列表中最后一次出现指定元素的索引 |

```dart
List<int> numbers = [1, 2, 3];
List<int> moreNumbers = [4, 5, 6];
numbers.addAll(moreNumbers); // [1, 2, 3, 4, 5, 6]
List<int> numbers = [1, 2, 3, 4, 5];
numbers.removeWhere((number) => number.isEven); // [1, 3, 5]
numbers.retainWhere((number) => number.isOdd);  // [1, 3, 5]
```

## Set（集合）

Dart中`Set`是一种无序的集合，它不允许重复的元素。

```dart
Set<int> numbers = {1, 2, 3, 4, 5};
Set<String> names = {'Alice', 'Bob', 'Charlie'};
```

Dart的`Set`类提供了一系列常见的方法来操作`Set`，包括添加、移除、查找等：

| 方法 | 用途 |
| -- | -- |
| `isEmpty` | 判断集合是否为空 |
| `isNotEmpty` | 判断集合是否不为空 |
| `add(E element)` | 向集合中添加一个元素 |
| `addAll(Iterable<E> elements)` | 向集合中添加一个可迭代的集合中的所有元素 |
| `remove(E element)` | 移除集合中指定的元素 |
| `contains(E element)` | 判断集合中是否包含指定的元素 |
| `clear()` | 移除集合中的所有元素 |
| `intersection(Set<E> other)` | 返回包含当前集合和另一个集合中共同元素的新集合 |
| `union(Set<E> other)` | 返回包含当前集合和另一个集合中所有元素的新集合 |
| `difference(Set<E> other)` | 返回包含当前集合中但不包含另一个集合中元素的新集合 |
| `toList()` | 将集合转换为列表 |
| `toSet()` | 将可迭代对象转换为集合 |

```dart
Set<int> numbers1 = {1, 2, 3};
Set<int> numbers2 = {2, 3, 4};
Set<int> intersectionSet = numbers1.intersection(numbers2); // {2, 3}
Set<int> numbers1 = {1, 2, 3};
Set<int> numbers2 = {2, 3, 4};
Set<int> unionSet = numbers1.union(numbers2); // {1, 2, 3, 4}
Set<int> numbers1 = {1, 2, 3};
Set<int> numbers2 = {2, 3, 4};
Set<int> differenceSet = numbers1.difference(numbers2); // {1}
```

## Map（映射）
Dart中`Map`是一种键值对的集合，其中每个键都是唯一的，并且与一个值相关联。

```dart
Map<String, int> ages = {
  'Alice': 30,
  'Bob': 25,
  'Charlie': 35,
};
```

Dart的`Map`类提供了丰富的方法来操作`Map`，包括添加、移除、查找、遍历等：

| 方法 | 用途 |
| -- | -- |
| `length` | 获取Map中键值对的数量 |
| `isEmpty` | 判断Map是否为空 |
| `isNotEmpty` | 判断Map是否不为空 |
| `keys` | 获取Map中所有的键 |
| `values` | 获取Map中所有的值 |
| `containsKey(K key)` | 判断Map中是否包含指定的键 |
| `containsValue(V value)` | 判断Map中是否包含指定的值 |
| `remove(K key)` | 移除Map中指定键的键值对 |
| `putIfAbsent(K key, V ifAbsent())` | 如果Map中不存在指定键，则插入指定的键值对 |
| `update(K key, V f(V value))` | 更新Map中指定键的值 |
| `updateAll(V f(K key, V value))` | 对Map中的每个键值对执行指定的更新操作 |
| `clear()` | 移除Map中的所有键值对 |

```dart
Map<String, int> ages = {'Alice': 30, 'Bob': 25};
ages.putIfAbsent('Charlie', () => 35);      // {'Alice': 30, 'Bob': 25, 'Charlie': 35}
Map<String, int> ages = {'Alice': 30, 'Bob': 25};
ages.update('Alice', (value) => value + 1); // {'Alice': 31, 'Bob': 25}
Map<String, int> ages = {'Alice': 30, 'Bob': 25};
ages.updateAll((key, value) => value + 1);  // {'Alice': 31, 'Bob': 26}
```
