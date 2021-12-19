

## JS基础![img](https://s2.loli.net/2021/12/19/xsqDv1Zzu8L6gXP.jpg)

[State of JS 2020](https://2020.stateofjs.com/zh-Hans/)

[JavaScript 和 HTML DOM 参考手册 (w3school.com.cn)](https://www.w3school.com.cn/jsref/index.asp)

脚本语言：运行过程中由js引擎逐行解释执行。

编译： 将源码编译为中间码，最后解释执行

最初是用来执行表单验证。

JS是单线程程序

**HTML中使用双引号， JS中使用单引号**

### 浏览器执行

浏览器组成：

* 渲染引擎：内核：解析html 和 css。 blink, -webkit
* js引擎： 读取js，并处理 chrome v8 (独立于浏览器)：会在window / global对象

**js 组成**

* ECMAScript: 语法规定 编程语法和基础核心知识，是js语法标准 

  **ES6** [ES6、ES7、ES8、ES9、ES10、ES11、ES12、ES13新特性大全<精心整理> - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/427857918)

* DOM： 页面文档对象

* BOM： 浏览器对象

引入js代码

* 行内JS: 
* 内嵌JS: 
* 外部JS： 

### 语法

#### 注释

// 单行

/* 多行注释

*/  

#### 输入输出

```js
//弹出提示框
alert("非法访问！")
// 提示输入框
let num = prompt("请输入年龄：")
//浏览器控制台日志
console.log(num)
```

#### 变量

标识符

保留字

关键字

声明 和 赋值

```js
var name;  //声明了一个name的变量。没有分配内存
//赋值
name = 'age'
//初始化
var age = 10
//多行声明
var name='ss', 
    age=18;
//只声明不赋值,输出为undefind
var str; 
//没有声明直接使用，直接使用会报错
console.log(tel)
//直接赋值使用, 可以使用会被升级为全局变量
age = 10, console.log(age) = 10;
//重复赋值，新值会覆盖旧值
```

##### 语法 和 规范

* 由字母和数字，_, $ 组成
* 严格区分大小写
* 不能数字开头
* 不能关键字
* 有语义
* 驼峰法

##### 数据类型

不同的类型占用的内存不同。JS是动态的（弱类型）语言，只有在运行时才确定类型

###### 基本数据类型

* 数字类型 Number （可包含整形和浮点）默认0： 底层为float 存储

  ```js
  var a = 10,
      b = 3.14,
      //八
      c = 0o13,
      //十六
      d = 0x14,
      //二进制
      e = 0b11;
  Number.MIN_SAFE_INTEGER 最小安全整数（即–（2 53 – 1））
  Number.MAX_VALUE：数值最大值：1.7976931348623157e+308 = (2^53 -1) * 2^971
  Number.MIN_VALUE：数值最小值：-9007199254740991
  console.log(Number.MAX_VALUE * 2); = infinity = 无穷大， -infinity：无穷小
  Number.NaN : 非数字
  isNaN(): 数字返回false，不是数字返回true
  
  ```

* Boolean： 默认false

  参与数值运算时 true = 1， false = 0； 只声明没有赋值，则为undefined。 

* String: 默认‘ ’

  ```js
  str = 'me to "x"'  外单内双
  str = "me to 'x' " 外双内单
  转义字符
  str = '\n'
  ```

  字符串的方法

  * length(str): 字符串的长度

  * str + var ：只要有字符串 + 其他类型，结果为字符 

    > **数值相加，字符相连** 。
    >
    > todo [JS中的加号+运算符详解 - MasterYao - 博客园 (cnblogs.com)](https://www.cnblogs.com/MasterYao/p/7783004.html)
    >
    > > **字符串拼接总结**
    > >
    > > * str + var ：建议100字符以下。 会创建一个新的内存区域存储拼接值，并销毁原值
    > >
    > > * str.concat(str1,st2): concat()连接字符串
    > >
    > > * array. join(“/”) ：第一种消耗更少的资源，速度也更快
    > >
    > > * 使用模板字符串，以反引号（ ` ）标识: var str = `hello ${str}Script`
    > >
    > > * 自定义stringbuffer
    > >
    > >   ```js
    > >   function StringBuffer() {
    > >       this.__strings__ = new Array();
    > >   }
    > >   StringBuffer.prototype.append = function (str) {
    > >       this.__strings__.push(str);
    > >       return this;    //方便链式操作
    > >   }
    > >   StringBuffer.prototype.toString = function () {
    > >       return this.__strings__.join("");
    > >   }
    > >   ```
    > >
    > >   

  

* undefined： 

  undefined + 1 = NaN

  undefined + true = NaN

  undefined + str = undefinedstr

* Null：

  null + str = nullstr

  null + 1 = 1
  
  既然`typeof null`返回的是`object`，而且`Boolean()`转换对象会得到`true`，然而`Boolean(null)`却是`false`
  
  null不是一个空引用, 而是一个原始值; 它只是期望此处将引用一个对象, 注意是"期望", typeof null结果是object, 这是个历史遗留bug. 在ECMA6中, 曾经有提案为历史平反, 将type null的值纠正为null, 但最后提案被拒了

###### 检测数据类型

* typeof  str  = string , 

  ```js
  局限性：
  typeof null = object. 无法检测对象类型
  数组还是正则都返回的是"object"
  ```

* instanceof/ **constructor**检测某一个实例是否属于某一个类

  ```js
  [] instanceof Array //->true
  /^$/ instanceof RegExp //true
  console.log([] instanceof Object);//->true
  console.log([].constructor === Array);//->true
  console.log([].constructor === Object);//->false
  //constructor可以避免instanceof检测数组的时候,用Object也是true的问题
  console.log({}.constructor === Object);//true
  console.log([].constructor === Object);//false
  
  ```

* Object.prototype.toString常用来判断对象值属于哪种内置属性，它返回一个JSON字符串——"[object 数据类型]"

  在类的原型继承中,instanceof检测出来的结果其实是不准确的

###### 数据类型转换

* 转为字符串

  1. 隐式转换：+号拼接: 被优化了 可以直接使用
  2. num. tostring(16):指定16进制字符串
  3. String( num ) 
     - 如果值有`toString()` 方法,则会调用 `toString()` 方法;
     - 如果值是`null`, 则会返回 `"null"`;
     - 如果值是`undefined` 则会返回`"undefined"`;
  4. concat
  5. join()
  6. `${}`

* 转为数值型

  1. parseInt( var )

     > * 如果在转换字符串的话，会忽略前面的空格，直到找到第一个非空格字符。
     > * 如果第一个字符不是数字字符或负号后不是数字字符，就会返回NaN。
     > * 如果是空字符串，就会返回NaN。
     > * 如果第一个字符是数字字符，parseInt()会继续解析下去，直到解析完或遇到了一个非数字字符。
     > * 因为小数点不是有效的数字字符，类似"22.5" 会被转换为22 。**浮点转整数**
     > * -parseInt能解析不同进制的数字字符。parseInt (‘0xa1’, 16)
     > * 因为javascript引擎不同，ECMAScript3和ECMAScript在解析八进制字符串时存在分歧，建议都加上进制参数。

  2. parseFloat()

     字符串从头解析到尾，或忽略前面的空格，直到遇到第一个无效的浮点数字字符为止.
     第一个小数点有效，之后的小数点就无效，后面跟着的字符串将会被忽略。
     可以识别不同进制的浮点数值格式，但都是转换为十进制值，无第二个参数指定转换进制。
     十六进制的字符串始终会被转化为0。
     如果解析的是整数，没有小数点或是小数点后都是零，会返回整数。

  3. Number()

     > * Boolean ,false 转化为 0 , true 转化为 1;
     >
     > * 如果是数值,则只进行简单的传入和传出;
     >
     > * null 转化为 0 ;
     >
     > * undefined 返回 NaN
     >
     > * 如果是字符串,则遵循以下规则:
     >
     >   > * 如果字符串中值包含数字(包括前面带正号或负号的情况),则转化为十进制.
     >   > * 如果字符串中包含有效的浮点数,则会将其转化为对应的浮点数值
     >   > * 如果字符串中包含有效的进制格式，例如 “0xf” ，则将其转换为相同大小的十进制数值。
     >   > * 如果是空字符串,则转化为0
     >   > * 如果字符串中包含上述格式以外的字符,则转为 NaN
     >
     > * 如果是对象,则调用对象的valueOf()方法,然后依照前面的规则转换返回的值,如果转化的结果是 NaN ,则调用对象的 toString() 法然后再依照前面的结果返回响应的值.

  4. 隐式转换（- ,* ,/）

     ```
     + :正号
     var x = +‘12’
     ‘12’ - 1
     '12' - '1'
     '12' * 1
     '12' / 1
     ```

* 转为boolean

  Boolean():总结:只有`undefined`,`null`, `0` ,`空字符串`,`NaN` 会转化为 `false` ,其余均为 `true`.

* `valueOf()`返回字符串对象的字符串、数值或者[布尔值](https://www.zhihu.com/search?q=布尔值&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A56450844})表示。通常与`toString()`方法返回相同。

###### 复杂数据类型



#### 运算符

表达式：有数字，运算符、变量等组成的式子。有返回值

返回值：



##### 算术运算符

+，  -，*，/，%：

%： 判断整除 余数为0

todo : 浮点数参与运算就会有精度问题（存储方式问题）

解决方案：

1. 浮点数转换字符串，分隔成为整数部分和小数部分，小数部分再转换为整数，
2. Math.js

**不要直接判断两个浮点数是否相等**

解决方法：

1 . 精度判断 

```js
console.log(Math.abs(0.1 + 0.2 - 0.3) <= Number.EPSILON);
```



2.`NumberObject.toFixed(num);`**Number四舍五入为指定位数的小数**// num代表要保留的小数位数。存在精度问题

```
重写方法
Number.prototype.toFixed = function (num) {
    let times = Math.pow(10, num)
    const  adjust = this >= 0 ? 0.5:-0.5;
    let des = this * times + adjust;
    des = parseInt(des, 10) / times;
    return des + '';
}
```

##### 递增和递减

* i++: 先赋值，后+1
* ++i: 先+1， 后赋值

##### 比较运算符

\>=, 

==：会转换，默认转换字符串数据类型，18==‘18’ true

!=：

===：全等，值和类型完全一致

！==：

##### 逻辑

&&。 II， ！。

**短路运算**：逻辑中断：

左边的值确定结果了，则中断右边的执行。否则使用右边 1 && 2 = 2， 0 && 1 = 0， 0 || 1 = 1， 1 || 0 = 1

##### 赋值

+=，%=

##### 优先级

（）， ！++ --， * / % + -， 。 先看逻辑运算符&&。||，划分区域判断各个表达式的值

##### 位运算

&，真真为真，其余为假

```js
   1001
 & 1010
   -------
   1000
//奇数的二进制末位为1，偶数为0
if(n & 1) {
    console.log('n为奇数');
} else {
    console.log('n为偶数');
}
1）清零
var num = 100111;
num = num & 0;
2）取一个数的指定位
X=1010 1110 的低4位，
Y=0000 1111，
X&Y=0000 1110
```

 |， 假假为假，其余为真

```js
      1001
    | 1010
    -------
      1011
// 整数与0的位或运算，都是本身。浮点数不支持位运算，过程中会自动转化成整数，利用这一点，可以将浮点数与0进行位或运算即可达到取整目的。

console.log(15.22 | 0); // 15
// 常用来对一个数据的某些位设置为1
X=1010 1110 
Y=0000 1111
X|Y=1010 1111
```

~，真为假，假为真

```js
9二进制位非运算

    ~ 0000000000000000 0000000000001001
    -------取反
      1111111111111111 1111111111110110
    -------符号位不变，其余取反
      1000000000000000 0000000000001001
    -------加1
      1000000000000000 0000000000001010
~1=-2
~0=1
~x = -(x + 1)
-x = ~x + 1 :取反数
// indexof 取不到返回-1，取到了返回位置0，1...
~-1=0，~0=-1, 
if(~str.indexOf(search)){
  /*code*/  
}
```

 ^：相同为假，不同为真

- 1、交换律
- 2、结合律 (a^b)^c == a^(b^c)
- 3、对于任何数x，都有 x^x=0，x^0=x
- 4、自反性: a^b^b=a^

```javascript
var a = 3, b = 5;
a ^= b;
b ^= a;
a ^= b;
console.log('a:', a); // 5
console.log('b:', b); // a

1）翻转指定位

比如将数 X=1010 1110 的低4位进行翻转，只需要另找一个数Y，令Y的低4位为1，其余位为0，即Y=0000 1111，然后将X与Y进行异或运算（X^Y=1010 0001）即可得到。

2）与0相异或值不变. 处理0值

例如：1010 1110 ^ 0000 0000 = 1010 1110
```

 <<, >>>

#### 条件分支语句

* if 的（）中的值根据Boolean()函数判断 负值为正

```js
if (){
    
}else if(){
    
}else{
    
}
year % 4 ==0 && year %100 != 0 || year % 400 == 0
```

* 三元运算符：

条件表达式 ? 表达式1 ： 表达式2；条件表达式真返回表达式1， 否则返回表达式2

* switch

  **express 匹配 value 使用的是 ===。如果没有break，会穿透直到break或default：**

  为什么效率比if高：

  * if 的变量在每个条件中都会被读取到寄存器，switch值读一次

  * 采用了 跳转表实现

  tableswitch ： 数组索引查找

  lookupSwitch ：二分法或分支比较

```js
switch(express){
    case value:
        code;
        break;
    ....
    default:
        code
```

#### 循环

* for

  ```js
  for (let i = 0; i < 1; i++) {
      
  }
  let i = 0;
  for(;;){
      if (i <10){
          break;
      }
      i++;
  }
  ```

* while

  while (){}

* do while

  do {

  }while ()

* for…in 

  循环将遍历对象的所有可枚举属性。不但可以循环遍历数组，还可以循环遍历对象。

```js
for i in arr:
	arr[i]
for i in pers:
	pers[i]
	for j in pers[i]
		pers[j]
```

* foreach(): 遍历数组

  ```js
  let arr = [1,2]
  arr.forEach(function (item,index,array) {
      console.log(item);
      console.log(index);
      array.length
  })
  ```

* for ...of  语句创建一个循环来迭代可迭代的对象。ES6新增的方法，但是缺点是无法遍历自定义普通对象。

  ```js
  for (var of itearale){
      
  }
  ```

##### 跳出循环

* continue： 跳出本次循环,继续执行下次

* break：跳出循环

* return： 结束整个函数并返回

* label 标记

  > 在 [JavaScript](http://c.biancheng.net/js/) 中，使用 label 语句可以为一行语句添加标签，以便在复杂结构中，设置跳转目标。语法格式如下：
  >
  > ​	label : states
  >
  > ```js
  > var num = 0;
  >     outermost:
  >     for (var i = 0; i < 10; i++) {
  >         for (var j = 0; j < 10; j++) {
  >             if (i == 5 && j == 5) {
  >                 continue outermost;
  >                 //break outermost;
  >             }else{
  >                 console.log(i,j,88);
  >             }
  >             num++;
  >         }
  >     }
  >     console.log(num); //95
  > ```
  >

#### 数组

可以存放任意类型

```js
var arr = new Array(); 创建空数组
var arr = []

```

##### 访问元素

索引从开始

```css
arr[i]
error:访问越界的元素会显示
arr[i] = undefined
```

##### 遍历数组

```js
// ES1
for (let i = 0; i < arr.length; i++) {
 	arr[i]   
}
 let arr = [1,2,3];
// ES1 for-in 访问继承属性的实际用途是：遍历对象的所有可枚举属性（自己的和继承的）。
// 作为属性键，数组元素的索引是字符串，而不是数字。
for (const arrKey in arr) {
    console.log(arr[arrKey]);
}
//  [ES6]
for (const number of arr) {
    console.log(number);
}
// 不能在它的循环体中使用 await。
// 不能提前退出 .forEach() 循环。而在 for 循环中可以使用 break。
// 退出使用 return true
arr.forEach(function (item,index) {
    console.log(index);
    console.log(item);
})
for (const [index, elem] of arr.entries()) {
    console.log(index, elem);
}
```

##### 数组方法

```js 
arr.length = 10; 修改js
arr[11] = 10; 如果索引上没有值则追加，原有的会被替换

let arr = [1,2,3];
for (let i = 0; i < arr.length - 1; i++) {
    for (let j = 0; j < arr.length -1 - i; j++) {
        if(arr[j] > arr[j+1] ){
            let t = arr[j];
            arr[j] = arr[j+1];
            arr[j+1] = t;
        }
    }
}
console.log(arr);
```

#### 函数



```js
// 声明式函数定义
function fn（args） {
    return xxx
}
fn（）
// 函数表达式
let fn = function(){}
fn()
// 函数对象方式
var sum = new Function("num1,num2","return num1+num2");
var result1 = sum(120,130); 
alert(result1);
因为这种语法会导致解析两次代码（第一次是解析常规js代码，第二次是解析传入构造函数中的字符串），从而影响性能。

// 匿名函数
(function(){...});
// 自执行函数
  (function(){ ... })()   (function(){ ... }())
  
 var fun1 = new Function (arg1 , arg2 ,arg3 ,…, argN , body  )；Function构造函数所有的参数都是字符串类型。除了最后一个参数, 其余的参数都作为生成函数的参数即形参。这里可以没有参数。最后一个参数, 表示的是要创建函数的函数体。

　　　　总结：1 、第一种和第二种函数的定义的方式其实是第三种new Function 的语法糖，当我们定义函数时候都会通过 new Function 来创建一个函数，只是前两种为我们进行了封装，我们看不见了而已，js 中任意函数都是Function 的实例。2、ECMAScript 定义的 函数实际上是功能完整的对象。
```

* 如果实参多于形参，则多余的实参作废
* 如果实参少于形参，则多余的形参为undefined 
* return 结束函数并返回一个值 ，return v1,v2; 只返回v2
* 如果没有return ，则返回undefined

##### 构造函数

通过 new 函数名  来实例化对象的函数叫构造函数。任何的函数都可以作为构造函数存在。之所以有构造函数与普通函数之分，主要从功能上进行区别的，构造函数的主要 功能为 初始化对象，特点是和new 一起使用。new就是在创建对象，从无到有，构造函数就是在为初始化的对象添加属性和方法。**构造函数定义时首字母大写**（规范）内部使用this绑定属性和方法。会自动返回一个新的对象

```js
function Foo(name,age,sex){
    this.name = name;
    this.age = age;
    this.sex = sex;
}
Foo.prototype.belief = function(){
    console.log('量变是质变的必要准备，质变是量变积累到一定程度的必然结果！');
}
let f = new Foo ('zh',18,'男');
```

1.  `let  f = {};  `一个继承自 `Foo``.prototype` 的新对象被创建。
2.  `  f.__proto__ = Foo.prototype;` f 继承 Foo的原型。  
3.   Foo.call(f,'zh',18,'男');  //执行Foo函数，将name,age,sex 参数传入Foo中执行，此时函数内部this 为 new 创建的 f对象，所以 f.name = 'zh';f.age = 18; f.sex = '男'；
4. 实例化对象完成，此时 f = {　name:'zh',　age:18,　sex:'男'}
5.  f.belief();   打印'量变是质变的必要准备，质变是量变积累到一定程度的必然结果！

##### arguments(内置)

arguments 存了所有实参, 是一个伪数组。 

* 具有数组的长度length,
* 按照索引方式存储
* 没有数组方法pop，push

```js
function fn (){
    console.log(arguments);
}
fn(1,2,3)

Arguments(3)
0: 1
1: 2
2: 3
callee: ƒ fn()
length: 3
Symbol(Symbol.iterator): ƒ values()
[[Prototype]]: Object
```

##### 作用域

限定变量的作用范围。

todo: 

ES6 前：

*  全局（全局生效）  ：只在浏览器关闭后才销毁. 

  1. 所有 window 对象的属性拥有全局作用域
  2. 没有声明直接赋值是全局变量
  3. 最外层函数 和在最外层函数外面定义的变量拥有全局作用域

   污染全局命名空间, 容易引起命名冲突。

  **这就是为何 jQuery、Zepto 等库的源码，所有的代码都会放在`(function(){....})()`中。因为放在里面的所有变量，都不会被外泄和暴露，不会污染到外面，不会对其他的库或者 JS 脚本造成影响。这是函数作用域的一个体现。**

* 局部（在函数内部的起作用）： 函数执行完毕就销毁

* ES6 块级作用域{}：

  块级作用域可通过新增命令 let 和 const 声明，所声明的变量在指定块的作用域外无法被访问。块级作用域在如下情况被创建：

  1. 在一个函数内部
  2. 在一个代码块（由一对花括号包裹）内部
  3. 声明变量不会提升到代码块顶部
  4. 禁止重复声明
  5. 循环中的绑定块作用域的妙用

  ```js
  <button>测试1</button>
  <button>测试2</button>
  <button>测试3</button>
  <script type="text/javascript">
     var btns = document.getElementsByTagName('button')
      for (var i = 0; i < btns.length; i++) {
        btns[i].onclick = function () {
          console.log('第' + (i + 1) + '个')
        }
      }
  </script>
  我们要实现这样的一个需求: 点击某个按钮, 提示"点击的是第 n 个按钮",此处我们先不考虑事件代理,万万没想到，点击任意一个按钮，后台都是弹出“第四个”,这是因为 i 是全局变量,执行到点击事件时，此时 i 的值为 3。那该如何修改，最简单的是用 let 声明 i
  ```


作用域链：

内部函数访问外部函数变量，用链式查找决定数据，就近原则。 一层层的查找

**作用域与执行上下文**

许多开发人员经常混淆作用域和执行上下文的概念，误认为它们是相同的概念，但事实并非如此。

我们知道 JavaScript 属于解释型语言，JavaScript 的执行分为：解释和执行两个阶段,这两个阶段所做的事并不一样：

**解释阶段：**

- 词法分析
- 语法分析
- 作用域规则确定

**执行阶段：**

- 创建执行上下文
- 执行函数代码
- 垃圾回收

JavaScript 解释阶段便会确定作用域规则，因此作用域在函数定义时就已经确定了，而不是在函数调用时确定，但是执行上下文是函数执行之前创建的。执行上下文最明显的就是 this 的指向是执行时确定的。而作用域访问的变量是编写代码的结构确定的。

作用域和执行上下文之间最大的区别是： **执行上下文在运行时确定，随时可能改变；作用域在定义时就确定，并且不会改变**。

一个作用域下可能包含若干个上下文环境。有可能从来没有过上下文环境（函数从来就没有被调用过）；有可能有过，现在函数被调用完毕后，上下文环境被销毁了；有可能同时存在一个或多个（闭包）。**同一个作用域下，不同的调用会产生不同的执行上下文环境，继而产生不同的变量的值**。

- 

##### js预解析

```js
//报错
console.log(num); 

console.log(num); //undefined
var num = 10;

// 没问题
fn();
function fn(){
    console.log(11);
}
// 报错
fn()
let fn = function () {

}
```

js执行：会先 预解析， 在执行代码

* 预解析： 将var 和function 提升到当前作用域的最前面

  变量提升：所有变量声明提升当前作用域的最前面

  函数提升：所有函数声明提升当前作用域的最前面

  **函数是一等公民，优先编译函数**

  ```js1
  console.log(a); //function a(){}
  var a = 10;
  function a(){
  }
  console.log(a); //10
  
  实际执行
  function a(){
  }
  console.log(a);
  a = 10;
  console.log(a);
  ```

  

* 接着代码按照书写顺序执行

```js
var num = 10;
fn();
function fn(){
    console.log(num); //undefined
    var num = 20;
}

let a = b = c = 9 // var a =9;b=9;c=9;  集体声明 var a =9,b=9,c=9；

```

#### 对象

一组无序的相关方法 和 方法的集合

ECMAScript ： 自定义对象， 内置对象，

 JS API： 浏览器对象

##### 创建对象的方式

1. 字面值创建

```js
let person = {name:'jone',
              age:19,
              // 方法
              talk:function(){
				console.log(age)
              }
             }
person['age']
```

2. new  Object()

```js
var person = new Object();
    person.name = "lisi";
    person.age = 21;
    person.family = ["lida","lier","wangwu"];
    person.say = function(){
        alert(this.name);
    }
```

3. 工厂方法  同一接口创建多个对象时，会产生大量重复代码，为了解决此问题，工厂模式被开发。

```js
function createPerson(name,age,family) {
    var o = new Object();
    o.name = name;
    o.age = age;
    o.family = family;
    o.say = function(){
        alert(this.name);
    }
    return o;
}

//instanceof无法判断它是谁的实例，只能判断他是对象，构造函数都可以判断出
var person =  createPerson("wangwu",18,["lida","lier","lisi"]);
console.log(person1 instanceof Object);//true
```

工厂模式解决了重复实例化多个对象的问题，但没有解决对象识别的问题（但是工厂模式却无从识别对象的类型，因为全部都是Object，不像Date、Array等，本例中，得到的都是o对象，对象的类型都是Object，因此出现了构造函数模式）

4. 构造函数模式
   * 构造函数名字首字母大写
   * 不需要return 就能返回新创建的对象
   * 调用构造函数必须配合new
   * 属性和方法绑定在this

```js
function Person(name,age,family) {
    this.name = name;
    this.age = age;
    this.family = family;
    this.say = function(){
        alert(this.name);
    }
}
var person1 = new Person("lisi",21,["lida","lier","wangwu"]);
console.log(person1 instanceof Object); //true
console.log(person1 instanceof Person); //true
econsole.log(person1.constructor);      //constructor 属性返回对创建此对象的数组、函数的引用
```

对比工厂模式有以下不同之处：

1、没有显式地创建对象

2、直接将属性和方法赋给了 this 对象

3、没有 return 语句

new 调用构造函数步骤 {

1、在内存中创建一个空对象

2、将构造函数的作用域赋给新对象（将this指向这个新对象）

3、执行构造函数代码（为这个新对象添加属性和方法）

4、返回新对象 ( 指针赋给变量person ？？？ )

可以看出，构造函数知道自己从哪里来（通过 instanceof 可以看出其既是Object的实例，又是Person的实例）

**构造函数也有其缺陷**，每个实例都包含不同的Function实例（ 构造函数内的方法在做同一件事，但是实例化后却产生了不同的对象，方法是函数 ，函数也是对象）详情见构造函数详解

因此产生了原型模式

5. 原型

   ```js
   function Person() {
   }
   
   Person.prototype.name = "lisi";
   Person.prototype.age = 21;
   Person.prototype.family = ["lida","lier","wangwu"];
   Person.prototype.say = function(){
       alert(this.name);
   };
   console.log(Person.prototype);   //Object{name: 'lisi', age: 21, family: Array[3]}
   
   var person1 = new Person();        //创建一个实例person1
   console.log(person1.name);        //lisi
   
   var person2 = new Person();        //创建实例person2
   person2.name = "wangwu";
   person2.family = ["lida","lier","lisi"];
   console.log(person2);            //Person {name: "wangwu", family: Array[3]}
   // console.log(person2.prototype.name);         //报错
   console.log(person2.age);              //21
   ```

   构造函数模式用于定义实例属性，原型模式用于定义方法和共享的属性

6. 混合模式 构造函数 + 原型

   ```js
   function Person(name,age,family){
       this.name = name;
       this.age = age;
       this.family = family;
   }
   
   Person.prototype = {
       constructor: Person,  //每个函数都有prototype属性，指向该函数原型对象，原型对象都有constructor属性，这是一个指向prototype属性所在函数的指针
       say: function(){
           alert(this.name);
       }
   }
   
   var person1 = new Person("lisi",21,["lida","lier","wangwu"]);
   console.log(person1);
   var person2 = new Person("wangwu",21,["lida","lier","lisi"]);
   console.log(person2);
   ```

   

   混合模式共享着对相同方法的引用，又保证了每个实例有自己的私有属性。最大限度的节省了内存

7. 寄生          没什么用的

8. 稳妥寄生

##### 调用

```js
person['age']
person.age = 21;
person.say()
```

##### 遍历对象

```js

for (var attr in obj){
    obj[attr]
}
```

```js
Object.keys(obj).forEach(function(key){
     console.log(key,obj[key]);
});
```

```js
// 返回一个数组，包含对象自身的所有属性（包含不可枚举属性）
const obj = {
    id:1,
    name:'zhangsan',
    age:18
    }
Object.getOwnPropertyNames(obj).forEach(function(key){
    console.log(key+ '---'+obj[key])
})
```

##### 内置对象

文档：[MDN](https://developer.mozilla.org/zh-CN/)

###### Math

**`Math`** 是一个内置对象，它拥有一些数学常数属性和数学函数方法。`Math` 不是一个函数对象。`Math` 用于 [`Number`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number) 类型。它不支持 [`BigInt`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/BigInt)。

​      与其他全局对象不同的是，`Math` 不是一个构造器。`Math` 的所有属性与方法都是静态的。引用圆周率的写法是 `Math.PI`，调用正余弦函数的写法是 `Math.sin(x)`，`x` 是要传入的参数。`Math` 的常量是使用 JavaScript 中的全精度浮点数来定义的。

```js
let mMath = {
    PI:Math.PI,
    max: function () {
        let maximum = arguments[0];
        for (let i = 0; i < arguments.length; i++) {
            if (arguments[i] > maximum){
                maximum = arguments[i];
            }
        }
        return this.max;
    }
}
```

`Math.abs('-1') = 1` : 取绝对值

`Math.ceil()`向上取整

`Math.floor()` 向下取整

`Math.round()`：四舍五入取整；- 1.5 = -1， 1.5 = 2. ;  .5 是看谁大取谁

`Math.random()`:函数返回一个浮点数,  伪随机数在范围从**0到**小于**1** [0, 1]

`*不能*提供像密码一样安全的随机数字。不要使用它们来处理有关安全的事情。使用Web Crypto API 来代替, 和更精确的[`window.crypto.getRandomValues()`](https://developer.mozilla.org/zh-CN/docs/Web/API/Crypto/getRandomValues) 方法.

```js
// 得到一个两数之间的随机数 [min, max]
function getRandomArbitrary(min, max) {
  return Math.random() * (max - min + 1) + min;
}
```

###### Date

创建一个新`Date`对象的唯一方法是通过[`new`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/new) 操作符，例如：`let now = new Date();`
若将它作为常规函数调用（即不加 [`new`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/new) 操作符），将返回一个字符串，而非 `Date` 对象

```js
dateString : 
const date1 = new Date('December 17, 1995 03:24:00');
const date2 = new Date('1995-12-17T03:24:00')
const date = new Date(1995,10, 5) // 返回 1995 11 5

let arr = ['星期日','星期一','星期二','星期三','星期四','星期五','星期六']
// 09：01:02
let time = new Date();
let h = time.getHours();
h = h < 10 ? '0' + h:h;
let m = time.getMinutes();
m = m < 10 ? '0' + m:m;
let s = time.getSeconds();
s = s < 10 ? '0' + s:s;
let result = h + ':' + m + ':' + s;
console.log(result);
```

表示日期的字符串值。该字符串应该能被 [`Date.parse()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/parse) 正确方法识别（即符合 [IETF-compliant RFC 2822 timestamps](https://tools.ietf.org/html/rfc2822#page-14) 或 [version of ISO8601](https://www.ecma-international.org/ecma-262/5.1/#sec-15.9.1.15)）。

**注意:** 由于浏览器之间的差异与不一致性，强烈不推荐使用`Date`构造函数来解析日期字符串 (或使用与其等价的`Date.parse`)。对 RFC 2822 格式的日期仅有约定俗成的支持。 对 ISO 8601 格式的支持中，仅有日期的串 (例如 "1970-01-01") 会被处理为 UTC 而不是本地时间，与其他格式的串的处理不同

时间戳：

```js
// 方式一
let time = new Date();
time.getTime()
// 方式二
time.valueOf()
//方式三
let times = +new Date();
// 方式四：h5新增方法
Date.now()

function countDown(time) {
    let now = +new Date();
    let older = +new Date(time);
    let times = (now - older) / 1000;
    let days = parseInt(times /60 /60 / 24);
    let hours = parseInt(times /60 /60 % 24);
    let minutes = parseInt(times /60 % 60 );
    let seconds = parseInt(times % 60 );
    return days + '天' + hours + '时' + minutes + '分' + seconds + '秒';
}

```

###### Array

```js
let arr = new Array(2);
let arr1 = new Array(2,3);
let arr2 = [2,3];
```

判断数组类型

```js
Array.isArray(arr)
```

```js
// H5新增的， iE9
arr instanceof Array
```

增删查改

```js
arr.push([x,x]): 在数组末尾添加，返回length
arr.pop(): 删除数组末尾最后有一个元素，返回删除的元素
arr.unShift(): 在数组前添加，返回length
arr.shift()：删除数组第一个元素，返回删除的元素
```

转换为字符串：

```js
arr.tostring()
arr.join(',')
```

*v8底层实现*

JS的数组可以存放不同的数据类型，是key-value的存储形式。

数组的两种方式： 

**fast ：**

快速的后备存储结构是 FixedArray ，并且数组长度 <= elements.length();

快数组是一种线性的存储方式。新创建的空数组，默认的存储方式是快数组，快数组长度是可变的，可以根据元素的增加和删除来动态调整存储空间大小，内部是通过扩容和收缩机制实现，

**新容量的的计算方式**：new_capacity = old_capacity /2 + old_capacity + 16

**如果容量 >= length的2倍 + 16，** 则进行收缩容量调整，否则用holes对象（什么是holes对象？下面来解释）填充未被初始化的位置。

holes （空洞）对象指的是数组中分配了空间，但是没有存放元素的位置。对于holes，快数组中有个专门的模式，在 Fast Elements 模式中有一个扩展，是**Fast Holey Elements**模式。

Fast Holey Elements 模式适合于数组中的 holes （空洞）情况，即只有某些索引存有数据，而其他的索引都没有赋值的情况。

那什么时候会是Fast Holey Elements 模式呢？

当数组中有空洞，没有赋值的数组索引将会存储一个特殊的值，这样在访问这些位置时就可以得到 undefined。这种情况下就会是 Fast Holey Elements 模式。

Fast Holey Elements 模式与Fast Elements 模式一样，会动态分配连续的存储空间，分配空间的大小由最大的索引值决定。

新建数组时，如果没有设置容量，V8会默认使用 Fast Elements 模式实现。

如果要对数组设置容量，但并没有进行内部元素的初始化，例如let a = new Array(10);，这样的话数组内部就存在了空洞，就会以Fast Holey Elements 模式实现。

1. **存储方式方面：**快数组内存中是连续的，慢数组在内存中是零散分配的。
2. **内存使用方面：**由于快数组内存是连续的，可能需要开辟一大块供其使用，其中还可能有很多空洞，是比较费内存的。慢数组不会有空洞的情况，且都是零散的内存，比较节省内存空间。
3. **遍历效率方面：**快数组由于是空间连续的，遍历速度很快，而慢数组每次都要寻找 key 的位置，遍历效率会差一些。

**slow ：**

缓慢的后备存储结构是一个以数字为键的 HashTable 

######  string

包装类：为基本数据类型添加方法和属性。String(), Number,Boolean()

字符串不可变：

查找字符串出现的位置： indexOf(x, startPosition): 没有结果返回-1

lastIndexOf(x)

```js
输入char 统计char出现的位置
function reverse(char, str) {
    let index = str.indexOf(char);
    while (~index){
        console.log(index);
        index = str.indexOf(char, index + 1);
    }
}
```

返回字符：

```js
charAt(index) //: 返回字符
charCodeAt(index)// 判断用户按下那个键
// H5新增的
str[index ] 返回字符 
```

```js
function reverse(str) {
    let obj = {};
    let i = 0;
    while(i < str.length){
        let c = str.charAt(i);
        if (obj[c]){
            obj[c] ++;
        }else {
            obj[c] = 1;
        }
        i ++;
    }
    let max = 0;
    let ch = ''
    for (const objKey in obj) {
        if (obj[objKey] > max){
            max = obj[objKey];
            ch = objkey
        }
    }
    return max;
}
```

字符串操作：

* concat([str,str1...]):
* substr(start,  length) 从start开始去length个
* slice(start, end)： 取子串
* substring(start, end) 取子串，不接受负值
* 替换字符： replace（被替换的字符, 替换为的字符）只替换第一个： 敏感词屏蔽
* split(‘ ,’ ) : 将字符串分割为数组

## Web API

浏览器提供的一套操作**浏览器功能**(BOM)和**页面元素**的API(DOM)

注意获取元素，页面加载是从上往下执行的，script放在body后

### DOM

W3C:推荐的文档对象模型，标准编程接口。

#### DOM树

* 文档：页面，document

* 元素：标签 element

* 节点： 所有内容（标签、属性、文本、注释）nodeType,nodeName. nodeValue

  

##### 获取元素

1. 返回一个匹配到 ID 的 DOM [`Element`](https://developer.mozilla.org/zh-CN/docs/Web/API/Element) 对象。若在当前 [`Document`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document) 下没有找到，则返回 null。

* ```js
  document.getElementById('test')
  ```

2. 返回一个包括所有给定标签名称的元素的HTML集合[`HTMLCollection`](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCollection)。 整个文件结构都会被搜索，包括根节点。返回的 `HTML集合`是**动态**的, 意味着它可以自动更新自己来保持和 DOM 树的同步而不用再次调用 `document.getElementsByTagName()` 。

   ```js
   let list = document.getElementsByTagName('div');
   for (const listElement of list) {
       console.log(listElement);
   }
   // element.getElementsByTagName
   let id = document.getElementById('test');
   let di = id.getElementsByTagName('div');
   ```

3. HTML5 新增方法，包含了所有指定类名的子元素的类数组对象

   ```
   let elements = document.getElementsByClassName('node');
   ```

4. HTML5 新增方法，文档对象模型[`Document`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document)引用的`**querySelector()**`方法返回文档中与指定选择器或选择器组匹配的第一个 [`HTMLElement`](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLElement)对象。 如果找不到匹配项，则返回`null`。**深度优先**

   ```js
   document.querySelector('div');
   document.querySelector('#test');
   // 获取所有
   document.querySelectorAll('div');
   ```

5. 特殊元素获取

   * html

     ```js
     document.documentElement
     ```

   * body

     ```js
     document.body
     ```

##### 获取属性

* element.属性： 内置属性
* element.getAttribute(‘属性’)： 可读取自定义的属性

##### 设置属性值

* element.属性 = ‘’
* element.setAttribute(' class'， ‘bg’)

##### 移除属性

```
delete element.lang;
element.removeAttribute('lang')
```

jd 切换tab

```js
 <style>
        * {
            margin: 0;
            padding: 0;
        }
        .tab {
            width: 500px;
            margin: 100px auto;

        }
        .tab_list {
            background-color: #cccccc;
        }
        ul {

            height: 30px;
            list-style: none;
        }
       .tab_list li{
           float: left;
           height: 30px;
           line-height: 30px;
           padding: 0 20px;
           text-align:center;
           cursor: pointer;
       }
       .tab_list .current{
           background-color: #c81623;
           color: #fff;
       }
       .item_info {
           padding: 20px 0 0 20px;
       }
       .item {
           display: none;
       }
   
    </style>

 <div class="tab">
        <div class="tab_list">
            <ul>
                <li class="current" style="display: block">介绍</li>
                <li>包装</li>
                <li>保障</li>
                <li>评价</li>
                <li>社区</li>
            </ul>
        </div>
        <div class="tab_con">
            <div class="item">1</div>
            <div class="item">2</div>
            <div class="item">3</div>
            <div class="item">4</div>
            <div class="item">5</div>
        </div>
    </div>

<script>
    let tabs = document.querySelector('.tab_list').querySelectorAll('li');
    let content = document.querySelector('.tab_con')
    let contents = content.querySelectorAll('div');

    let i = 0;
    for (const tab of tabs) {
        tab.setAttribute('index', i);
        // 上部tab
        tab.onclick = function () {
            // 清除class
            for (const t of tabs) {
                t.className = '';
            }
            this.className = 'current'
            // 切换content
            let index = this.getAttribute('index');
            for (const con of contents) {
                con.style.display = 'none';
            }
            contents[index].style.display = 'block';
        }
        i ++;
    }
</script>
```



#### 事件

事件源： 事件的对象

事件类型： 事件如何触发

事件处理： 触发后的处理

```js
let element = document.querySelector('#button');
element.onclick = function(){
    alert('触发 ')
}
window.onload 全局加载
```

##### *事件的类型：*

依赖于设备的输入事件，如：mousedown，mouseover等。

独立于设备的输入事件，如：尚未广泛实现 textinput事件就是一个独立于设备的输入事件，他既可以取代按键事件并支持键盘的输入，也可以替代剪切和黏贴与手写识别事件。

用户界面事件，通常是比价高级的事件，通常出现在定义问问吧应用用户界面的HTNL表的元素上，如;

focus，change事件。

状态变化事件，如：loadstart，progress等。

特定API事件，如：dragstart，dragenter等。

计时器和错误处理程序事件。如timer和error hangdler。

传统事件类型

表单事件：submit，reset，click，change，focus，blur。

Window事件：unload，load，beforeload，beforeunload，resize，scroll。

鼠标事件：click，mousedown，mouseover，mousemove，mouseup，

键盘事件：keypress，keydown，keyup。

DOM事件：

3级DOM事件规范标准化了不冒泡的focusein和focuseout事件来取代冒泡的focusheblur事件，标准化了冒泡的mouseenter和mouseleave事件来取代不冒泡的mouseover和mouseout事件。

HTML5事件

html5定义了大量的新的web应用API，如：<audio>和<video>元素。

触摸屏和移动设备事件

***注册事件处理程序\***

##### 注册事件

* onXxx同一个元素同一时间只能注册同一个事件。后面注册的事件会将前面的覆盖。

* addEventListener 同一个元素同一个事件可注册多个监听器 tr.addEventListener('click', function () {}, capture)

* attachEvent（‘onclick ’, function()） :IE9 支持

   兼容方案

```js
function addEventListener(element,eventName,fn) {
    if(element.addEventListener){
        element.addEventListener(eventName,fn);
    }else if (element.attachEvent){
        element.attachEvent('on'+eventName, fn );
    }else {
        element['on'+ eventName] = fn
    }
}
```

##### 解绑事件

```js
element.onclick = function(){
    alert('触发 ')
    // 解绑事件
    element.onclick = null;
}

// 移除监听
function fn() {

   }
element.addEventListener('click', fn)
element.removeEventListener('click',fn )


// 但是在IE5之后定义了类似的方法attachEvent()和detachEvent()
 b.onclick = function () {
     this.detachEvent('mouseover', ChangeColor);
     alert('click me');
 };
```

##### 事件流

事件流描述事件从页面中接收事件的顺序

先由document捕获事件依次向下传递给 targetElement 事件监听器 ， 再由targetElement  冒泡事件向上传递。如果某一层级监听该事件会被执行

Js代码只能执行捕获或者冒泡的一个阶段， onclick 和 attacheEvent只能得到冒泡阶段

element.addEventListener('click', fn， capture):  capture= true 代表对捕获阶段进行监听

element.addEventListener('click', fn， capture):  capture= false 代表对冒泡阶段进行监听

**没有冒泡的事件** `

> ## scroll
>
> 1 .不会冒泡.无法取消,stopPropagation,preventDefault都无法阻止scroll事件
>  2 .取消事件的唯一就是停止触发,阻止滚轮事件,touchstart事件
>  3 .所以scroll事件必须在捕获阶段就处理完
>
> ## blur,focus
>
> 1 .无法冒泡,无法取消
>  2 .focusIn,focusout是可以冒泡
>
> ## media事件
>
> 1 .媒体事件,视频,图片,音频
>  2 .onpause,onplay.onplaying,onpaused
>  3 .以上都不行
>
> ## mouseleave,mouseenter
>
> 1 .不会冒泡
>  2 .mouseout,mouseover会冒泡

##### 事件对象 Event

它被自动传递给事件处理函数，以提供额外的功能和信息。

```js
function fn(e) {
    // 兼容写法 ie window.event
	if(e = e || window.event){
        // this 返回的是绑定事件的对象 ul绑定了事件
        // e.target 返回触发事件的对象 li触发事件
    }
}
element.addEventListener('click', fn)
```

IE6,8

```js
e.srcElemt
e.returnValue 
e.returnValue 
```



#####  [阻止默认行为](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Building_blocks/Events#阻止默认行为)

```js
e.preventDefault() dom推荐
e.returnValue ie678
retrun false; 没有兼容问题
```

##### 阻断冒泡

```js
 `e.stopPropagation();`//这个函数的作用是阻止事件进一步冒泡，进而被其他节点接收。
 `event.stopImmediatePropagation()`
　　　　　　这个函数用于阻断同一element的事件传播。 例如一个element上定义了多个listener，如果其中一个调用这个方法后面的listener则都不会执行。
  e.returnValue= true // ie678

```

##### 事件委托

给父节点设置监听器，利用冒泡原理影响每个子节点 

```js
<ul class="box">
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
    </ul>

let ul = document.querySelector('ul');
   ul.addEventListener('click', function (e){
       alert(e.target.innerHTML);
   })
```

案例： 禁用右键菜单

```js
document.addEventListener('contextmenu', function (e) {
    e.preventDefault();
})
```

不能选中文字

```js
document.addEventListener('selectstart', function (e) {
       e.preventDefault();
   })
```

##### 鼠标事件

[图解Js event对象offsetX, clientX, pageX, screenX, layerX, x区别 - jiangxiaobo - 博客园 (cnblogs.com)](https://www.cnblogs.com/jiangxiaobo/p/6593584.html)

* `clientX`: 鼠标相对浏览器可视化区域的坐标， 滚动没有影响坐标

* `pageX` :  鼠标相对于文档页面的坐标， 滚动影响坐标 IE9
* `screenX`: 鼠标相对于电脑屏幕的坐标

```js
<img src="images/point-w650.jfif" alt="">
img {
    position: absolute;
    width: 38px;
    height: 38px;
}
<script>
    let img = document.querySelector('img')
    document.addEventListener('mousemove', function (e) {
        let x = e.pageX;
        let y = e.pageY;
        img.style.left = x - 19 + 'px';
        img.style.top = y - 19 + 'px';
    })
</script>
```

##### 键盘事件 KeyboardEvent

* keyup; 松开触发
* keydown: 按下一直触发
* keypress:  按下一直触发 不识别功能键 ctrl + shift + 箭头 +insert等

执行顺序 `down , press, up .`, 可以获取keyCode 

***注意***: `keydown  keyup`都不区分大小写。`keydown` 可识别f1。。。。。up不能。 注意在表单输入时，文字还没写入就会执行keydown'，keypress

`keypress` : 区分大小写

当按下 shift 键时，首先触发 `keydown (en-US)` 事件，然后将 `key` 属性的值设为 `"Shift"` 字符串。如果继续长按 shift 键，由于不会生成字符按键值，`keydown (en-US)` 事件不会继续重复触发。

```js
e.key: A, a ctrl  shift
e.code：兼容 格式KeyS,CtrlLeft,shiftleftM KeyA
e.keycode: 弃用
```

也可通过Xxxkey判断功能键

**mouseover**: 鼠标经过子元素也会触发事件，触发两次

**mouseenter**: 鼠标经过子元素不会触发事件， 该事件不会冒泡（搭配mouseleave）

#### 操作元素

##### 修改文本

```js
let element = document.querySelector('#button');
let test = document.querySelector('#test');
element.onclick = function(){
   test.innerText = 'this is gal';
}

```

```js
// w3c 推荐 可显示标签。 可读取信息; 显示html信息，保留空格换行
test.innerHTML = 'this is gal';
// 无法识别标签 IE发起的。获得去除空格或换行的纯文本信息
test.innerText = '</br>this is gal';
// 获取表单具有value属性的value值 注意button通过innderHTMLx修改
test.value 
// 将指定的文本解析为 Element 元素，将结果节点插入到DOM树中的指定位置
element.insertAdjacentHTML
```

##### 操作元素的属性

```js
img.src
img.title
```

##### 表单属性

type、value、checked、selected、disabled

```js
let test = document.querySelector('#button');
let text = document.getElementById('text');
test.onclick = function(){
   text.value = 'this is gal';
   // this指向调用者 禁用属性
   this.disabled = true;
}
```

京东密码框

```js
<!doctype html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <!--以ie浏览器的最高版本内核渲染页面-->
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <style>
       .box {
           position: relative;
           width: 400px;
           border-bottom: 1px solid #2aabd2;
           margin: 100px auto;

       }
       .box input {
           width: 370px;
           height: 30px;
           border: 0;
           outline:none;

       }
       .box img {
           position: absolute;
           right: 2px;
           top: 2px;
           width:24px;
       }
    </style>

    <title></title>
</head>
<body>
   <div class="box">
       <label for="password">
           <img src="images/colseEye.png" alt="" id="eye">
       </label>
       <input type="password" id="password" >
   </div>
</body>
<script>
    let password = document.querySelector('#password');
    let eye = document.getElementById('eye');
    let flag = 0;
    eye.onclick = function(){
        if(!flag){
            password.type = 'text';
            eye.src = 'images/openEye.png';
            flag = 1;
            return;
        }
        password.type = 'password';
        eye.src = 'images/colseEye.png';
        flag = 0;
    }
</script>
</html>
```

##### js 操作样式

* 通过行内样式修改样式， 权重较高。追加行内样式

```js
element.style.样式 = ''
```

关闭二维码

```js
    <style>
       .box {
           position: relative;
           width: 70px;
           border: 1px solid #ccc;
           margin: 100px auto;
           font-size:12px;
           text-align: center;
           color: red;
       }
       .box img {
           width: 60px;
           margin-top: 5px;
       }
       .close-btn {
           position: absolute;
           top: -1px;
           left:-16px;
           width: 14px;
           height: 14px;
           border-top: 1px solid #ccc;
           line-height: 14px;
           font-family: Arial, Helvetica, sans-serif;
           cursor: pointer;
       }
    </style>

    <title></title>
</head>
<body>
   <div class="box">
       <img src="images/qrcode.png" alt="" id="eye">
       <i class="close-btn">x</i>
   </div>
</body>
<script>
    let btn = document.querySelector('.close-btn');
    let box = document.querySelector('.box')
    btn.onclick = function(){
        box.style.display = 'none';
    }
</script>
```

新事件： onfocus, onblur

京东搜索框

```js
<style>
    input {
        color: #999;
    }
</style>
<div class="box">
       <input type="text" name="" id="text" value="iphone">
 </div>
let text = document.querySelector('#text')
text.onfocus = function(){
    if(this.value=== 'iphone'){
        this.value = '';
    }
    this.style.color = '#333';
}
text.onblur = function () {
    if(!this.value){
        this.value = 'iphone';
    }
    this.style.color = '#999';
}
```

2. 通过内嵌样式修改. 适合样式较多。但注意会覆盖原有的样式。如果想保留 必须使用并集

```js
.change {}
element.className = 'first change';
```

多个元素添加事件，循环获取每个元素并绑定事件。先清除其他人的样式，添加自己的样式

表格隔行变色

**onMouseOver**, **onmouseleave**

```js
let text = document.querySelector('tbody').querySelectorAll('tr');
    for (const element of text) {
        element.onmouseover = function () {
                this.className = 'bgc';   
        }
        element.onmouseleave = function () {        
                this.className = '';
        }
    }
```

表单全选，不全选取消

```js
let checkAll = document.querySelector('checkAll');
let check_list = document.getElementsByTagName('input');
// 大全选控制所有
checkAll.onclick = function () {
    for (const check of check_list) {
        check.checked = this.checked;
    }
}
// 下面全选、上面选中.下面不全选，上面不选
for (const element of check_list) {
    element.onclick = function () {
        let flag = true;
        for (const element of check_list){
            if(!element.checked){
                flag = false;
                break;
            }
        }
        checkAll.checked = flag;
    }
}
```

#### 自定义数据

用来保存简单的页面数据。 但`getAttribute`不容易区分自定义和内置属性。H5规定自定义属性应该以data-开头

如： data-last-name = “lion”;

获取数据：

* ```js
  getAttribute("data-last-name")
  ```

* ```js
  // 只能获取data-开头的数据，IE11才行
  this.dataset.lastName
  ```

* ```js
  this.dataset['lastName']
  ```

#### 节点操作

* 元素节点，nodeType = 1  nodeValue = ‘null’， nodeName= ‘element’
* 属性节点，nodeType = 2  
* 文本节点（文字、空格、换行 注释），nodeType = 3， nodeValue = ‘文本信息’， nodeName= ‘#text’
* 注释节点，

##### 层级关系

* 父节点操作

```js
`element.parentNode` ： 获取元素的亲父亲节点
```

* 子节点

```js
`childNodes`: 可获取所有节点（包含元素和文本节点） 
`children` :获取子元素节点 实际开发常用

`firstChild`: 获取第一个子节点（元素和文本）
`lastChild`: 获取最后一个子节点（元素和文本）
// IE9 以上才支持
`firstElementChild`: 返回第一个元素子节点
`lastElementChild`: 返回最后一个元素子节点

// 实际开发
`element.childrem[0]`: 第一个元素子节点
`element.childrem[element.childrem.length - 1]` 最后一个元素子节点
```

* 兄弟节点

```js
`element.nextSibling`    获取后面的所有兄弟节点（元素和文本）
`element.previousSibling`获取前面的所有兄弟节点（元素和文本）
// 存在兼容问题IE9
`element.previousElementSibling`获取前面的所有兄弟元素节点
`element.nextElementSibling`获取后面的所有兄弟节点（元素和文本）
// 自定义兼容函数
function getNextElementSibling(element) {
       var el = element;
       while (el = el.nextSibling){
           if (el.nodeType === 1){
               return el;
           }
       }
       return null
   }
```

* 创建节点

```js
let element = document.createElement('div');
element.innderHtml = ''： 多个元素拼接字符串比较耗时耗内存（数组。join(标签) 比较快）
document.write (): 文本中写入标签。 当文本流执行完毕，执行write页面会重绘。原先的内容被覆盖。
```

* 添加元素

```js
 // 在元素的子元素后面追加元素
   element.appendChild(element);
// 把 element ， 添加在第一个元素之前
   document.body.insertBefore(element, document.body.children[0])
```

* 删除节点

```js
element.removeChild(ul.children[0]);
```

* 复制节点

```js
// 空参是浅拷贝，只复制标签不拷贝节点的内容
let newNode = element.cloneNode();
// 深拷贝
let newNode = element.cloneNode(true);
element.appendChild(element);
```

案例

```js
<!doctype html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <!--以ie浏览器的最高版本内核渲染页面-->
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        ul {
            height: 30px;
            list-style: none;
        }
        a {
            text-decoration: none;
        }
        table {
            width: 500px;
            margin: 100px auto;
            border-collapse: collapse;
            text-align: center;
        }
        td,th {
            border:1px solid #333;
        }
        thead tr {
            height: 40px;
            background-color: #ccc;
        }


    </style>

    <title></title>
</head>
<body>
    <table cellspacing="0">
        <thead>
            <tr>
                <th>name</th>
                <th>subject</th>
                <th>score</th>
                <th>options</th>
            </tr>
        </thead>
        <tbody>
           <tr>
               <td>andy</td>
               <td>two</td>
               <td>1.0</td>
               <td><a href="#">删除</a></td>
           </tr>
        </tbody>
        
    </table>
</body>
<script>
   let data = [
       {
           name: 'wq',
           subject: 'JS',
           score: 20,
       },
       {
           name: 'kele',
           subject: 'JD',
           score: 10,
       }
   ]
   let tbody = document.querySelector('tbody');
   for (let i = 0; i < data.length; i++) {
       let tr = document.createElement('tr');
       tbody.appendChild(tr);
       for (const attr in data[i]) {
           let td = document.createElement('td');
           td.innerHTML = data[i][attr];
           tr.appendChild(td)
       }
       let td = document.createElement('td');
       td.innerHTML = '<a href="#">删除</a>';
       tr.appendChild(td);
   }
   // 删除
   let as = document.getElementsByTagName('a');
   for (const a of as) {
       a.onclick = function () {
           let parentNode = this.parentNode.parentNode;
           let result = tbody.removeChild(parentNode)
           console.log(result)
       }
   }
</script>
</html>
```

### BOM

浏览器对象： 浏览器私有实现的对象，有严重的兼容问题。实现浏览器的功能

* Global:

​     Global对象是单体内置对象，即不依赖于宿主环境的对象，这些对象在ECMAScript程序执行之前就已经存在了，就是一切全局里存在的变量和函数都是它的属性和方法，即“终极老祖宗”。也就是那些在宿主环境（常见的宿主环境：浏览器和nodejs）里所有的内建或自定义的变量和函数全局都是Global这个的全局对象和方法。它更像是一个抽象概念，而要指明它是什么，取决于程序在什么环境中运行。（例如：js不仅可以书写页面，在书写页面中，global相对于浏览器这个环境而言就是window，但是其他环境就不一定。

​     window对象是相对于Web浏览器而言的，它并不是ECMAScript规定的内置对象，它是浏览器的Web API,是存在于浏览器之中的，也就是离开浏览器这个宿主环境的话就不存在此对象了。所以说Global对象是包含于window对象这种情况的。

* window

window 是客户端浏览器对象模型的基类，window 对象是客户端 [JavaScript](http://c.biancheng.net/js/) 的全局对象。一个 window 对象实际上就是一个独立的窗口，对于框架页面来说，浏览器窗口每个框架都包含一个 window 对象。所有的全局变量都被解析为该对象的属性。

- window：客户端 JavaScript 顶层对象。每当 <body> 或 <frameset> 标签出现时，window 对象就会被自动创建。
- navigator：包含客户端有关浏览器信息。
- screen：包含客户端屏幕的信息。
- history：包含浏览器窗口访问过的 URL 信息。
- location：包含当前网页文档的 URL 信息。
- document：包含整个 HTML 文档，可被用来访问文档内容及其所有页面元素。

#### 使用系统对话框

window 对象定义了 3 个人机交互的方法，主要方便对 JavaScript 代码进行调试。

- alert()：确定提示框。由浏览器向用户弹出提示性信息。该方法包含一个可选的提示信息参数。如果没有指定参数，则弹出一个空的对话框。
- confirm()：选择提示框。。由浏览器向用户弹出提示性信息，弹出的对话框中包含两个按钮，分别表示“确定”和“取消”按钮。如果点击“确定”按钮，则该方法将返回 true；单击“取消”按钮，则返回 false。confirm() 方法也包含一个可选的提示信息参数，如果没有指定参数，则弹出一个空的对话框。
- prompt()：输入提示框。可以接收用户输入的信息，并返回输入的信息。prompt() 方法也包含一个可选的提示信息参数，如果没有指定参数，则弹出一个没有提示信息的输入文本对话框。

```js
window.open (URL, name, features, replace)
win.close();
使用 window.closed 属性可以检测当前窗口是否关闭，如果关闭则返回 true，否则返回 false。
```

```js
win = window.open();  //打开新的空白窗口
win.document.write ("<h1>这是新打开的窗口</h1>");  //在新窗口中输出提示信息
win.focus ();  //让原窗口获取焦点
win.opener.document.write ("<h1>这是原来窗口</h1>");  //在原窗口中输出提示信息
console.log(win.opener == window);  //检测window.opener属性值
win.close(); //关闭新打开的
window.close（）; /
```

####  load事件

会等待页面加载完毕后再执行load事件，js 可以写在任意位置了。 

```js
window.onload = function () {}
```

但这种写法，只能生效最后一个onload。

下面的没有限制

```js
 window.addEventListener('load', function () { })
```

```js
document.addEventListener('DOMContentLoaded', function () {})
```

只有当DOM加载完毕后，才触发，不包括样式表和图片、flash等 IE9. 当图片等较大时，改事件用户体验好

触发load事件的情况；

1. a 的跳转
2. f5
3. 前进后退

但火狐缓存了整个页面的信息。后退不能刷新。不能触发load。`pageshow`会在load事件后，页面显示触发；根据Event中的`persisted`判断是否是缓存中

的页面触发的pageshow

#### 窗口调整

```js
window.addEventListener('resize',function () {
   //  检测window宽度
	window.innerWidth
})
```

####  定时器

* setTimeout 只执行一次的定时器，单位毫秒， 

```js
// window.setTimeout(fn, mills)
// window.setTimeout(‘fn（）’, mills)
let timer = window.setTimeout(fn, 3000)
// 停止计时器
window.clearTimeout(timer)
```

* setIntervalL 反复调用回调函数

* ```js
  
   function fn() {
    	// 时分秒实现
  }
  // 为防止刷新后的第一秒页面空白 先执行fn
  fn();
  let timer = window.setInterval(fn, 3000)
  //清除计时器
  window.clearInterval(timer)
  
  let btn = document.querySelector('.btn');
      let time = 3;
      btn.addEventListener('click', function () {
          btn.disabled = true;
          let timer = setInterval(function () {
              if(time === 0){
                  clearInterval(timer);
                  btn.disabled = false;
                  btn.innerHTML = 'send';
                  time = 3;
              }else {
                  btn.innerHTML = `还剩下{$time}秒`;
                  time--;
              }
          }, 1000)
  ```

#### this

todo: this

1. 局作用域下 和 普通函数调用中this指向window

```
console.log(this);

function f() {
 	console.log(this);
}
```

2. 方法调用中，指向调用者
3. 构造函数中this指向构造函数的实例

####  同异步

* 同步任务

  所有同步任务都在主线程的执行栈上

* 异步任务

  异步任务是回调函数实现， 所有相关回调函数都添加到任务队列中

  1. 普通事件
  2. 资源加载 load error
  3. 定时器

```js
console.log(1); // 先执行同步
setTimeout(f, 0)// 将回调函数放入队列
console.log(2); // 执行同步，等待执行栈的同步任务执行完毕，再执行栈依次执行队列的异步任务。
function f() {
    console.log(3);
}
// 输出 1 2 3
```



todo: js执行机制

#### JS机制

主线程执行栈将异步任务给异步进程处理回调任务，如果触发回调，异步进程将其写入任务队列。等待同步任务执行完毕后。会轮询任务队列。这被称为事件循环

####  location

URI，统一资源标志符(Uniform Resource Identifier， URI)，表示的是web上每一种可用的资源，如 HTML文档、图像、视频片段、程序等都由一个URI进行标识的。

URL（Uniform Resource Locator,统一资源定位器），它是WWW的统一资源定位标志，就是指网络地址。URL是URI的一个子集。

`protocol :// hostname[:port] / path / [:parameters][?query]#fragment`

[URL格式_百度百科 (baidu.com)](https://baike.baidu.com/item/URL格式/10056474?fr=aladdin)

| hash                                                         | 设置或返回从井号 (#) 开始的 URL（锚）。       |
| ------------------------------------------------------------ | --------------------------------------------- |
| [host](https://www.w3school.com.cn/jsref/prop_loc_host.asp)  | 设置或返回主机名和当前 URL 的端口号。         |
| [hostname](https://www.w3school.com.cn/jsref/prop_loc_hostname.asp) | 设置或返回当前 URL 的主机名。                 |
| [href](https://www.w3school.com.cn/jsref/prop_loc_href.asp)  | 设置或返回完整的 URL。直接前往地址，没有后退  |
| [pathname](https://www.w3school.com.cn/jsref/prop_loc_pathname.asp) | 设置或返回当前 URL 的路径部分。               |
| [port](https://www.w3school.com.cn/jsref/prop_loc_port.asp)  | 设置或返回当前 URL 的端口号。                 |
| [protocol](https://www.w3school.com.cn/jsref/prop_loc_protocol.asp) | 设置或返回当前 URL 的协议。                   |
| [search](https://www.w3school.com.cn/jsref/prop_loc_search.asp) | 设置或返回从问号 (?) 开始的 URL（查询部分）。 |

| 属性                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [assign()](https://www.w3school.com.cn/jsref/met_loc_assign.asp) | 加载新的文档。重定向页面：记录历史,可后退                    |
| [reload()](https://www.w3school.com.cn/jsref/met_loc_reload.asp) | 重新加载当前文档（点击刷新）。false = ′f5’ true = ctrl  f5 = 刷新缓存 |
| [replace()](https://www.w3school.com.cn/jsref/met_loc_replace.asp) | 用新的文档替换当前文档。没有历史，无法后退                   |

```js
let btn = document.querySelector('.btn');
let div = document.querySelector('div');


btn.addEventListener('click', function () {
    location.href = 'https://www.sina.com.cn/'
})
let time = 10;
fn();
function fn() {
    if(!time){
        time = 10;
        // 自动跳转页面，不打开新页面
        location.href = 'https://www.sina.com.cn/'

    }else {
        div.innerHTML = `还剩${time}秒跳转首页`
        time --;
    }

}

setInterval(fn, 1000)
```

#### navigator

Navigator 对象包含有关浏览器的信息。

[js判断浏览器版本以及浏览器内核的方法_javascript技巧_脚本之家 (jb51.net)](https://www.jb51.net/article/60121.htm)

#### History

History 对象包含用户（在浏览器窗口中）访问过的 URL。

History 对象是 window 对象的一部分，可通过 window.history 属性对其进行访问。

| [ length](https://www.w3school.com.cn/jsref/prop_his_length.asp) | 返回浏览器历史列表中的 URL 数量。 |
| ------------------------------------------------------------ | --------------------------------- |

| [back()](https://www.w3school.com.cn/jsref/met_his_back.asp) | 加载 history 列表中的前一个 URL。   |
| ------------------------------------------------------------ | ----------------------------------- |
| [forward()](https://www.w3school.com.cn/jsref/met_his_forward.asp) | 加载 history 列表中的下一个 URL。   |
| [go()](https://www.w3school.com.cn/jsref/met_his_go.asp)     | 加载 history 列表中的某个具体页面。 |

###  网页特效

####  元素偏移offset

动态获取元素的位置，相对于定位的父元素，不带单位

如果父亲没有定位，则以body为准

* offsetTop
* offsetLeft ： 盒子相对定位父元素的距离
* offsetWidth: 包含width， padding、 border的盒子的大小
* offsetHeight
* offsetParent: 该元素带有定位的父元素。如果没有返回body， `parentNode` 返回亲父亲

style 与 offset的区别：

style： *

*  只能获取行内样式值，* 
* 获取值带有px单位，* 

* style。width不包含padding和border

* 可读写
* 适用于更改值

offset:

* 可以读取任意样式表中的样式

* 数值没有单位
* 包含width， padding、 border
* 只能读取
* 适用于获取实际大小和位置

```js
let div = document.querySelector('.box');
// 获取鼠标在盒子里的坐标 
div.addEventListener('mousemove', function (e) {
    let x = e.pageX - this.offsetLeft;
    let y = e.pageY - this.offsetTop;
    let left = e.pageX - x;
    let top = e.pageY - y;
})
```

模态框

触发， keydown（获取鼠标在盒子里的坐标 ） move(改变left、 top)  keyup(移除move)

京东放大镜

```js
<!doctype html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <!--以ie浏览器的最高版本内核渲染页面-->
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        .preview_img {
            width: 400px;
            height:300px;
            border: 1px solid #ccc;
            position: relative;
            margin: 100px auto;
            /*cursor: move;*/
        }
        .preview_img>img {
            width: 100%;
        }
        .mask {
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 200px;
            height: 200px;
            background-color: yellow;
            opacity: .1;
            cursor: move;
        }
        .back {
            display: none;
            width: 500px;
            height: 500px;
            position: absolute;
            left: 410px;
            top:0;
            background-color: #cccccc;
            z-index: 999;
            border: 1px solid #ccc;
            overflow: hidden;
        }
        .back>img {
            position: absolute;
            top: 0;
            left: 0;
        }

    </style>
    
    <title></title>
</head>
<body>
<div class="preview_img">
    <img src="images/girls.jpg" alt="">
    <div class="mask"></div>
    <div class="back">
        <img src="images/girls.jpg" alt="" class="big">
    </div>
</div>
</body>
<script>
    let preview_img = document.querySelector('.preview_img')
    let mask = document.querySelector('.mask');
    let back = document.querySelector('.back');

    preview_img.addEventListener('mouseover', function (e) {
        mask.style.display = 'block';
        back.style.display = 'block';


    })
    preview_img.addEventListener('mouseout', function () {
        mask.style.display = 'none';
        back.style.display = 'none';
    })
    preview_img.addEventListener('mousemove',function (e) {
        // 获取鼠标在盒子位置
        let x = e.pageX - this.offsetLeft;
        let y = e.pageY - this.offsetTop;
        // 控制黄色区域在盒子呢移动
        let left =  x - mask.offsetWidth/2;
        let top = y - mask.offsetHeight/2;
        let maskMaxX = preview_img.offsetWidth - mask.offsetWidth;
        let maskMaxY = preview_img.offsetHeight - mask.offsetHeight;
        if (left <= 0 ){
            left = 0 ;
        }else if(left >= maskMaxX) {
           left = maskMaxX;
        }
        if (top <= 0 ){
            top = 0 ;
        }else if(top >= maskMaxY) {
            top = maskMaxY;
        }
        mask.style.left = left + 'px';
        mask.style.top = top + 'px';

        // 算大图移动  大图移动距离 = 遮挡移动 * 大图移动最大距离 / 遮挡移动最大距离
        // 大图
        let big = document.querySelector('.big');
        // 大图最大移动距离
        let bigMaxX = big.offsetWidth - back.offsetWidth;
        let bigMaxY = big.offsetHeight - back.offsetHeight;
        // 大图移动距离
        let bigX = left * bigMaxX / maskMaxX;
        let bigY = top * bigMaxY / maskMaxY;
        big.style.left = - bigX + 'px';
        big.style.top = - bigY + 'px';

    })

</script>
</html>
```

#### 元素可视区 client

* clientTop
* clientLeft ： 返回元素左边框的大小。
* clientWidth: 返回包含padding + 内容区width的宽度， 不包含border，不带单位
* clientHeight

#### 元素滚动scroll

* scrollTop
* scrollLeft ： 返回被卷去的左侧距离， 隐藏的大小
* scrollWidth: 返回自身的实际宽度， 不包含border，不带单位。 当出现滚动时，client无法获取实际宽度
* scrollHeight

确定事件源 document， 事件 scroll， 

判断页面卷起的头部使用，``window.scrollY`, `element.scrollTop` 判断元素卷起的大小

淘宝侧边栏

注意兼容问题

```js
<!doctype html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <!--以ie浏览器的最高版本内核渲染页面-->
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        .w {
            width: 1200px;
            margin: 10px auto;
        }
        .slider-bar {
            position: absolute;
            width: 45px;
            height: 130px;
            top: 300px;
            left: 50%;
            margin-left: 600px;
            background-color: aqua;
        }
        .header {
            height: 150px;
            background-color: green;
        }
        .banner {
            height: 400px;
            background-color: gray;
        }
        .main {
            height: 1000px;
            background-color: yellow;
        }
        span {
            position: absolute;
            display: none;
            bottom: 0;
            background-color: #985f0d;
        }

    </style>

    <title></title>
</head>
<body>
<div class="slider-bar">
    <span class="goBack">go top</span>
</div>
<div class="header w">头部区域</div>
<div class="banner w">banner</div>
<div class="main w">主题</div>


</body>
<script>
    let sliderBar = document.querySelector('.slider-bar');
    let banner = document.querySelector('.banner');
    let main = document.querySelector('.main');
    let goBack = document.querySelector('.goBack');
    // 被卷曲的大小
    let bannerTop = banner.offsetTop;
    let mainTop = main.offsetTop;
    // console.log(mainTop)
    // 获取固定定位之后的顶部值
    let sliderBarTop = sliderBar.offsetTop - bannerTop;
    // window.scrollY
    document.addEventListener('scroll', function () {
        if(window.scrollY >= bannerTop ){
            sliderBar.style.position = 'fixed';
            // 为了滚丁顺滑
            sliderBar.style.top = sliderBarTop + 'px';
        }else {
            sliderBar.style.position = 'absolute';
            // 为了滚动顺滑
            sliderBar.style.top = 300 + 'px';
        }
        // console.log(window.scrollY)
        if(window.scrollY >= mainTop ){
            goBack.style.display = 'block';
        }else {
            goBack.style.display = 'none';
        }

    })
    function animate (element, target, callback){
        // 未解决元素的定时器多开问题
       if(!element.timer){
           element.timer = setInterval(function () {
               let step =  (target - window.scrollY)  / 10;
               step = step > 0 ? Math.ceil(step) : Math.floor(step);
               if (window.scrollY === target){
                   clearInterval( element.timer);
                   // 结束时调用函数
                   callback && callback();
               }
               console.log(step + window.scrollY)
               // element.style.left = window.scrollY + step + 'px';
               window.scroll (0, window.scrollY + step);
           }, 30)
       }else {
           console.log('不要重复点击')
       }
    }
    goBack.addEventListener('click',function () {
        animate(window, 0);
    })
</script>
</html>
```

#### 动画实现

1. 获取盒子位置
2. 移动位置
3. 定时器操作
4. 结束条件
5. 元素定位

```js
todo ： 单例模式 
// 必须先开启定位
 function animate (element, target, callback){
        // 未解决元素的定时器多开问题
        clearInterval( element.timer);
        element.timer = setInterval(function () {
            if (element.offsetLeft === target){
                clearInterval( element.timer);
                // 结束时调用函数
                if(callback){
                    callback();
                }
            }
            let step =  (target - element.offsetLeft)  / 10;
            step = step > 0 ? Math.ceil(step) : Math.floor(step);
            element.style.left = element.offsetLeft + step + 'px';
        }, 300)
    }
```

#### 轮播图

* 鼠标进入显示点击按钮，离开会隐藏按钮
* 点边侧的按钮，会切换图片，
* 播放同时切换下面分页器
* 分页器也会切换图片
* 没有操作自动播放
* 进过停止播放

无缝滚动：

```
 将第一个li复制一份放到最后。
 当ul滚动到最后的克隆图，让ul直接切换到第一张最左侧， left= 0;j=0。
```

```js
    <div class="focus">
        <a href="#" class="arrow-l">&lt;</a>
        <a href="#" class="arrow-r">&gt;</a>
		// ul应该比div大几倍，让li悬浮在一行
        <ul>
            <li>
                <a href="#"><img src="images/girls.jpg" alt=""></a>
            </li>
        </ul>
        <ol>
            <li></li>
            <li></li>
            <li></li>
        </ol>
    </div>

```

todo:轮播图

* 节流阀

  在点击函数外声明一个flag=true，先判断flag = true执行动画同时将flag = flase; 在回调函数中  flag = true； callback && callback();

##### 返回顶部

#### 移动端

#####  触屏事件

* touchstart：触摸
* touchmove: 在元素上移动
* touchend： 离开

##### touchEvent

* touches: 记录触摸屏幕的所有手指的列表
* targetTouches:记录触摸当前元素的手指列表
* changesTouches: 手指状态发生了改变的列表。有无变化

拖动元素：

* touchstart: 获取元素的初始坐标和盒子的位置
* touchmove： 计算手指的移动距离
* touchend

```js
let div = document.querySelector('div');
let startX = 0;
let startY = 0;
let y = 0;
let x = 0;
div.addEventListener('touchstart',function (e) {
    startX = e.targetTouches[0].pageX;
    startY = e.targetTouches[0].pageY;
    x = this.offsetLeft;
    y = this.offsetTop;
})
div.addEventListener('touchmove',function (e) {
    let moveX = e.targetTouches[0].pageX - startX;
    let moveY = e.targetTouches[0].pageY - startY;

    this.style.left = x + moveX + 'px';
    this.style.top = y + moveY + 'px';
    // 阻止屏幕滚动行为
    e.preventDefault()
})
```

##### classList

返回类的列表

```js
element.classList.add(name): 追加类名
element.classList.remove(name):删除
element.classList.taggle(name): 添加或取消
```



##### 移动端轮播图

```js
<!doctype html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <!--以ie浏览器的最高版本内核渲染页面-->
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        ul,ol {
            list-style: none;
        }
        .focus {
            position: relative;
            width: 750px;
            padding-top: 44px;
        }
        .focus ol{
            position: absolute;
            bottom: 5px;
            right: 5px;
        }
        .focus ul {
            width: 500%;
            overflow: hidden;
            /*显示第一张*/
            margin-left: -100%;
        }
        .focus ul li{
            float: left;
            width: 20%;
        }
        .focus ol li{
            display: inline-block;
            width: 10px;
            height: 5px;
            background-color: red;
            transition: all .3s;
        }
        .focus img {
            width: 100%;
        }
        .focus ol li.current {
            width: 15px;
        }


    </style>

    <title></title>
</head>
<body>
<div class="focus">
    <ul>
        <!--补充最前-->
        <li><img src="images/impact3.png" alt=""></li>

        <li><img src="images/impact1.png" alt=""></li>
        <li><img src="images/impact2.png" alt=""></li>
        <li><img src="images/impact3.png" alt=""></li>
        <!--补充最后-->
        <li><img src="images/impact1.png" alt=""></li>
    </ul>
    <ol>
        <li  class="current"></li>
        <li></li>
        <li></li>
    </ol>
</div>


</body>
<script>
    let focus = document.querySelector('.focus');
    let ul = focus.children[0];
    let ol = focus.children[1];
    let width = focus.offsetWidth;
    let index = 0;
    function play() {
        index ++ ;
        let translateX = -index * width
        ul.style.transition = `all .3s`;
        ul.style.transform = `translateX(${translateX}px)`;
    }
    let timer = setInterval(play, 3000);
    // 监听过渡事件完成. 注意动画时间要短于 定时器
    ul.addEventListener('transitionend',function (e) {
        if(index >= 3){
            index = 0;
            let translateX = -index * width
            ul.style.transition = 'none';
            ul.style.transform = `translateX(${translateX}px)`;
            // 倒着走
        }else if(index < 0){
            index = 2;
            let translateX = -index * width
            ul.style.transition = 'none';
            ul.style.transform = `translateX(${translateX}px)`;
        }
        // 分页跟随
        // 去除current
        ol.querySelector('li.current').classList.remove('current');
        ol.children[index].classList.add('current');
    })
    // 手指拖动
    let startX = 0;
    let moveX = 0;
    let flag = false;
    ul.addEventListener('touchstart',function (e) {
        startX = e.targetTouches[0].pageX;
        // 拖动时，暂停播放
        timer && clearInterval(timer)
    })
    ul.addEventListener('touchmove',function (e) {
        moveX = e.targetTouches[0].pageX - startX;
        let translateX = -index * width + moveX;
        // 取消动画
        ul.style.transition = 'none';
        ul.style.transform = `translateX(${translateX}px)`;
        flag = true;
        e.preventDefault();
    })
    // 松手
    ul.addEventListener('touchend',function (e) {
        // 判断是否移动
        if (flag) {
            if(Math.abs(moveX) > 50){
                moveX > 0 ? index-- : index ++;
                let translateX = -index * width;
                ul.style.transition = `all .3s`;
                ul.style.transform = `translateX(${translateX}px)`;
            }else {
                let translateX = -index * width;
                ul.style.transform = `translateX(${translateX}px)`;
            }
        }
        timer && clearInterval(timer);
        timer = setInterval(play, 3000);
    });

</script>
</html>
```

##### 点击延时

移动端点击时，为了判断接下来的动作有300ms的延时。两手指捏大元素，双击缩放页面。

* 禁用缩放， <meta name="viewport", user-scalable=no> 不方便

* 判断触摸后是否滑动： 代码频繁

  ```js
      function tap(obj, callback) {
          let isMove = false;
          let startTime = 0;
          obj.addEventListener('touchstart',function () {
                  startTime = Date.now();
          })
          obj.addEventListener('touchmove',function () {
              isMove = true;
          })
          obj.addEventListener('touchend',function () {
              if (!isMove && (Date.now() - startTime) < 150){
                  callback && callback();
              }
              isMove = false;
              startTime = 0;
          })
      }
      tap(element, fn);
  ```

* fastclick.js 插件

  ```js
  <script type='application/javascript' src='/path/to/fastclick.js'></script>
  if ('addEventListener' in document) {
  	document.addEventListener('DOMContentLoaded', function() {
  		FastClick.attach(document.body);
  	}, false);
  }
  ```

  

#####  轮播图插件Swiper

1. [Swiper中文网-轮播图幻灯片js插件,H5页面前端开发](https://www.swiper.com.cn/)
2. 在下载的压缩包中，选demo看类型， 在dist文件夹，引入css和js文件
3. 将html结构引入。引入css样式， 引入 js代码调用

##### superSlide， touchSlide， isScroll   

##### zy.media.js

移动视频播放插件

#####  移动端开发框架

1. 引入依赖和css，js文件
2. 引入html结构，修改代码
3. `Auto.js` 是个基于 `JavaScript` 语言运行在Android平台上的脚本框架

### 本地存储

* 数据存在浏览器中

* sessionStorage 5M localStorage 20M,
*  只存json字符串



####  sessionStorage 

window对象 

特点：

* 关闭浏览器窗口就消失
* 数据可以共享
* 键值对存储

```js
sessionStorage.setItem('key', val)
let item = sessionStorage.getItem('key');
sessionStorage.removeItem('key');
 sessionStorage.clear()： 清除所有
```

######  localStorage 

* 本地化存储，永久有效
* 同一浏览器数据可以共享
* 键值对存储

```js
localStorage .setItem('key', val)
let item = localStorage.getItem('key');
localStorage.removeItem('key');
localStorage.clear()： 清除所有
```

## 库

### jquery

```js
//入口函数 相当于原生的DOMContentLoaded.
$(document).ready(function () {
    $('div').hide();
})
$(function () {
    
});
```

#### 顶级对象 JQuery || $

相当于window对象, 本质是伪数组

```js
$() 
JQuery()
```

#### DOM对象与JQuery对象

DOM对象：原生JS对象, 不能相互调用.

* DOM 转换为 JQuery对象 ： $(DOM 对象) 
* JQuery转换为 DOM 对象 ： $(‘div’)[0],   $(‘div’).get(0)

#### 常用api

隐式迭代，内部自动循环给选择器添加方法。

索引从零开始， 方法从层级关系处理

链式编程

###### 选择器

* 基础选择器

  ```js
  $("css选择器").css(attr: value)
  ```

* 筛选选择器

  ```js
  :first:
  :eq(2):
  :odd:
  :even:
  :last:
  :checked
  ```

* 筛选方法

  ```js
  parent(): 查找亲父元素
  parents(selector) 查找祖先元素
  children(selector): 查找亲子元素 ul>li
  find(selector):  ul li
  siblings(selector): 不包含自身的兄弟元素
  hasClass(name)
  nextAll( [])
  preAll( [])
  eq(selector): :eq(2):
  
  ```

##### 方法

```js
mouseover(function(){})
show/hide([speed, easing fn])
css(attr)
css(attr: value)
css({
    width:100px,
    color:#fff
})
add/remove/toggleClass('className'): 不影响原来的类

slideUp/slideDown/silderToggle([speed, easing fn]): 滑动

hover([enterfn, leavefn]): mouseenter mouseleave的简写
change(): 选中状态
click()

// 动画排队
stop(): 必须写在动画的前面，停止上一次动画，阻止多次触发。
// 淡入淡出
fadeIn/fadeOut/fadeToggle([speed easing fn]): 淡入淡出
fadeTo([s]) :修改透明
// 动画
animate(params, speed easing fn):自定义动画 params {width:100}
// 属性值
prop(attr): 获取元素内置属性
prop(attr: value): 获取元素内置属性
attr(attr): 可获取和设置自定义属性
data(attr:value)存放在元素的缓存中（内存）, 当获取的是h5的属性时data('index‘） 不用谢data-index
 // 文本方法                                              
html(text):相当于innerHTML
text() 相当于innerText
val() 相当于value

toFixed(2): 保留两位小数


```

#####  元素操作

```js
// DOM对象
$('div').each(function(index, domElement){})
$.each(obj, function(){}): 遍历数据处理 obj是对象或者数组

append()
preppend()： 在子元素的最前面
after() 在什么的后面
before()
remove（）：删除
empty() 清空子节点 
html("")清空子节点
```

##### 尺寸

```js
width(): 不包含border，padding
innerWidth(): 包含padding的width
outerWidth() 包含border，padding的
outerWidth(true) 包含border，padding， margin的
```

##### 位置

```js
offset(): 距离文档的距离{left, top} (只以文档为标准)
position(): 获取带有定位的父级偏移， 如果没有以文档为准
scrollTop()： 盒子距离文档顶部的距离
$('html,body').stop().animate({scrollTop: 0})
```

##### 事件

* 注册事件

  ```js
  $('').click(function(){})
  ```

  

* 事件处理

  ```js
  $('div').on({
      click: function () {},
      mouseenter: function () {},
  }, )
  $('ul').on('click change',li, function () {}) 事件委托给ul,处理点击事件
  // on可以给动态创建的元素绑定事件，click无法处理动态创建的事件
  off() 解绑on事件
  $('ul').on('click change',li)解绑事件委托
  one（）： 只能触发一次的事件 
  div. click()
  trigger（‘click’）：自动触发的事件
  $('').triggerHandler('click') : 不触发元素的默认行其他方法
  ```
  
  

#### 其他

```js
$.extend(true,tagetObj, obj): true:深拷贝（不会覆盖）、目标， 复制的对象

```

##### JQuery 冲突

* $冲突解决， 使用Jquery（）

* 释放$的控制权，自定义JQuery函数名

  ```js
  $(function () {
      let custom = $.noConflict();
      console.log(custom("div"));
  })
  ```

#### JQuery 插件

[dowebok - 做好网站](https://www.dowebok.com/)

[jQuery之家-自由分享jQuery、html5、css3的插件库 (htmleaf.com)](http://www.htmleaf.com/)



##### 图片懒加载

EasyLazyLoad.js, 引入的js文件，必须在所有图片的下面

todo:图片懒加载

##### 瀑布流

##### 全屏滚动

fullpage.js.  github

[jQuery全屏滚动插件fullPage.js_dowebok](https://www.dowebok.com/77.html)

### BootStrap

[2021最新完整版Bootstrap教程（最给力的前端框架）bootstrap框架讲解-快速上手,最适合后端开发人员的bootstrap保姆级使用教程_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1TU4y1p7zU/?spm_id_from=333.788.recommend_more_video.4)

### 数据可视化

都基于：

Canvas：位图的图像 只能缩放显示 适合像素处理，动态渲染和大数据量绘制

 SVG ： 基于矢量的 处理图形大小的改变

* D3.js： 评价最好的前端库，定制化，学习难度大， SVG 是基于 DOM 操作的，**支持更精确的用户交互**，
* Echart.js ： 百度开源库   数据量多 基于canvas的  不灵活
* Highcharts.js    国外
* AntV
* threejs  WebGL

#### Echart.js

##### 基本使用

1. 引入js
2. 给出DOM容器
3. 初始化echart对象
4. 指定配置和数据（根据options， 设定不同的图）
5. 设置echart

```js
<!doctype html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <!--以ie浏览器的最高版本内核渲染页面-->
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="js/echarts.min.js"></script>
    <style>
        // 必须给定大小
        .box {
            width: 400px;
            height: 600px;
            background-color: yellow;
        }
    </style>
    <title> EChart 数据可视化</title>
</head>
<body>
        // 准备容器
 <div class="box"></div>
</body>
<script>
    // 初始化
    let chart = echarts.init(document.querySelector('.box'));
    // 配置
    let options = {
        title: {
            text: 'ECharts 入门示例'
        },
        tooltip: {},
        xAxis: {
            data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
        },
        yAxis: {},
        series: [
            {
                name: '销量',
                type: 'bar',
                data: [5, 20, 36, 10, 10, 20]
            }
        ]
    }
    // 应用
    chart.setOption(options);
</script> 
</html>
```

##### 配置

* title:表的标题

* toolttip: 提示框 数据标示

* legend: 图例组件 

* toolbox： 工具栏 下载为图片

* grid: 网格

* XAxis, YAxis,： 坐标轴

* color 颜色设置

* series ： 数据对象组成的数组

  ```js
  name:决定legend 和 tooltip
  type:图标类型
  stack: 数据堆叠， 去掉属性，或者改写属性
  data: [1122， {}， 23] // 数据点, 可以是数值，也可以设置柱对象来控制**单独**柱状图的样式 
  ```

##### 适配

设计稿是1920px

PC端适配： 宽度在 1024~1920之间页面元素宽高自适应

flexible.js 把屏幕分为 24 等份

cssrem 插件的基准值是 80px

插件-配置按钮—配置扩展设置–Root Font Size 里面 设置。

设计稿 1920px

1024 ~ 1920 等比例缩放

##### 边框图片

盒子大小不一，边框样式相同。可以使用css3的border-image.

**要求** 使用九宫格形式 代码切图切四个角， 需要先指定border

```html
<div class="panel">
    <div class="inner"></div>
</div>
```

```css
.panel {
    position: relative;
    border-image-source: url("../images/logo.png");
    border-image-slice: 上右下左; 不加单位，直接使用px数值 相当于border的宽度控制了
    border-image-width: 30px;默认border的宽度，但不影响box的内容
    border-image-repeat: round;  边框是否铺满
}
采用绝对定位将inner 拉伸压在border上， 将父容器完全覆盖 让内容在父盒子内显示
.inner {
    position: absolute;
    top: 20px;
    right: 30px;
    bottom: 40px;
    left: 60px;
    padding:2px 3px;-
}
```

##### 字体图标

* 类名调用
  1. 引入css 和 fonts
  2. class = “name”

##### 图表缩放

```js
 window.addEventListener('resize',function () {
        chart.resize();
 })
```

##### 第三方模块

echarts Gallery  [Make A Pie](https://www.makeapie.com/explore.html)

**注意** ： 地理地图，不是图片，而是点面构成的。 必须使用china.js

## 面向对象

### 类和对象ES6

```js
class Sun {
    // new 对象时自动调用 返回对象
     constructor(uname) {
         this.uname = uname;
     }
     // 公有方法
     sing（） {
         
     }
 }
let john = new Sun('bitch');
console.log(john.uname)
```

#### 类的继承

```js
    class Sun {
        constructor(uname) {
            this.uname = uname;
        }
    }
    class Star extends Sun {
        constructor(uname) {
            super(uname);
            this.btn =  document.querySelector('button');
            this.btn.onclick = this.sing;
        }
        sing() {
            console.log(this.name)
        }
    }
    let john = new Sun('bitch');
    console.log(john.uname)
```

* 子类可以通过super()调用父类的构造方法
* 子类可以通过super.say()调用父类的普通方法
* 子类调用方法先查自己的方，再查父类的。就近原则

**注意**   

* 如果要显示调用super() 执行父构造器后， 才能调用this。
* ES6中类没有变量提升，必须先定义在实例对象
* 公有的属性和方法一定要加this调用

#### this的指向问题

* constructor 中的this 指向 实例对象

* 类公有方法的this， 指向调用者  实例对象。
* 上诉的sing 方法中的this， 指向了触发事件的btn。指向方法的调用者， 可以使用that 全局保存this 注意释放

```js
    class Sun {
        constructor(uname) {
            this.uname = uname;
        }
    }
    let that;
    class Star extends Sun {
        constructor(uname,age) {
            super(uname);
            this.age = age
            this.btn =  document.querySelector('input');
            this.btn.onclick = this.sing;
            that = this;
        }
        sing() {
            console.log(this.uname)
            console.log(that.age)
        }
    }
    let john = new Star('bitch',10);
    john.sing()
	that = null;
```



## ES6

###  新特性

###              

## 技巧

### 阻止链接跳转

```js
<a href="javascript:void(0);">@me</a>
<a href="javascript:;">@me</a>
```

### 立即执行函数

匿名函数并且执行,被当做一个语句

独立创建了作用域,解决冲突问题

```js
( function () {}) ();
( function () {}() );
li.click() : 自动触发点击事件
input.select(): 自动选中文字
```

### html双击禁止选中文字

```js
window.getSelection ? window.getSelection().removeAllRanges() : document.selection.empty();
```

#### 复合就执行

```js
 X && X()
```



## **专栏**

[Miya's 技术学习小记 - 知乎 (zhihu.com)](https://www.zhihu.com/column/miya393)

前端变化 https://www.zhihu.com/question/428128531

[2021年 React项目推荐的和应该放弃的技术方案 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/378619948)

[webpack5用url-loader打包后出现图片打不开、资源重复_ChrisJin的博客-CSDN博客](https://blog.csdn.net/w184167377/article/details/118930758)

蓝湖，原型图

## 总结：

微前端（https://zhuanlan.zhihu.com/p/96464401）、全栈、大前端、前端工程化

### 数组去重的方法

[js 数组去重的几种方式及原理 - neilniu - 博客园 (cnblogs.com)](https://www.cnblogs.com/neilniu/p/9635055.html)

indexOf()

对象属性 obj[ key ]

全局变量的形式

[JS 内存分配](https://blog.csdn.net/qq_40028324/article/details/92970588)

[js常见的内存泄漏 - cwxwdm - 博客园 (cnblogs.com)](https://www.cnblogs.com/cwxwdm/p/10845376.html)

this :总结

todo: 回调地狱

todo:JS执行机制

todo：iframe

todo: codepen

todo: flexible.js代码

todo: 响应式瀑布流文件

todo:图片懒加载

todo:**《前端架构师课》**

todo: [正则表达式可视化-Visual Regexp：在线测试、学习、构建正则表达式 (wangwl.net)](https://wangwl.net/static/projects/visualRegex/#prefix=Y&source=Yemail)

* headless ui

* place-items：center： 垂直水平居中

* clip-path：polygon（点）
* clip-path：circle（）  圆形 shape-outside：circle 改变占位形状

* background：url：picsum.photos/200(定义宽，随机给图片)

### 查找属性，类型信息

* typeof( Xxx): 查看Xxx是基本数据类型
* instanceOf:  查看Xxx是不是某个构造函数的实例
* console.dir(): 查看属性

##  Dev Tools:

* 6个变量 $ 0-4: 0代表选中的元素， 1代表上次选中的元素， $_:代表上次控制台计算的结果
* 打开命令面板 ctrl  shift p : 
  1. 设置外观，Theme
  2. 截屏 screenshot(框选，全屏， 节点)
  3. dock

### css 调试

* ctrl + f: 可以字符串搜索，可以选择器
* console面板输入 inspect(document.getElementByID())

​	

### console

* 6个变量 $ 0-4: 0代表选中的元素， 1代表上次选中的元素，2上上次， $_:代表上次控制台计算的结果

* log(‘%c ’ “css样式”)

* console.error, warn, table.clear,time,assert trace

  ```js
  console.group('test start')
  console.log()
  console.log()
  console.groupEnd('test end')
  
  console.time()
  for i<100 {}
  console.timeEnd()
  console.table() ：将数组以表格的方式显示，可排序
  
  ```

### Source

在需要调试的代码部分，写入 debugger;

ctrl shift p  enable code folding: 折叠无关代码





## 技术栈

ES6,node.js. react，vite+vue3+ts，rust / wasm,  Blazor,pnpm，ahooks，Tailwind CSS， Jest

1. Interface Types Proposal 实施
2. Web IDL到Web Assembly的映射
3. import和<script>的支持
4. Typescript的WebAssembly后端

> **HTML**
>
> HTML基础 - 这部分比较简单，要求95%以上掌握，body内标签全手写
>
> HTML5， 主要是语义化，其他了解即可，有空可以了解一下
>
> 
>
> **CSS**
>
> CSS基础 - 80%以上掌握，主要是布局相关css必须全部掌握，浮动，清除浮动，所有position定位，盒子布局相关，BFC，高度塌陷，margin合并，为关键知识点
>
> 进阶 - 部分CSS3（ 媒体查询，动画，变型transform为主），自适应设计，常见导航栏，常用两列三列布局，flexbox布局，视差滚动，[轮播图](https://www.zhihu.com/search?q=轮播图&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})，精灵图，面包屑，字体图标，自定义字体
>
> 
>
> **JS**
>
> 基础部分 - 90%以上掌握，数据类型，操作符，语句，函数，数组，对象，内置对象，作为基础学习。
>
> API部分 - DOM作为重点专项学习，BOM仅了解即可。
>
> [面向对象](https://www.zhihu.com/search?q=面向对象&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})部分 - 面向对象（原型，继承），[作用域](https://www.zhihu.com/search?q=作用域&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})，闭包，this，new
>
> 高阶部分 - 主要是模块化思想（commonJS，AMD，CMD），[函数式编程思想](https://www.zhihu.com/search?q=函数式编程思想&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})（了解），JS内存管理，设计模式（主要是单例和工厂），MVC思想（mvp，mvvm），RESTful API
>
> 
>
> **其他**
>
> 需要了解一下，前端代码规范和风格指南，腾讯，阿里都有自己的规范，可以借鉴
>
> 需要了解一下，浏览器的兼容性问题，以及解决方案PostCSS+AutoPrefixer或webpack配置的用法
>
> 
>
> **2. 必须的相关技术**
>
> JSON -- 现在最常用的一种数据格式，取代了XML
>
> PHP -- 一种常见的后端语言，前端建议了解一下，需要学习通过php连接[mysql数据库](https://www.zhihu.com/search?q=mysql数据库&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})，还需掌握AJAX或任何一种替代技术
>
> 正则表达式 -- [字符串检索语法](https://www.zhihu.com/search?q=字符串检索语法&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})
>
> SQL -- 数据库的规范化语言
>
> MYSQL -- SQL的应用，需要学会搭建并使用一个简单的mysql数据库，完成一些简单的sql语句
>
> Node JS -- 使用[JS语法](https://www.zhihu.com/search?q=JS语法&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})的服务器端语言（前端高阶重点语言之一）
>
> Linux -- 常用于服务器的操作系统，基本操作要会，可以用[virtual-box](https://www.zhihu.com/search?q=virtual-box&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})搭个ubantu系统
>
> 
>
> 
>
> **3. 工具，框架和库**
>
> JS常见库（比如：lodash，Underscore）
>
> JS[前端框架](https://www.zhihu.com/search?q=前端框架&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})（react，angular，vue，必学重点，需要掌握一种，了解其余两种）
>
> 模块打包工具（Browserify，RequireJS）
>
> 自动化构建工具（webpack，gulp必会，NPM scripts了解）
>
> JQuery（现在已经基本不需要，了解即可）
>
> BootStrap库（一个实用的CSS类库）
>
> 
>
> 
>
> **4，前端高阶（仅供参考）**
>
> - SSR（Next.js、Nuxt.js）
> - ES6及以上版本
> - TypeScript
> - 算法
> - 设计模式
> - [高阶函数](https://www.zhihu.com/search?q=高阶函数&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})
> - 后端技术
> - 运维技术
>
> 
>
> **5，设计相关**
>
> 会一种图片编辑工具（如：Photoshop）
>
> 会一种[矢量图](https://www.zhihu.com/search?q=矢量图&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})工具（如：Adobe illustrator）
>
> 会一种原型工具（如：Adobe XD）
>
> 
>
> **6，其他**
>
> - 理解DevOps
> - 理解[敏捷开发](https://www.zhihu.com/search?q=敏捷开发&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"article"%2C"sourceId"%3A148927405})
> - 理解TDD和DDD
> - PWA
> - HTTP
> - UX/UI
> - SEO
> - WEB安全
> - CI/CD
>
> 
>
> #### 计算机网络
>
> 掌握计算机网络的基础是一名前端工程师的基本素养，建议先学习以下的知识：
>
> 1. ✔︎ Internet 如何工作
> 2. ✔︎ HTTP 协议
> 3. ✔︎ 浏览器工作机制
> 4. ✔︎ DNS 及其运行机制
> 5. ✔︎了解域名、网站托管
>
> #### HTML
>
> 1. ✔︎ 学习 HTML 基础，标签、元素、表单验证等等
> 2. ✔︎ 语义化标签
> 3. ✔︎ 了解 Web 无障碍（Accessibility）
> 4. ✔︎ 学习 SEO 优化
>
> #### CSS
>
> 1. ✔︎ 学习 CSS 基础
> 2. ✔︎ 制作布局：浮动、定位、显示、盒模型、网格布局、弹性布局
> 3. ✔︎ 响应式设计和媒体查询（@media）
> 4. ✔︎ 结合 HTML 制作一个简单的网页作为最佳实践
>
> #### JavaScript
>
> 1. ✔︎ 学习语法和基本结构
> 2. ✔︎ 学习操作 DOM
> 3. ✔︎ 学习 Fetch API / Ajax（XHR）
> 4. ✔︎ ES6+ 和模块化 JavaScript
> 5. ✔︎ 了解变量提升、事件冒泡机制、作用域、原型、Shadow DOM、严格模式等概念
>
> #### 版本控制
>
> 1. ✔︎ Git 的基本操作
> 2. ✔︎ 创建账号并且学习使用 GitHub
> 3. ✔︎ 创建账号并且学习使用 GitLab
>
> #### Web 安全知识
>
> 1. ✔︎ HTTPS
> 2. ✔︎ 内容安全策略（CSP）
> 3. ✔︎ 跨域资源共享
> 4. ✔︎ OWASP 安全风险
>
> ------
>
> 上面的内容是前端最基础的部分，建议多花时间，掌握好每一个知识点。
>
> 从这开始，将进入前端工程化的部分，你可能会接触到很多种不同的框架，并学习使用多种的工具为自己的开发提效。
>
> #### 包管理工具
>
> npm 和 yarn 都很好，选择一个学习即可，他们两是相似的
>
> 1. ✔︎ npm
> 2. ✔︎ yarn
>
> #### CSS 构架
>
> 通过使用现代的 CSS 框架和 CSS-in-JS 的书写方式，不用再担心 CSS 的构架问题，但熟悉 BEM 规范是一个不错的选择。
>
> 1. ✔︎ BEM，一种书写规范
> 2. ✘ OOCSS
> 3. ✘ SMACSS
>
> #### CSS 预处理器
>
> 以下三个可选择一个进行学习。
>
> 1. ✔︎ SCSS
> 2. ✔︎ PostCSS
> 3. ✔︎ Less
>
> #### 构建工具
>
> 1. 任务执行器
>
> 2. - ✔︎ npm scripts
>   - ✘ Gulp
>
> 3. 代码检查和格式化工具
>
> 4. - ✔︎ Prettier 代码格式化
>   - ✔︎ ESLint 代码检查
>    - ✘ StandardJS
>
> 5. 模块打包
>
> 6. - ✔︎ Webpack
>   - ✔︎ Rollup
>    - ✔︎ Parcel
>
> #### 前端框架
>
> 前端框架推荐先学习 React，能理解函数式编程和组件化。Vue 的特点是上手快，中文文档齐全，可以选择性的学习。
>
> 1. ✔︎ React.js
>
> 2. - ✔︎Redux
>    - ✔︎ MobX
>
> 3. ✔︎ Vue.js
>
> 4. - VueX
>
> 5. ✔︎ Angular
>
> 6. - RxJS
>   - NgRx
>
> #### 现代 CSS
>
> 1. ✔︎ Styled Component
> 2. ✔︎ CSS Module
> 3. ✔︎ Styled JSX
> 4. ✔︎ Emotion
> 5. ✘ Radium
> 6. ✘ Glamorou
>
> #### Web 组件
>
> 1. ✔︎ HTML 模版
> 2. ✔︎ 自定义元素
> 3. ✔︎ Shadow DOM
>
> #### CSS 框架
>
> CSS 框架有两种，一种是基于 JavaScript 框架开发的应用程序。推荐的框架有：
>
> 1. ✔︎ Reactstrap
> 2. ✔︎ Material UI
> 3. ✔︎ TailWind CSS
> 4. ✔︎ Chakra UI
>
> 另外一种是纯 CSS 框架，默认不和 JavaScript 组件一起使用。
>
> 1. ✔︎ BootStrap
> 2. ✔︎ Materialize CSS
> 3. ✔︎ Bulma
>
> #### 测试
>
> 在这里你需要学习使用下面的框架进行单元、集成和功能测试。
>
> 1. ✔︎ Jest
> 2. ✔︎ react-testing-library
> 3. ✔︎ Cypress
> 4. ✔︎ Enzyme
>
> #### 类型检查器
>
> 1. ✔︎✔︎ TypeScript
> 2. ✘ Flow
>
> ------
>
> 上面是前端工程化的学习内容，接下来的内容涉及到性能、服务端渲染以及跨端，这一部分前端也叫被称作「大前端」。
>
> #### PWA
>
> 1. ✔︎ 学习 PWA 中使用到的 Web API：
>
> 2. - Storage
>    - Web Sockets
>   - Service Workers
>    - 定位
>   - 通知
>    - 设备方向
>   - 支付、证书等等
>
> 3. ✔︎ 计算、测量以及提高性能：
>
> 4. - PRPL 模式
>   - RAIL 模式
>    - 性能指标
>   - 学习使用 LightHouse
>    - 学习使用 DevTools
>
> #### 服务端渲染
>
> 1. ✔︎ Next.js （React.js）
> 2. ✔︎ Nuxt.js （Vue.js）
> 3. ✔︎ Universal（Angular）
>
> #### ✔︎ GraphQL
>
> 1. ✔︎ Apollo
> 2. ✔︎ Relay Modern
>
> #### ✔︎ 静态网站生成
>
> 1. ✔︎ Next.js
> 2. ✔︎ GatsbyJS
> 3. ✔︎ Nuxt.js
> 4. ✔︎ Vuepress
> 5. ✔︎ JekyII
> 6. ✔︎ Hugo
>
> #### ✔︎ 移动端应用开发
>
> 1. ✔︎ ReactNative
> 2. ✔︎ Flutter
>
> #### ✔︎ 桌面应用开发
>
> 1. ✔︎ Electron
> 2. ✔︎ Carlo
> 3. ✔︎ Proton Native
>
> #### ✔︎ WebAssembly

## 书

[现代 JavaScript 教程](https://zh.javascript.info/)



**《JavaScript权威指南（第六版）》** ★★★★★

淘宝前端团队翻译的，看译者列表都是一堆大神。这本书又叫犀牛书，号称javascript开发者的圣经，网上对此书评价很多，大概意思都是说这本书是一本JavaScript文档手册，没有完整看过一遍此书的都不能算是一名合格的前端工程师。

**《JavaScript[高级程序设计](https://www.zhihu.com/search?q=高级程序设计&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A157022092})》** ★★★★★

又称红宝书，雅虎首席[前端架构师](https://www.zhihu.com/search?q=前端架构师&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A157022092})，YUI的作者Zakas出品。虽然书名带了“高级”二字，但是讲得也很基础，而且行文风格很流畅，每一小节就像是一篇博客，读起来并不枯燥，个人感觉比上面那本犀牛书可读性更强。说到这里，也推荐大家多多关注作者的博客： [http://www.nczonline.net/](https://link.zhihu.com/?target=http%3A//www.nczonline.net/) ，上面也有许多高质量的博文。感觉这本书就像是作者平时的博文按照前端知识体系组织成了一本技术书。

**《[JavaScript DOM编程艺术](https://www.zhihu.com/search?q=JavaScript+DOM编程艺术&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A157022092})》**

作为初学者如果觉得上面两本书作为入门书来说太厚了，也可以看看这本，不厚，评价也很高，但是由于本人没看过，就不作过多评价了。

**《[JavaScript编程精解](https://www.zhihu.com/search?q=JavaScript编程精解&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A157022092})》** ★★★★

用上下班时间看完的第三本书。看起来比较吃力，第五章函数式编程和第六章的[面向对象编程](https://www.zhihu.com/search?q=面向对象编程&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A157022092})很多都没看懂。全书游戏式的编程教程还是很有意思的。译者tom大叔名头很大，翻译的质量也只是中规中矩吧。不过，还是get到很多技巧！这本书的推荐语说这本书用来入门很好，但是个人认为初学者并不合适看这本书入门，作者在代码示例中不自觉得使用了一些高级用法，初学者看容易晕菜。听说最近出了第二版，加入了NodeJS的内容，这本书是开源的：[http://eloquentjavascript.net/](https://link.zhihu.com/?target=http%3A//eloquentjavascript.net/)

\--------------------------------------------------

**《[编写可维护的JavaScript](https://www.zhihu.com/search?q=编写可维护的JavaScript&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A157022092})》** ★★★★

又一本Zakas的书，还没读完，基本上是zakas那本红宝书的子集，重点是javascript代码风格、规范以及最佳实践。

**《JavaScript异步编程》** ★★★★

掌握异步编程，显然是一位JS开发者必备的技能，用多看的畅读优惠看完了这本介绍js异步编程的科普小书，书中介绍了js异步编程的概念、场景和工具，不过更重要的是把这些工具给用起来。

**《JavaScript设计模式》** ★★★

作者似乎很偏爱JQuery的源码，不过这本书tom大叔翻译的很烂，代码也很多没有缩进。。。 不推荐。

**《[Effective JavaScript](https://www.zhihu.com/search?q=Effective+JavaScript&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A157022092})》** ★★★★

这本书我当时看到最后一章“并发”的部分就很吃力了，显然这是一本进阶的js书籍，还是先把那本[权威指南](https://www.zhihu.com/search?q=权威指南&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A157022092})啃完吧！听说这本书上的技巧对于IE6有很好的优化效果，不过显然书上提到的这些技巧肯定已经大量的运用到JQuery、Underscore这样流行的JS库中，这些第三方库已经帮我们把这些优化细节封装得很好了。

**《[JAVASCRIPT语言精髓与编程实践](https://www.zhihu.com/search?q=JAVASCRIPT语言精髓与编程实践&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A157022092})》**

一本讲JavaScript的硬书，以JavaScript这门语言为栗子，讲述编程语言的特性（动态语言、函数式编程、面向对象编程等等）。作者周爱民老师是前支付宝架构师，现[豌豆荚](https://www.zhihu.com/search?q=豌豆荚&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A157022092})架构师。

**《高性能JavaScript》**, **《Node.js开发指南》**,**《深入浅出Node.js》**，**《Web性能权威指南》**《深入理解JavaScript特性》，《Java编程思想》。**《ES6标准入门（第三版）》**

## 面试



* ```js
  function a() {
      return
      {
          "OK"
      }
  }
  a() undefined
  retrun 后省略了; 直接结束函数了返回了
  ```

* 
