JS基础学习

## 主流浏览器

(市场份额大于3%, **有独立研发的内核**)

> 1. IE					Trident
> 2. Chrome                               Webkit/Blink  blink--2014年后抽出来的
> 3. Firefox                                 Gecko
> 4. Opera                                  Presto
> 5. Safari                                  Webkit
>

## JS的特点

> 1. 解释性语言  解释一行执行一行
> 2. 单线程 同一时间只能干一件事
> 3. 由ECMScript DOM BOM 三部分组成
>

## 原始值

> 1. Number, 
> 2. Boolean, 
> 3. String,
> 4. undefined, 
> 5. null  **占位符**.
> 6. symbol(es6新类型)

## 引用值

使用的是同一个地址

> 1. Object, 
> 2. function, 
> 3. Array,
> 4. ...
> 5. data
> 6. RegExp

## JS运算符

不容易记得的几个:

> 1 / 0 = Infinity                                                    !Infinity = false	 Number类型
>
> 0 / 0 = NaN(not a number    非数)                     !NaN = true              Number类型

```js
var a = 1;
var b = a ++ + 1;   //先 a + 1    后执行 a++
console.log(a) //2
console.log(b) //2

var a = 1;
var b = a -- + -- a;   //先 --a 则a = 0  所以为0 + 0
console.log(b); //0  
console.log(a); //-1
```

## JS比较运算符

> NaN == NaN   //false  唯一的一个自己不等于自己的.

## JS逻辑运算符

> " && ", " || ", " ! "
>
> **短路语句:**
>
> ​	[data] && 用到data的一个语句
>
> ​	可以先判断data是否存在,存在才会执行后面的语句
>
> **" || " 运算符兼容应用**
>
> ```js
> div.onclikc = function (e){
>     var event = e; //非IE浏览器写法
>     var event = window.event; //IE浏览器写法
>     
>     var event = e || window.event;
> }
> ```

## JS循环

> break语句可以用于循环语句, 也可以用于分支语句(switch), 而continue语句只能用于循环语句;
>
> break语句用于跳出全部循环,而continue用于结束本次循环

## JS typeof \类型转换

### 数据类型:

> 1. number
>
> 2. boolean
>
> 3. string
>
>    ↑ 基础值 ↑
>
> 4. object
>
> 5. undefined
>
> 6. function
>
> 7. symbol

### typeof:

```js
//number
typeof(10);
typeof(NaN); //NaN在JavaScript中代表的是特殊非数值,它本身是一个数字类型
typeof(Infinity);

//boolean
typeof(true);
typeof(false);

//string
typeof("hello world!")

//undefined
typeof(undefined)
typeof(a) //a为不存在的变量

//object
//对象,数组,null返回均为object

//function
//函数

//symbol
typeof Symbol()   //ES6提供的新的类型

```

### 类型转换

显式转换

``` js
Number('a')  // NaN
Number(undefined) // NaN
Number(null) //0

parseInt(123.8) //123
parseInt('123.8') //123
parseInt(true) // NaN
parseInt(null) //NaN
parseInt(undefined) //NaN
parseInt('123px') //123  从数字位开始,识别到非数字为结束
parseInt('a123px'); parseInt('123px12') //123
parseInt(10, 16) //把10当成16进制转换为10进制

parseFloat(12)  //12

String(undefined) //'undefined'

var a = undefined;
a.toString() //会报错 
			//Uncaught TypeError: Cannot read property 'toString' of undefined
var a = null;
a.toString() //会报错 
			//Uncaught TypeError: Cannot read property 'toString' of null
var a = 10;
var num = demo.toString(8)  //把10当成10进制转换为8进制

Boolean(1) //true
```

隐式转换

调用的都是显示转换的方法

```js
isNaN('abc');  //true
isNaN('NaN');  //true
isNaN('123');  //false
isNaN(123);  //false
// isNaN执行了 Number('abc') == NaN 

+ 'abc' //NaN
-
++ '123' 124
//也调用了Number

'' + 123 //'123'
//调用了String

1 > 2 > 1 //false  从左到右计算
/*********比较特殊的**********/
//undefined 和 null 与任意值比较都为 false
undefined == null //true
NaN == NaN //false



```

## 函数

高内聚 弱偶合

不会输出地址,只会输出所属的房间

函数引用  test   \\\   函数执行  test()

函数声明:

```js
function theFirstName() {
    
}
```

命名函数表达式

```js
//表达式会忽略名字,充当了表达式就不是一个函数声明了
var test = function theFirstName() {
    
}

test.name  //tehFistName
```

匿名函数表达式 --  函数表达式

```js
var test = function () {
    
}
test.name // test
```

arguments -- [] 类数组的数组   (实参列表)

```js
function test(a){ 
    // arguments -- [1, 2, 3] 实参列表
}

test(1, 2, 3)
//test.length 为形参长度 
//arguments.length 为实参长度

//arguments和形参有 映射规则(你变我就变)
//但是不是同一个变量
function test(a, b){
	b = 2;
    console.log(aruments[1]); // undefined
}
test(1);
/*******/
function tset
function test(a, b){
	b = 2;
    console.log(aruments[1]); // 2
}
test(1, 3);

```

return -- 终止函数 & 返回值



------



## 递归

> 1. 找规律
> 2. 找出口
>
> 唯一的优点就是使代码变得更简洁
>
> 缺点执行效率低,很慢

```js
function mul(n) {
    if(n == 1 || n == 0){
        return 1;
    }
    return n * mul(n - 1);
}

mul(5)  //120
```



------



## 暗示全局变量

1. 任何变量,如果未经声明就赋值,此变量就为全局所有

2. 所有全局变量都是window的属性--window就是全局的域


> 即 a=123  ===> window.a =123

## 预编译

1. 预编译发生在函数执行的前一刻
2. 预编译现象:
   1. 函数声明整体提升
   2. 变量声明提升
3. 预编译四部曲:
   1. 创建AO对象---AO对象  Activation Object (执行期上下文)
   2. 找形参和变量声明,将变量和形参名作为AO对象的属性名, 值为undefined
   3. 将实参值和形参值相统一
   4. 在函数体里找变量声明, 值为函数体

全局也会发生预编译, 会创建GO对象 Global Object

GO === window





## 作用域(scope)

[[scope]]是对象的一个隐式属性

每个JavaScript函数都是一个对象,其中对象中的一些属性是可以直接访问的,但有些不可以,不可以的这些属性仅供JavaScript引擎存取,[[scope]]-作用域就是其中一个.

[[scope]]:指的就是作用域,其中储存了执行期上下文的集合

作用域链:[[scope]]中所储存的执行期上下文对象的集合呈链式链接,这种链式链接叫做作用域链

查找变量时:从作用域链的顶端(数组的第0位即该函数执行期的AO对象),依次向下查找.

```js
function a(){
    function b(){
        function c(){
            
        }
        c();
    }
    b();
}
a();

a defined a.[[scope]] --> 0 : GO
a doing   a.[[scope]] --> 0 : a-AO
						1 : GO
                        
b defined b.[[scope]] --> 0 : a-AO
						1 : GO
b doing   b.[[scope]] --> 0 : b-AO
						1 : a-AO
						2 : GO  
                        
c defined c.[[scope]] --> 0 : b-AO
						1 : a-AO
						2 : GO 
c doing   c.[[scope]] --> 0 : c-AO
    					1 : b-AO
						2 : a-AO
						3 : GO  
                        
//查找变量时:从作用域链的顶端(数组的第0位即该函数执行期的AO对象),依次向下查找.
```

立即执行函数

执行完之后立即销毁

与其他函数对比,除了会立即销毁,无其他不同点

()执行符号--被执行符号执行后函数名称会被忽略,也就销毁

只有表达式能被执行符号执行, 函数声明不能被执行符号所执行

```js
(function (){
	var a = 123;
    var b = 234
    console.log(a + b);
}())

//带形参和实参
(function (a, b){
    console.log(a +b);
}(1, 2))

//返回值
var num = (function (a, b){
    var c = a + b;
    return c;
}(1, 2))


//拓展
//函数声明
function test (){
	console.log("hah")
}()  //不能执行因为不是表达式

//函数表达式
var test = function (){
    console.log("hah")
}() //可以执行

+ function test (){                  
    console.log("hah")
}();  //也算函数表达式

// ()  + 都算运算符
// 所以才有
(function (){
	var a = 123;
    var b = 234
    console.log(a +b);
}()) 

function test(a, b, c, d){
    console.log(a + b + c + d);
}(1,2,3,4)
//不报错
//系统理解为
function test(a, b, c, d){
    console.log(a + b + c + d);
}
(1,2,3,4)



```



## 闭包

当内部函数被保存到外部时,将会生成闭包. 闭包会导致原有作用域链不释放,造成内存泄漏

内存泄漏:就是内存占用,导致非常慢加载.

实现共有变量

eg:函数累加器

```js
function add(){
	var count = 0;
	function demo(){
        count ++;
        console.log(count);
	}
	return demo;
}
var counter = add();
counter();
counter();
counter();
counter();

输出1 2 3 4 
```

可以做缓存 (储存结构)

eg:eater

铺垫:

```js
function test(){
    var num = 100 
        function a() {
            num ++;
            console.log(num)
        }
        function b (){
            num --;
            console.log(num)
        }
    return [a,b];
}

var myArr = test();
myArr[0]();
myArr[1]();

输出: 101 100
a和b公用一个testAO
```

实例:

```js
function eater(){
    var food = "";
    var obj = {
        eat : function(){
            console.log("i am eating" + food);
            food = "";
        },
        push : function (myFood) {
            food = myFoodl
        }
    }
    return obj;
}
var eater1 = eater();

eater1.push("");
eater1.eat();
```

私有化变量

```js
function Deng(name, wife){
    var prepareWife = "xiaozhuang";
    
    this.name = name;
    this.wife = wife;
    this.divvorce = function (){
        this.wife = prepareWife;
    }
    this.changePrepareWife = function (target){
        prepareWife = target;
    }
    this.sayPraprewife = function (){
        console.log(prepareWife);
    }
}
var deng = new Deng('deng', 'xiaocheng')
```



## 对象

```js
var person = {
            name: "Daniel",
            age: 21,
            sex: "male",
            health: 100,
            drink: function () {
                console.log("I'm drinking");
                this.health ++;
            }
        }

```

对象的创建方法有: 

1. 字面量;

   1. var obj = {} plainObject 对象字面量/对象直接量

2. 构造函数

   1. 系统自带

      1. new Object()

         1. 相当于一个工厂, 每次生成的都一样, 但是彼此相互独立

         2. var obj = new Object();

            包装类

            1. Array()  

            2. Number() 

            3. Boolean()

            4. String()

            5. Date()

   2. 自定义

      ```js
      //自定义构造函数
      //构造函数,命名的规则: 大驼峰式 ThePerson
      //可以通过 this. 生成默认值
      //有 new就可以生成对象
      function Person(val) {
      	this.age = 0;
          this.face = 'cute';
          this.height = val;
      }
      var person1 = new Person('179');
      
      //构造函数 基本属性
      function Student (name, age, sex) {
          //var this = {}
          this.name = name;
          this.age = age;
          this.sex = sex;
          this.grade = 2017;
          //return this;
      }
      
      var student = new Student('Tom', 18, '男'); 
      ```

      

3. Object.create(原型)方法

## 构造函数内部原理

1. 在函数体前面饮食的加上this = {}
2. 执行 this.xxx =  xx;
3. 隐式的返回this

```js
//构造函数 基本属性
function Student (name, age) {
    //var this = {}
    this.name = name;
    this.age = age;
    this.say = function (){
        console.log(this.say);
    }
    //return this;
}
//this就是对象
var student = new Student('Tom', 18); 
```

## 原型

原型是function对象的一个属性,它定义了构造函数制造出的对象的公共祖先.通过该构造函数产生的对象,可以继承该原型的方法和属性.原型也是对象

```js
Person.prototype.LastName = "Lee";  //2.共有属性
function Person() {  //构造工厂
    
}
var person = new Person()

//原型的增删改查, 不能通过构造函数修改原型

person.constructor -->  funciton Person

//因为有__proto__所以构造函数才可以找原型的东西
```

利用原型特点和概念,可以提取共有属性

对象如何查看原型 -->隐式属性 'proto'

对象如何查看对象的构造函数 --> constructor(构造器)

## 原型链

绝大多数对象都会继承自Object.prototype

Object.create(null)--没原型

连接点就是prototype

```js
Person.prototype = {
    name: 'a',
    sayName: function(){
        console.log(this.name);
    }
}
function Person(){
    this.name = 'b';
}
var person = new Person();

console.log(person.sayName) //b
//sayName里面的this指向是, 谁调用的这个方法, this就指向谁
```

## 拓展

```js
Math.ceil(123.23) //124
Math.floor(123.56) //123
Math.rendom()  //产生0-1的数
```

## call/apply

可以改变this的指向

两者区别, 传参列表不同

test() --> test.call()

Person.call(obj, 'cheng', 300 )  //  this --> obj

```js
function Person (name, age, sex){
    this.name = name;
    this.age = age;
    this.sex = sex;
}
function Student(name, age, sex, tel, grade){
	Person.call(this, name, age, sex);
    
    this.tel = tel;
    this.grade = grade;
}
var student = new Student('sunny', 123. 'male', 139, 2017);
```

apply只能传一个实参, 且必须为数组形式

Person.apply(this, [name, age, sex])

call 需要把实参按照形参的个数传进去

apply 需要传一个arguments进去

apply(null, arguments) ==> apply(arguments)

## 继承发展史

#### 原型链

> 过多的继承了没用的属性

#### 借用构造函数

> 不能继承借用构造函数的原型
>
> 每次构造函数都要多走一个函数
>
> ```js
> function Person (name, age, sex){
>     this.name = name;
>     this.age = age;
>     this.sex = sex;
> }
> function Student(name, age, sex, tel, grade){
> 	Person.call(this, name, age, sex);
>     
>     this.tel = tel;
>     this.grade = grade;
> }
> var student = new Student('sunny', 123. 'male', 139, 2017);
> ```
>
> 

#### 共享原型

> 不能随便改动自己的原型
>
> ```js
> Father.prototype.lastName = "Deng";
> function Father(){
> }
> function Son(){
>     
> }
> Son.prototype = Father.prototype
> 
> //封装
> Father.prototype.lastName = "Deng";
> function Father() {
>     
> }
> function Son (){
>     
> }
> function inherit(Target, Origin){
>     Target.prototype = Origin.prototype;
> }
> inherit(Son, Father);
> ```
>
> 

#### 圣杯模式

```js
Father.prototype.lastName = "Deng";
function Father() {
    
}
function Son (){
    
}
function inherit(Target, Origin){
    function F(){

    }
    F.prototype = Origin.prototype
    Target.prototype = new F();
    Target.prototype.constuctor = Target;
    Target.prototype.uber = Origin.prototype;
}
inherit(Son, Father);

/*********/
var inherit = (function (){
    function F(){

    }
    return function inherit(Target, Origin){
    F.prototype = Origin.prototype
    Target.prototype = new F();
    Target.prototype.constuctor = Target;
    Target.prototype.uber = Origin.prototype;
}
}());
```

## 链式调用模式(连续调用) 

```js
var a = {
	b(){
        console.log('hah')
        return this;
    }
    c(){
        console.log('hah')
        return this;
    }
}
a.b.c 
//this = a
```

## 属性表示方法

obj.name  ==> obj['name']  

```js
//属性名拼接

var deng = {
    wife1: {name: "xiaoli"},
    wife2: {name: "Lee"},
    sayName: function (num){
        return this['wife' + num];
    }
}
```

## 对象枚举

 for in

```js
var obj = {
    name: 'hah',
    age: 1
}
for(var prop in obj){
    //console.log(obj.prop) 全部都是undefined 因为obj.prop ==> obj['prop']
    console.log(obj[prop])
    
    //hasOwnProperty  判断属性是不是自己的
    if(obj.hasOwnProperty(prop)){
        console.log(obj[prop]); 
    }
    
    //in 'name' in obj      ---true
}

//instanceof
// A instanceof B
//看A对象的原型链上有没有B的原型
function B() {
    
}
var A = new B();
//!!!!!可以判断一个变量 到底是数组 还是对象!!!!!
[] instanceof Array   true
obj instanceof Array  false
obj instanceof Object  true

```

## this

预编译过程 this --> window

全局作用域 this -->window

call/apply  可以改变函数运行时this指向

obj.funciton()  function里的this指向obj

## 克隆

1. 判断是不是原始值
2. 判断是数组还是对象
3. 建立相应的数组或对象

```js
function deepClone(origin, target) {
	var target = target || {},
        toStr = Object.prototype.toString,
        arrStr = "[object Array]";
    for(var prop in origin){
        if(origin.hasOwnProperty(prop)) {
            if(origin[prop] !== "null" && typeof(origin[prop]) == 'object'){
                /*if(toStr.call(originp[prop]) == arrStr){
                    target[prop] = [];
                }else{
                    target[prop] = {};
                }*/
                target[prop] = toStr.call(originp[prop]) == arrStr ? [] : {};
                deepClone(origin[prop], target[prop]);
            }else{
                target[prop] = origin[prop];
            }
        }
    }
    return target;
}
```

## 数组常用的方法

```js
// ES3.0
// 改变原数组
// push, pop, shift, unshift, sort, reverse
// splice
//---------
// 不改变原数组
// concat,join -> split, toString, slice

// push 向数组的最后添加一个或更多元素，并返回新的长度
Array.prototype.push = function() {
    //push 实现原理
    for(var i in arguments){
        this[this.length] = arguments[i];
    }
    return this.length;
}
// pop 把数组的最后一个元素删除，并返回第一个元素的值,传参没用

// shift 把数组的第一个元素从其中删除，并返回第一个元素的值

// unshift 向数组的开头添加一个或更多元素，并返回新的长度

// sort 给数组排序 升序 可以把方法传入
// 1. 必须写两形参
// 2. 看返回值
/**
		1). 当返回值为负数时, 那么前面的数放在前面
		2). 为正数,那么后面的数在前
*/
arr.sort(function (a, b){
    arr.sort(function (a,b){
     return a - b   
    }
});

// sort 乱序
    var arr = [1, 2, 3, 4, 5]
    arr.sort(function() {
        return Math.random() - 0.5;
    });
// reverse ---- 降序

// splice(从第几位开始, 截取多少的长度, 在切口处添加新的数据) (3, 0, 4)第三位插入
    
    
    
    
//concat 将两个数组链接
    arr.concat(arr1)
//toString 转换为字符串 
    arr.toString()  //"1, 2, 3, 4, 5"
//slice 只截取不删除
 
//join 数组之间加入某个字符串, 链接成字符串
    arr.join("-") //"1-2-3-4-5"
//split 按照什么拆分成数组
    let a = "1-2-3-4-5"
    a.split("-") //[1, 2, 3, 4, 5]

```

字符串

str.substr(str.length-4)

类数组

```js
// 属性要为索引(数字)属性, 必须有length属性, 最好加上push方法
var obj = {
    "0" : 'a',
    "1" : 'b',
    "2" : 'c',
    "length" : 3,
    "push" : Array.prototype.push,
    "splice" : Array.prototype.splice,  //加入splice后 obj会和数组一模一样
}
```

```js
// 数组去重
Array.prototype.unique = function (){
    var temp ={},
        arr = [],
        len = this.length;
    for(var i in len){
        if(!temp[this[i]]){
            temp[this[i]] = "abc"; //等于一个任意不为false的值
            arr.push(this[i]);
        }
    }
    return arr;
}
```

## try-catch

当有一行代码报错时, 不会抛出错误, 因此try外面的后续代码会继续执行, 但是try的后续代码不会执行.

catch则是接收错误对象  有:  e.message / e.name

### Error.name的六种值对应的信息

1. ReferenceError: 非法或不能识别的引用数值      (未经声明就用)
2. SyntaxError: 发生语法解析错误          (中文符号之类的)
3. TypeError: 操作数组类型错误
4. RangeError: 数值越界
5. UrlError: Url处理函数使用不当
6. EvalError: eval()的使用与定义不一致

## ES3.0/ES5.0

浏览器是基于es3.0 + es5.0的新增方法 使用的

es5.0严格模式下,es3.0和es5.0产生冲突的部分才会使用es5.0, 否则会使用3.0

```js
"use strict"  //严格模式
/**
*不再兼容es3的一些不规则的语法.使用全新的es5规范
*两种用法
*	全局严格模式
*	局部函数内严格模式 (推荐)
*就是一行字符串, 不会对不兼容严格模式的浏览器产生影响
*
*不支持with, arguments.callee, func.caller, 
*变量赋值前必须声明, 
*局部this必须被赋值(Person.call(null / undefined)赋值什么就是什么),
*拒绝重复属性和参数
*/

function test() {
    console.log(arguments.callee);  //会报typeError错误
}
test();

//with会更改作用域链 会导致程序变得非常慢 所以ES5不支持with
with(document){
    write('a');
}
```

## DOM

DOM BOM 返回的数组都是类数组

DOM定义了表示和修改文档所需的方法. DOM对象即为宿主对象,由浏览器厂商定义,用来操作html和xml功能的一类对象的集合.也有人称DOM是对HTML以及XML的标准编程接口.

```js

var div = document.getElementsByTagName('div')[0]
div.style.backgroundColor = "red";
div.onclick = function (){
    this.style.backgroundColor = 'green'
}

var speed = 1;
var timer = setInterval(function (){
    speed += speed/20;
    div.style.left = parseInt(div)
})
```

### 查看元素节点

document代表整个文档

document.getElementById()   //!! 元素id在ie8以下的浏览器, 不区分id大小写, 而且也返回匹配name属性的元素

.getElementsByTagName() //!! 标签名  任意浏览器都能使用

.getElementsByName() //!! 需注意,只有部分标签name可以生效(表单, 表单元素, img, iframe)

.getElementsByClassName() // 类名 -> ie8和ie8以下的ie版本中没有, 可以多个class一起

/***非实时的↓***/

.querySelector() // 属性选择器 在ie7和ie7以下的版本中没有   只选择一个

.querySelectorAll() // 属性选择器 在ie7和ie7以下的版本中没有

### 节点的类型

1-3比较重要 8-9其次

元素节点 - 1(返回值,可用于判断是什么节点)

属性节点 -2

文本节点 -3 

注释节点 - 8

document -9

DocumentFragment -11

### 节点的四个属性

nodeName (元素的标签名,以大写形式表示,只读)

nodeValue (Text节点或Comment节点的文本内容,可读写)

//!!     nodeType (该节点的类型)--数字类型

attributes (Element节点的属性集合)----后期没用    用getAttribute和setAttribute

### 节点的一个方法 

Node.hasChildNodes()    查看是否有

### 遍历节点树

parentNode -> 父节点(最顶端的parentNode为#document);

childNodes -> 子节点们

firstChild -> 第一个子节点

lastChild -> 最后一个子节点

nextSibling ->后一个兄弟节点 previousSibling ->前一个兄弟节点

### 基本元素节点树的遍历

IE9及以下不兼容    children最常用

parentElement -> 返回当前元素的父元素节点(IE兼容)

children -> 只返回当前元素的元素子节点

node.childElementCount === node.children.length当前元素节点的子元素节点个数(IE不兼容)

firsElementChild -> 返回的是第一个元素节点(IE不兼容)lastElementChild -> 返回的是第一个元素节点(IE不兼容)

nextElementSibling/previousElementSibling -> 返回后一个/前一个兄弟元素节点(IE不兼容)

### DOM结构树

document --> HTMLDocument.prototype --> Document.prototype

![](C:\Users\MMP\Desktop\DOM结构树.png)

### DOM基本操作

1. getElementById方法定义在Document.prototype上, 即Element节点上不能使用.
2. getElementsByName方法定义在HTMLDocument.prototype上, 即非html中的document不能使用(XMLDocument,Element)
3. getElementsByTagName方法定义在Document.prototype和Element.prototype上
4. HTMLDocument.prototype定义了一些常用的属性,指代文档的根元素,在HTML文档中,他总是指代<html>元素
5. getElementsByClassName querySelectorAll querySelector在Document.prototype, Element.prototype类中均有定义

增

document.createElement();

document.createTextNode();

document.createComment();

document.createDocumentFragment();

插

PARENTNODE.appendChild();   (是剪切操作)

PARENTNODE.inserBefore(a, b);

删

parent.removeChild();

child.remove();

替换

parent.replaceChild(new, origin);

## Date对象,定时器



```js
 //记录的是new Date()创建时候的时间
//时间戳  .getTime()

//测程序运行时间                     
var firstTime = new Date().getTime();

for(var i = 0; i < 10000000; i++){};

var lastTime = new Date().getTime();
console.log(lastTime - firstTime);


//setInterval
var a =  setInterval(function (){
    
},1000);
var b =  setInterval(function (){
    
},1000);

//clearInterval
clearInterval(a) //会清除返回值, 且会停止计时器   a = 1   b = 2

//setTimeout
var c = setTimeout(function (){
    console.log("a");
}, 1000);
//等待1s后执行,且只执行一次

//clearTimeout
clearTimeout(c)  //可以提前结束
```

## 滚动条

IE9以上

window.pageXOffset/pageYOffset

IE8和IE8以下的浏览器

document.body.scrollLeft/Top   ie8 ie5 ie4

document,documentElement.scrollLeft/Top ie7 ie6

兼容性比较混乱, 用时取值两个值相加,因为两个不可能同时有值

document.body.scrollLeft + document,documentElement.scrollLeft

```js
function getScrollOffset() {
    if (window.pageXOffset){
        return {
            x : window.pageXOffset,
            Y : window.pageYOffset
        }
    }else{
        return {
            x: document.body.scrollLeft + document.documentElement.scrollLeft,
            y: document.body.scrollTop + document.documentElement.scrollTop,
        }
    }
}
```

## 浏览器兼容(一般只有ie做兼容要用)

标准模式

怪异/混杂模式  兼容前几个版本浏览器 (一般只有ie做兼容要用)

## 查看视口的尺寸

window.innerWidth/innerHeight

IE8及IE8以下不兼容

document.documentElement.clientWidht/clienHeight

标准模式下,任意浏览器都兼容

document.body.clientWidth/clienHeight

适用于怪异模式下的浏览器

## 脚本化CSS

```js
function getStyle(elem, prop){
    if(window.getComputedStyle){
        return windwo.getComputedStyle(elem, null)[prop];  //null如果为伪元素, 则可以获取伪元素的css
    }else{
        return elem.currenStyle[prop];  //兼容IE
    }
} 
```

## 事件

```js

div.onclick = function (){ //绑定点击事件
    this.className = "yellow"  //修改class的值   this指向DOM本身
}

/********/
<div onclick="console.log(a)">  //句柄,同样可以绑定点击事件   

/********/   
div.addEventListener('click', function(){
    console.log('a');   //this指向DOM本身
},false)

/********/ 
div.attachEvent('onclick',function(){
    console.log(this)
})   //this指向window

div.attachEvent('onclick',function(){
    handle.call(div)
});   //this指向DOM
funciton handle(){
    console.log(this)
}


//!! 兼容各个浏览器的方法
funciton addEvent(elem, type, handle){
    if(elem.addEventListener){
        elem.addEventListener(type, handle, false);
    }else if(elem.attachEvent){
        elem.attachEvent('on'+type, function(){
            handle.call(elem);
        });
    }else{
        elem['on' + type] = handle;
    }
}

```

## 解除事件处理程序

```js
div.onclick = false/null;
div.removeEventListener(type, funName,false);
div.detachEvent('on'+ type,funName);
//!!   若绑定匿名函数, 则无法解除
```

## 事件处理模型--事件冒泡&捕获

1. 事件冒泡

   > 结构上(非视觉上)嵌套关系的元素, 会存在事件冒泡功能, 即同一事件, 子元素冒泡向父元素. (自底向上)

2. 事件捕获

   > 结构上(非视觉上)嵌套关系的元素, 会存在事件捕获的功能, 即同一事件, 自父元素捕获至子元素(事件源元素)(自顶向下)
   >
   > IE没有捕获事件

3. 触发顺序:先捕获, 后冒泡

4. focus, blur, change, submit, reset, select 等事件不冒泡

5. ```js
   div.addEventListener('click', function(){
       console.log('wrapperBubble');
   },false);  //false表示不捕获,即为事件冒泡  true则为事件捕获   (两者只能存在其一,但可以绑定另一个点击事件)
   ```

## 取消冒泡和阻止默认事件

1. 取消冒泡

   1. w3c标准event.stopPropagation();但不支持ie9以下版本

   2. IE独有event.cancelBubble = true;

   3. 封装取消冒泡的函数 stopBubble(event)

   4. ```js
      function stopBubble(event){
          if(event.stopPropagation){
              event.stopPropagation() = true;
          }else{
              event.cancelBubble = true;
          }
      }
      ```

      

2. 阻止默认事件

   1. 默认事件:

      1. 表单提交

      2. a标签跳转   

          <a href="javascript: void(0)" /> <a href="javascript: console.log(0)" />

         javascript: 可以执行javascript代码, void 相当于 return

      3. 右键菜单

      4. ...

   2. return false; 以对象属性的方式注册的事件才能生效  (句柄)

   3. event.preventDefault(); w3c标注, IE9以下不兼容

   4. event.returnValue = false; 兼容ie

   5. 封装阻止默认事件的函数 cancelHandler(event);

   6. ```js
      function cancelHandler(event){
          if(event.preventDefault){
              event.preventDefault()
          }else{
              event.returnValue = false;
          }
      }
      ```

## 事件对象

1. event || window,event 可以兼容ie

2. 事件源对象

   1. event.target 火狐只有这个
   2. event.srcElement IE只有这个
   3. 这两个 chrome都有

3. 兼容性写法

4. 事件委托

   1. ```html
      <ul>
       	<li>1</li>
          <li>2</li>
          <li>3</li>
          <li>4</li>
          <li>5</li>
      </ul>
      <script>
          //利用事件冒泡和事件源对象进行处理
          //优点:
          	//性能: 不需要循环所有的元素一个一个绑定事件
          	//灵活: 当有新的子元素时不需要重新绑定事件
      	var ul = document.getElementsByTagName('ul')[0];
          ul.onclick = function(e){
              var event = e || window.event;
              var target = event.target || event.srcElement;
              console.log(target.innerText);
          }
      </script>
      ```


## 异步加载JS

1. defer 异步加载,但要等到dom文档全部解析完才会被执行. 也可以将代码写到script标签里.
2. async 异步加载 , 加载完就执行, async 只能加载外部脚本, 不能把js写在script里. 执行时也不阻塞页面
3. 创建script,插入到dom中,加载完毕后callback

```js
function loadScript(url, callback){
    var script = document.creatElement('script');
    script.type = "text/javascript";
    if(script.readyState){  //兼容IE
        script.onreadystatechange = function(){
            if(script.readyState == "complete" || script.readyState == "loaded"){
                tools[callback]()
            }
        }
    }else{ //其他浏览器
        script.onload = function() {
            tools[callback()]
		}
    }
    script.src = url;
    document.head.appendChild(scirpt)
}
```



## 正则表达式

### 转义字符   \

\ 反斜杠    强制转义后面的字符

\n	换行(回车)

\r	行结束

\t	tab键 (制表符)

多行代码

```js
var test = "\
<div></div>\
<span></span>\
";
```

### RegExp (正则表达式)

```js
var reg = /abc/; 
var str = "abcd";
reg.test(str) // true  匹配str里是否有 abc片段

var reg = /abc/i; // ignoreCase 忽视大小写
		 /abc/igm; // 三种 / g 全局匹配 / m 多行匹配

//!!
var reg = /abc/;
var reg1 = /abc/g;
var reg2 = /^abc/g;
var reg3 = /^abc/gm;
var str = "abcabcabc";
var str = "abc/nabc/nabc";
str.match(reg)  // ["abc"]
str.match(reg1) // ["abc", "abc", "abc"]
str.match(reg2)  // ["abc"]  / 以abc开头的字符串才会匹配到
str.match(reg3) // ["abc", "abc", "abc"]  //换行后 全局匹配 abc都是每一行开头 所以可以匹配到

//第二种创建方法
var reg  = new RegExp("abc", "i")



//表达式
var reg = /[0-9A-z][cd][d]/g; // []代表一位 0-9 表示0到9数字都可以 A-z表示52个英文字符(大写+小写)

var reg = /(abc|bcd)[0-9]/g;  //第一位为abc或bcd
var str = "bcd2"
str.match(reg)  //bac2

//元字符

42′
```

