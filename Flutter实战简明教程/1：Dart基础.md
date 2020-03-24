## Dart,iOS数据类型对比

| int    | int                              |
| ------ | -------------------------------- |
| double | Double                           |
| bool   | BOOL                             |
| String | NSString                         |
| List   | NSArray,NSMutableArray           |
| Map    | NSDictionary,NSMutableDictionary |

在 Dart 中，所有类型都是对象类型，都继承自顶层类型 Object，因此一切变量都是对象，**数字**、**布尔值**、**函数**和 **null **也概莫能外。

## Num

Int,double

## String

```dart
var s1 = 'this is a uppercased string: ${s.toUpperCase()}';
var s2 = 'Hello' + ' ' + 'World!' ;
var s3 = """This is amulti-line string.""";
```

## List

```dart
var arr1 = ["Tom", "Andy", "Jack"];
var arr1 = <String>['Tom', 'Andy', 'Jack'];
var arr2 = List.of([1,2,3]);
arr2.add(499);
arr2.forEach((v) => print('${v}'));
```

## Map

```dart
var map1 = {"name": "Tom", 'sex': 'male'}; 
var map1 = <String, String>{"name": "Tom", 'sex': 'male'}; 
var map2 = new Map();
map2['name'] = 'Tom';
map2['sex'] = 'male';
map2.forEach((k,v) => print('${k}: ${v}'));
```

## 常量定义

- const，表示变量在编译期间即能确定的值；

- final 则不太一样，用它定义的变量可以在运行时确定值，而一旦确定后就不可再变。

## 函数

在 Dart 中，所有类型都是对象类型，函数也是对象，它的类型叫作 Function。它当然就能够被当作参数传递。

- 可选命名参数{};（有点类似于objectC里的方法签名）

```dart
void enable1Flags({bool bold, bool hidden}) => print("$bold , $hidden");
```

- 可选参数[]

```dart
void enable3Flags(bool bold, [bool hidden]) => print("$bold ,$hidden");
```

示例

区别：对调用者调用方式不同，一个需要显式声明参数名，参数位置无所谓；一个不用，但需要按照顺序摆放参数。

## 类

- 每个对象都是一个类的实例，都继承自顶层类型 Object。
- Dart 中并没有 public、protected、private 这些关键字，我们只要在声明变量与方法时，在前面加上“\_”即可作为 private 方法使用。如果不加“\_”，则默认为 public。不过，“_”的限制范围并不是类访问级别的，而是库访问级别。
- 命名构造函数

```
class User {
	String name;
	int age;
	User(this.name,this.age);//普通构造方法
	User.fromJson(Map json){//命名构造方法(有点类似于一个静态方法去构造一个对象)
		name = json['name'];
		age = json['age'];
	}
}
```

- 继承（extends）
- 接口（implements）

Flutter是没有interface的，但是Flutter中的每个类都是一个隐式的接口，这个接口包含类里的所有成员变量，以及定义的方法

- 混入（Mixin）；混入能实现类似于多继承。可以使用混入的多个类的方法。

```dart
class Point { 
  num x = 0, y = 0; 
  void printInfo() => print('($x,$y)');
}
class Coordinate with Point {
  
}
var yyy = Coordinate();
print (yyy is Point); //true
print(yyy is Coordinate); //true
```

> 思考：继承，接口，混入在实际的使用中怎么做出选择？
>
> 继承是继承了实现；接口只是复用方法，不复用实现；混入是直接使用。

- 泛型

```
var map1 = <String, String>{"name": "Tom", 'sex': 'male'}; //<T>主要是保障类型安全
```



## 特殊运算符

- ?. 假设 Point 类有 printInfo() 方法，p 是 Point 的一个可能为 null 的实例。p 调用成员方法的安全代码，可以简化为 p?.printInfo() ，表示 p 为 null 的时候跳过，避免抛出异常

- ??= 如果 a 为 null，则给 a 赋值 value，否则跳过。即兜底代码。
- ?? 即(a != null)? a : b可以简写为a ?? b



**Dart可以在没有锁的情况下进行进行对象分配和垃圾回收。Dart避免了抢占式调度和共享内存。？？**还没有理解其中的精髓。

## 异步支持

