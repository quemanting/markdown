### vue 双向数据绑定原理

`Angular`、`Vue`、`React`等等框架，它们最大的优点就是可以实现数据绑定，再也不需要手动进行`DOM`操作了，它们实现的原理也基本上是**脏检查**或**数据劫持**。 

#### Object.defineProperty()

> `vue`是通过`Object.defineProperty(obj,prop,descriptor) `来实现数据劫持的 。

- 语法：`Object.defineProperty(obj,prop,descriptor)`

- 参数

  `obj`:目标对象

  `prop`:需要定义的属性或方法的名称

  `descriptor`:目标属性所拥有的特性

- 可供定义的特性列表

  `value`:属性的值

  `writable`:如果为`false`，属性的值就不能被重写。

  `get`: 一旦目标属性被访问就会调回此方法，并将此方法的运算结果返回用户。

  `set`:一旦目标属性被赋值，就会调回此方法。

  `configurable`:如果为`false`，则任何尝试删除目标属性或修改属性性以下特性（`writable, configurable, enumerable`）的行为将被无效化。

  `enumerable`:是否能在`for...in`循环中遍历出来或在`Object.keys`中列举出来。

#### 什么是数据劫持

当我们访问或设置对象的属性的时候，都会触发相对应的函数，然后在这个函数里返回或设置属性的值 。我们可以在触发函数的时候做点我们自己想做的事情，这也就是“劫持”操作。在`Vue`中其实就是通过`Object.defineProperty`来劫持对象属性的`setter`和`getter`操作，并“种下”一个监听器，当数据发生变化的时候发出通知。即属性在赋值的时候触发`set`方法， 。 

```javascript
var data = {
    name:'Martin'
}

Object.keys(data).forEach(function(key){
    Object.defineProperty(data,key,{
        enumerable:true,
        configurable:true,
        get:function(){
            console.log('get data');
        },
        set:function(){
            console.log('监听到数据发生了变化');
        }
    })
});
data.name; //控制台会打印出 “get data”
data.name = 'Martin Que' //控制台会打印出 "监听到数据发生了变化"
```

#### vue实现步骤

![01](E:\learn\TC\兵\01.png)

- `Observer`用来实现对每个`vue`中的`data`中定义的属性循环用`Object.defineProperty()`实现数据劫持，以便利用其中的`setter`和`getter`，然后通知订阅者，订阅者会触发它的`update`方法，对视图进行更新。 
- 在`vue`中`v-model`，`v-name`，`{{}}`等都可以对数据进行显示，也就是说假如一个属性都通过这三个指令了，那么每当这个属性改变的时候，相应的这个三个指令的`html`视图也必须改变，于是`vue`中就是每当有这样的可能用到双向绑定的指令，就在一个`Dep`中增加一个订阅者，其订阅者只是更新自己的指令对应的数据，也就是`v-model='name'`和`{{name}}`有两个对应的订阅者，各自管理自己的地方。每当属性的`set`方法触发，就循环更新`Dep`中的订阅者。 
- 首先我们为每个`vue`属性用`Object.defineProperty()`实现数据劫持，为每个属性分配一个订阅者集合的管理数组`dep`；然后在编译的时候在该属性的数组`dep`中添加订阅者，`v-model`会添加一个订阅者，`{{}}`也会，`v-bind`也会，只要用到该属性的指令理论上都会，接着为`input`等`view`层面会添加监听事件，修改值就会为该属性赋值，触发该属性的`set`方法，在`set`方法内通知订阅者数组`dep`，订阅者数组循环调用各订阅者的`update`方法更新视图。 

#### 发布订阅模式

订阅发布模式（又称观察者模式）定义了一种一对多的关系，让多个观察者同时监听某一个主题对象，这个主题对象的状态发生改变时就会通知所有观察者对象。 