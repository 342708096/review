# 前端复习大纲

## JS基础知识

### 值类型
字符串、数字、布尔、Undefined

### 引用数据类型
对象、函数、Symbol(es6)、null

除了Undefined, JavaScript的一切都可以看成对象, 或者说底层回自动包装成对象.
### typeof 能得到哪些类型？

```
typeof undefined // undefined
typeof 'abc' // string
typeof 123 //number
typeof true //boolean
typeof {} //object
typeof [] //object
typeof null //object 特殊的引用类型，并没有指向任何地址
typeof console.log //function
```

`typeof` 只能区分值类型的数据，不能区分引用类型(除function)，如果要区分引用类型用`instanceof`

### js 发生类型转换的情形
* 字符串拼接

	```
	var b = 100 + '10' // '10010'
	```
* ==运算符

	```
	100 == '100' // true 转化为字符串‘100’
	0 == '' // true 转化为false
	null == undefined //true 转换为false
	```
* if语句（强制转换为boolean类型）

	```
	//为false的情形
	if (0) {...}
	if (NaN) {...}
	if (null) {...}
	if ('') {...}
	if (undefined){...} 
	if (false) {...}
	```
* 逻辑运算 （强制转换为boolean类型）

### 何时使用 ==== 何时使用 ==

```
	if (obj.a == null ){
	  // 相当于 obj.a === null || obj.a === undefined
	}
```
除此以外一律用`===`

### JS中有哪些内置函数 -- 数据封装类对象
* Object
* Array
* Boolean
* Number
* String
* Function
* Date
* RegExp
* Error

### JS有哪些内置对象
* Math
* JSON

	```
	JSON.stringify({a: 10, b: 20})
	JSON.parse('{"a": 10,"b":20}')
	```

### Array

1. concat: 连接两个或更多的数组, 并返回结果
	
2. join: 数组连接成字符串
	
3. pop: 删除并返回数组的最后一个元素
	
4. shift: 删除并返回数组的第一个元素
	
5. reverse: 反序
	
6. slice(start, end): 从某个数组返回选定的元素
	
   **start**: 从何处开始选取,如果为负数则从尾部开始
   
   **end**: 可选.从何处结束如果是负数则从尾部算起
   
   **return**: 一个新的数组,并不会修改原数组
   
   	**arguments 转 array**: Array.prototype.slice.call(arguments,0)

7. sort: 排序

8. splice: 删除元素,并添加新的元素

9. push: 向数组末尾添加元素,返回新的长度

10. unshift: 向数组开头添加元素,返回新的长度

### Date

1. getDate(): 返回一个月中的某一天(1~31)

2. getDay(): 一周中的某一天(0~6) 

3. getFullYear(): 4位数字的年份

4. getTime(): 1970-1-1 至今的毫秒数

5. parse: 返回1970-1-1到指定日期字符串的毫秒数.

6. setTime(): 根据毫秒数来设置date

### Math

1. ceil(): 向上取整 Math.ceil(5.1) => 6 Math.ceil(-5.1) => -5

2. floor(): 向下取整 Math.ceil(5.1) => 5 Math.ceil(-5.1) => -6

3. parseInt: 舍去小数部分parseInt(5.1) => 5 parseInt(-5.1) => -5

4. round(): 把数四舍五入为最接近的整数 Math.round(5.5) => 6 Math.round(-5.5) => -5

### Number

1. MAX_VALUE	可表示的最大的数。1.7976931348623157e+308
2. MIN_VALUE	可表示的最小的数。5e-324
3. MAX_SAFE_INTEGER 9007199254740991
4. MIN_SAFE_INTEGER -9007199254740991
5. NaN	非数字值。NaN === NAN //false ,请用 Object.is
6. NEGATIVE_INFINITY	负无穷大，溢出时返回该值。
7. POSITIVE_INFINITY	正无穷大，溢出时返回该值。

### String

1. charAt(): 返回在指定位置的字符。

2. charCodeAt():	返回在指定的位置的字符的 Unicode 编码。

3. indexOf(search, from): 返回字符串首次检索到的位置.

4. match(str|reg): 返回数组或字符串, 如果没有匹配则返回null.
	
	match() 方法将检索字符串 stringObject，以找到一个或多个与 regexp 匹配的文本。这个方法的行为在很大程度上有赖于 regexp 是否具有标志 g。
	如果 regexp 没有标志 g，那么 match() 方法就只能在 stringObject 中执行一次匹配。如果没有找到任何匹配的文本， match() 将返回 null。否则，它将返回一个数组，其中存放了与它找到的匹配文本有关的信息。该数组的第 0 个元素存放的是匹配文本，而其余的元素存放的是与正则表达式的子表达式匹配的文本。除了这些常规的数组元素之外，返回的数组还含有两个对象属性。index 属性声明的是匹配文本的起始字符在 stringObject 中的位置，input 属性声明的是对 stringObject 的引用。
	如果 regexp 具有标志 g，则 match() 方法将执行全局检索，找到 stringObject 中的所有匹配子字符串。若没有找到任何匹配的子串，则返回 null。如果找到了一个或多个匹配子串，则返回一个数组。不过全局匹配返回的数组的内容与前者大不相同，它的数组元素中存放的是 stringObject 中所有的匹配子串，而且也没有 index 属性或 input 属性。
	注意：在全局检索模式下，match() 即不提供与子表达式匹配的文本的信息，也不声明每个匹配子串的位置。如果您需要这些全局检索的信息，可以使用 RegExp.exec()。
	
5. replace(reg|str, replacement)	
	字符串 stringObject 的 replace() 方法执行的是查找并替换的操作。它将在 stringObject 中查找与 regexp 相匹配的子字符串，然后用 replacement 来替换这些子串。如果 regexp 具有全局标志 g，那么 replace() 方法将替换所有匹配的子串。否则，它只替换第一个匹配子串。
	replacement 可以是字符串，也可以是函数。如果它是字符串，那么每个匹配都将由字符串替换。但是 replacement 中的 $ 字符具有特定的含义。如下表所示，它说明从模式匹配得到的字符串将用于替换。
	
	|字符|	替换文本|
	|:------------- |:---------------:| 
	|$1、$2、...、$99|	与 regexp 中的第 1 到第 99 个子表达式相匹配的文本。|
	|$&	|与 regexp 相匹配的子串。|
	|$`|	位于匹配子串左侧的文本。|
	|$'|	位于匹配子串右侧的文本。|
	|$$	|直接量符号。|
	
	在本例中，我们将把 "Doe, John" 转换为 "John Doe" 的形式：
	
	```
	name = "Doe, John";
	name.replace(/(\w+)\s*, \s*(\w+)/, "$2 $1");
	```
	
6. slice(start,end) 提取字符串的某个部分并返回一个新的字符串(不包含end),负数表示从后往前数.

7. substring(start,stop) 提取字符串的某个部分并返回一个新的字符串(不包含end)
	重要事项：与 slice() 和 substr() 方法不同的是，substring() 不接受负的参数。
	
8. substr(start,length) 方法可在字符串中抽取从 start 下标开始的指定数目的字符。start负数表示从后往前数.
	重要事项：ECMAscript 没有对该方法进行标准化，因此反对使用它。
	
### RegExp
1. 修饰符

	|修饰符	|描述|
	|:------------- |:---------------:| 
	|i	|执行对大小写不敏感的匹配。|
	|g	|执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。|
	|m	|执行多行匹配。|
	
2. 方括号

	|表达式	|描述|
	|:------------- |:---------------:|
	|[abc]	|查找方括号之间的任何字符。|
	|[^abc]|	查找任何不在方括号之间的字符。|
	|[0-9]	|查找任何从 0 至 9 的数字。|
	|[a-z]	|查找任何从小写 a 到小写 z 的字符。|
	|[A-Z]	|查找任何从大写 A 到大写 Z 的字符。|
	|[A-z]	|查找任何从大写 A 到小写 z 的字符。|
	|[adgk]|	查找给定集合内的任何字符。|
	|[^adgk]|	查找给定集合外的任何字符。|
	|(red \| blue \| green)|	查找任何指定的选项。|
	
3. 元字符

	|元字符|	描述|
	|:------------- |:---------------:|
	|.	|查找单个字符，除了换行和行结束符。|
	|\w	|查找单词字符。|
	|\W	|查找非单词字符。
	|\d	|查找数字。|
	|\D|	查找非数字字符。|
	|\s|	查找空白字符。|
	|\S|	查找非空白字符。|
	|\b|	匹配单词边界。|
	|\B|	匹配非单词边界。|
	|\0|	查找 NUL 字符。|
	|\n|	查找换行符。|
	|\f|	查找换页符。|
	|\r	|查找回车符。|
	|\t|	查找制表符。|
	|\v|	查找垂直制表符。|
	|\xxx|	查找以八进制数 xxx 规定的字符。|
	|\xdd|	查找以十六进制数 dd 规定的字符。|
	|\uxxxx|	查找以十六进制数 xxxx 规定的 Unicode 字符。|

4. 量词

	|量词	|描述|
	|:------------- |:---------------:|
	|n+|	匹配任何包含至少一个 n 的字符串。|
	|n*|匹配任何包含零个或多个 n 的字符串。|
	|n?|	匹配任何包含零个或一个 n 的字符串。|
	|n{X}|	匹配包含 X 个 n 的序列的字符串。|
	|n{X,Y}|	匹配包含 X 至 Y 个 n 的序列的字符串。|
	|n{X,}|	匹配包含至少 X 个 n 的序列的字符串。|
	|n$|	匹配任何结尾为 n 的字符串。|
	|^n|	匹配任何开头为 n 的字符串。|
	|?=n|	匹配任何其后紧接指定字符串 n 的字符串。|
	|?!n|	匹配任何其后没有紧接指定字符串 n 的字符串。|
	
5. exec(): 方法用于检索字符串中的正则表达式的匹配。

	**返回值**
	
	返回一个数组，其中存放匹配的结果。如果未找到匹配，则返回值为 null。
	
	**说明**
	
	exec() 方法的功能非常强大，它是一个通用的方法，而且使用起来也比 test() 方法以及支持正则表达式的 String 对象的方法更为复杂。
	
	如果 exec() 找到了匹配的文本，则返回一个结果数组。否则，返回 null。此数组的第 0 个元素是与正则表达式相匹配的文本，第 1 个元素是与 RegExpObject 的第 1 个子表达式相匹配的文本（如果有的话），第 2 个元素是与 RegExpObject 的第 2 个子表达式相匹配的文本（如果有的话），以此类推。除了数组元素和 length 属性之外，exec() 方法还返回两个属性。index 属性声明的是匹配文本的第一个字符的位置。input 属性则存放的是被检索的字符串 string。我们可以看得出，在调用非全局的 RegExp 对象的 exec() 方法时，返回的数组与调用方法 String.match() 返回的数组是相同的。
	
	但是，当 RegExpObject 是一个全局正则表达式时，exec() 的行为就稍微复杂一些。它会在 RegExpObject 的 lastIndex 属性指定的字符处开始检索字符串 string。当 exec() 找到了与表达式相匹配的文本时，在匹配后，它将把 RegExpObject 的 lastIndex 属性设置为匹配文本的最后一个字符的下一个位置。这就是说，您可以通过反复调用 exec() 方法来遍历字符串中的所有匹配文本。当 exec() 再也找不到匹配的文本时，它将返回 null，并把 lastIndex 属性重置为 0。
	
	**提示和注释**
	
	**重要事项**：如果在一个字符串中完成了一次模式匹配之后要开始检索新的字符串，就必须手动地把 lastIndex 属性重置为 0。
	
	**提示**：请注意，无论 RegExpObject 是否是全局模式，exec() 都会把完整的细节添加到它返回的数组中。这就是 exec() 与 String.match() 的不同之处，后者在全局模式下返回的信息要少得多。因此我们可以这么说，在循环中反复地调用 exec() 方法是唯一一种获得全局模式的完整模式匹配信息的方法。
	
6. compile(): 方法用于在脚本执行过程中编译正则表达式。也可用于改变和重新编译正则表达式。
	为什么要编译正则表达式? 因为正则表达式对象是有状态的(lastIndex), 编译后可以重置状态.
	
7. test(str): 检测一个字符串是否匹配某个正则表达式, 返回一个boolean.



### 全局对象\函数

1. encodeURI() 函数可把字符串作为 URI 进行编码。

	**说明**
	
	该方法不会对 ASCII 字母和数字进行编码，也不会对这些 ASCII 标点符号进行编码： - _ . ! ~ * ' ( ) 。
	该方法的目的是对 URI 进行完整的编码，因此对以下在 URI 中具有特殊含义的 ASCII 标点符号，encodeURI() 函数是不会进行转义的：;/?:@&=+$,#
	
	提示：请注意 encodeURIComponent() 函数 与 encodeURI() 函数的区别之处，前者假定它的参数是 URI 的一部分（比如协议、主机名、路径或查询字符串）。因此 encodeURIComponent() 函数将转义用于分隔 URI 各个部分的标点符号。
	
2. parseInt(string, radix) 将字符串转为整数.
	说明
	当参数 radix 的值为 0，或没有设置该参数时，parseInt() 会根据 string 来判断数字的基数。
	举例，如果 string 以 "0x" 开头，parseInt() 会把 string 的其余部分解析为十六进制的整数。如果 string 以 0 开头，那么 ECMAScript v3 允许 parseInt() 的一个实现把其后的字符解析为八进制或十六进制的数字。如果 string 以 1 ~ 9 的数字开头，parseInt() 将把它解析为十进制的整数。
	
	注释：只有字符串中的第一个数字会被返回。
	
	注释：开头和结尾的空格是允许的。
	
	提示：如果字符串的第一个字符不能被转换为数字，那么 parseFloat() 会返回 NaN。	
	
## 原型和原型链
### 构造函数产生对象的过程
```
function Foo (name, age) {
   // this = {}； 将this绑定到一个新的obj
   // this新对象的`__proto__`的 
   // `constructor`属性绑定构造函数
   // this.__proto__ = Foo.prototype； 绑定原型链
	this.name = name;
	this.age = age;
	// return this； 返回obj
}
```	
* **注意**:若构造函数中没有返回值或返回值是**基本类型**(Number, String,Boolean),则返回新的实例对象;
* 若返回值是引用类型,则实际返回值为这个引用类型(实际上很少用到)

### 构造函数 - 扩展
* var a = {} 其实是 var a = new Object()的语法糖
* var a = [] 其实是 var a = new Array()的语法糖
* function Foo(){...} 其实是 var Foo = new Function()的语法糖
* 使用instanceof判断一个函数是否是一个变量的构造函数

### 原型规则和示例
* 所有的引用类型(数组、对象、函数),都具有对象的特性,即可以自由扩展属性(除了`null`)
* 所有引用类型(数组、对象、函数),都有一个`__proto__`属性,属性值是一个普通的对象(隐式原型)
* 所有的函数,都有一个prototype属性,属性值也是一个普通的对象(显式原型)
* 所有的引用类型(数组、对象、函数),`__proto__`属性值指向它的构造函数的`prototype`属性值

	```
	console.log(obj.__proto__ === Object.prototype) //true
	```
* 当试图得到一个对象的某个属性时,如果这个对象本身没有这个属性,那么会去它的`__proto__`(即它的构造函数的`prototype`)中寻找.

```
for (item in f){
	// 如果不用`hasOwnProperty` 则会遍历来自原型的属性
	if (f.hasOwnProperty(item)){
		console.log(item);
	}
}
```	

```
//封装一个DOM查询的例子 用原型链

//构造函数
function Elem(id){
	this.elem = document.getElementById(id);
}
//get set html
Elem.prototype.html = function(val){
	var elem = this.elem;
	if (val){
		elem.innerHTML = val;
		return this; //链式调用
	} else {
		return elem.innerHTML;
	}

}
//事件绑定
Elem.prototype.on = function(type, fn){
	 var elem = this.elem;
	 elem.addEventListener(type, fn);
	 return this;
}

var div1 = new Elem('div1');
div1.html('<p>hello word</p>');
div1.on('click',function () {
	alert('click');
})

```

## 作用域和闭包

### 执行上下文
* 全局: 变量定义, 函数声明 提升到最前面
* 函数: 变量定义, 函数声明, this, arguments 

### 变量提升和函数提升
* 函数声明和函数表达式的区别
* 变量提升用var声明的变量会提升到作用域的最前面此时并没有赋值(undefined)
* 函数提升用function来声明函数会提升到作用域的最前面

### this 运行时绑定,定义时无法确认

```
var a = {
  name: 'A'
  fn: function () {
  	console.log(this.name)
  }
}
a.fn() //this === a
a.fn.call({name: 'B'}) // this === {name: 'B'}
var fn1 = a.fn;
fn1() // this === window
```	
应用场景: 

* 作为构造函数执行
* 作为对象属性执行
* 作为普通函数执行
* call apply bind

### 作用域
* 全局作用域
* 函数作用域
* 块级作用域(es6)

### 创建10个`<a>`,点击弹出相应序号 (闭包应用)

```
function create () {
	var i,a;
	for (i = 0; i < 10; i++ ){
	 (function(i){
	 	a = document.createElement('a');
		a.innerHTML = 'a标签' + i + '<br>';
		a.addEventListener('click', function(e){
			e.preventDefault();
			alert(i);

		});
		document.body.appendChild(a);
	 })(i)
	}
}
```
```
//es6 写法
function create () {
	for (let i = 0; i < 10; i++ ){
	 	const a = document.createElement('a');
		a.innerHTML = 'a标签' + i + '<br>';
		a.addEventListener('click', function(e){
			e.preventDefault();
			alert(i);

		});
		document.body.appendChild(a);
	}
}
```

### caller 和 callee
* caller返回一个函数的引用,表示这个函数调用了当前的函数,如果由顶层调用则返回null
* callee是arguments的一个属性,指向当前函数本身

```
var a = function() {   
	alert(a.caller === b);   
}   
var b = function() {   
	a();   
}   
b(); // true
```

```
var a = function() {   
	alert(arguments.callee === a);    
} 
a(); // true
```

## DOM (Document Object Model)
### 数据结构 (tree)
### 本质
符合W3C标准的XML
### 常用API有哪些
* 获取DOM节点

```
var div1 = document.getElementById('div1');
var divList = document.getElementsByTagName('div');
console.log(divList.length);
console.log(divList[0]);

var containerList = document.getElementsByClassName('.container');//集合
var pList = document.querySelectorAll('p');//集合
var obj = document.querySelector("#id");
var obj = document.querySelector(".classname");
var obj = document.querySelector("div");
var el = document.body.querySelector("style[type='text/css'], style:not([type])");
```

```
var pList = document.querySelectorAll('p')
var p = pList[0];
console.log(p.style.width) // 获取样式
p.style.width = '100px';//修改样式
console.log(p.className)//获取class
p.className = 'p1' //修改class

//获取 nodeName 和 nodeType
console.log(p.nodeName); // P 大写
console.log(p.nodeType); // 1 元素节点 2 属性节点 3 TEXT

//Attribute
var pList = document.querySelectorAll('p')
var p = pList[0];
p.getAttribute('data-name');
p.setAttribute('data-name', 'imooc');
p.getAttribute('style');
p.setAttribute('style', 'font-size:30px')
```
```
var div1 = document.getElementById('div1');
//添加新的节点
var p1 = document.createElement('p');
p1.innerHTML = 'this is p1';
div1.appendChild(p1); //添加新创建的元素
//移动已有节点
var p2 = document.getElementById('p2')
div1.appendChild(p2);
var parent = div1.parentElement
var children = div1.childNodes //所有子节点包括TEXT
div1.removeChild(children[0]); 
```
### DOM节点的attr 和 property 有何区别?
* property是DOM中的属性，是JavaScript里的对象；
* attribute是HTML标签上的特性，它的值只能够是字符串；

## BOM (Browser Object Model)

### location
* location.href //整个url `http://www.baidu.com`
* location.protocol // `http:` or `https:`
* location.host // 域名
* location.port // 端口 http默认80 https443
* location.pathname // 路径 `/classindex.html`
* location.search // query `?oid=1231233`
* location.hash // hash `#page=1`

### navigator
* navigator.userAgent //判断浏览器类型,操作系统

### screen
* screen.width
* screen.height

### history
* history.forward()
* history.back()

## 事件冒泡
### 编写一个通用的事件绑定函数
```
function bindEvent(elem, type, selector, fn) {
	if (fn == null) {
		fn = selector;
		selector = null;
	}
	elem.addEventListener(type, function(e){
		var target ;
		if (selector) {
			target = e.target;
			if (target.matches(selector)){ //'a.btn'
				fn.call(target, e);
			}
		} else {
			fn.call(elem, e);
		}
	})
}
```

* 代理
* 阻止冒泡 e.stropPropagation();

## Ajax 
* XMLHttpRequest
* 状态码
* 跨域

### 编写一个ajax,不依赖第三方库
```
var xhr = new XMLHttpRequest();
xhr.open("GET", '/api', false) //false 表示异步
xhr.onreadystatechange = function () {
	// 0 未初始化还未调用send
	// 1 (载入) 已经调用send,正在发送
	// 2 (载入完成) send()执行完成,已经接收
	// 3 (交互) 正在解析响应内容
	// 4 (完成) 响应内容解析完成,可以在客户端调用

	if (xhr.readyState === 4) {
		if (xhr.status === 200) {
			alert(xhr.responseText);
		}
	}
}
xhr.send(nulll);
```

### 跨域问题
* 浏览器同源策略,协议、域名、端口,有一个不同就算跨域
* 跨域方法 JSONP CORS
* 三个可以跨域的标签 `<img src="xxxx">` `<link href="xxxxx">` `<script src="xxx">`

## 存储

### cookie
* 最大支持4k
* 只能存储字符串
* 每次请求都会携带
* `document.cookie = "xxxxx"` 获取和修改

### sessionStorage
* 最大支持5M
* 可以以key value存储`setItem(key,value)`和 `getItem(key)`;
* 浏览器关闭清空

### localStorage
* 最大支持5M
* 可以以key value存储
* 一般不会清空
* IOS safari隐藏模式下 localStorage.getItem 会报错


## 合并DOM插入

```
var listNode = document.getElementById('list')
var frag = document.createDocumentFragment();
var x, li
for (x = 0; x < 10; x++) {
	li = document.createElement("li");
	li.innerHTML = 'List item ' + x;
	frag.appendChild(li);
}

listNode.appendChild(frag);
```

## 性能优化
* 资源合并
* 静态资源缓存(浏览器缓存)
* CDN(bootcss)
* 后端渲染
* 懒加载
* 缓存DOM查询
* 减少DOM操作次数(合并DOM插入)
* 事件除颤(debounce)
* 尽早操作(DOMContentLoaded)

## 安全性
* XSS跨站请求攻击(escape转义字符)
* CSRF跨站请求伪造(增加验证)