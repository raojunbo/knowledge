## 一：Flutter架构图

![](https://static001.geekbang.org/resource/image/ac/2f/ac7d1cec200f7ea7cb6cbab04eda252f.png)

## 一：Widget

StateFullWidget，StateLessWidget

Widget树由数据驱动。可以发生变化的可以是StateFullWidget，它有个状态对象，我们可以更改状态的数据，状态的数据从而重新根据数据构建页面。

这种状态也可以是其他状态管理方法。

## 二：组件分类

| 常用        | 布局           | 装饰        | 动画            | Material            |
| ----------- | -------------- | ----------- | --------------- | ------------------- |
| Container   | Container      | Opacity     | AnimatedOpacity | MaterialApp         |
| Image       | Center         | DecorateBox | Hero            | Scaffold            |
| Text        | Padding        | RotateBox   |                 | AppBar              |
| Icon        | Align          | Clip        |                 | BottomNavigationBar |
| RaiseButton | Row            | 自定义画板  |                 | TabBar              |
| FlatButton  | Column         |             |                 | Drawer              |
| Listview    | Stack          |             |                 | PopupMenuButton     |
| GrideView   | OverFlowBox    |             |                 | SnackBar            |
| TextField   | SizedBox       |             |                 | Card                |
|             | ConstrainedBox |             |                 |                     |
|             | Wrap           |             |                 |                     |

## 三：渲染过程

![](https://static001.geekbang.org/resource/image/b4/c9/b4ae98fe5b4c9a7a784c916fd140bbc9.png)



![](https://static001.geekbang.org/resource/image/35/6d/3536bd7bc00b42b220ce18ba86c2a26d.png)

### Widget

widget是对视图的一种结构化描述，里面存储的是视图渲染的描述信息，包括布局、渲染属性、事件响应信息等

### Element

Element 树这一层将 Widget 树的变化（类似 React 虚拟 DOM diff）做了抽象，可以只将真正需要修改的部分同步到真实的 RenderObject 树中，最大程度降低对真实渲染视图的修改，提高渲染效率，而不是销毁整个渲染视图树重建。就是 Element 树存在的意义。

### RenderObject

渲染对象树在 Flutter 的展示过程分为四个阶段，即布局、绘制、合成和渲染。其中，布局和绘制在 RenderObject 中完成，Flutter 采用深度优先机制遍历渲染对象树，确定树中各个对象的位置和尺寸，并把它们绘制到不同的图层上。绘制完毕后，合成和渲染的工作则交给 Skia 搞定。

### 源码查看

### 在iOS中的联系





## 三：详解布局

需要说明布局体系的内核是什么。

## 四：详解动画

需要说明动画的本质是什么

