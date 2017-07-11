# 样式篇
## jQuery 对象转为 DOM
* 利用数组下标的方式读取到jQuery中的DOM对象

	```
	var $div = $('div') //jQuery对象
	var div = $div[0] //转化成DOM对象
	div.style.color = 'red' //操作dom对象的属性
	```
* 通过jQuery自带的get()方法

	```
	var $div = $('div') //jQuery对象
	var div = $div.get(0) //通过get方法，转化成DOM对象
	div.style.color = 'red' //操作dom对象的属性
	```	
## DOM 对象转化为jQuery对象
* 通过$(dom)方法将普通的dom对象加工成jQuery对象之后，我们就可以调用jQuery的方法了	

	```
	var div = document.getElementsByTagName('div'); //dom对象
	var $div = $(div); //jQuery对象
	var $first = $div.first(); //找到第一个div元素
	$first.css('color', 'red'); //给第一个元素设置颜色
	```
	
## jQuery 选择器
* id选择器 `$('#imoc')`	
* class选择器 `$('.imoc')`
* 元素选择器`$('div')`
* \*选择器(全选择器) `$('*')`
* 子选择器 `$('div > p')`
* 后代选择器 `$('div p')`
* 相邻兄弟选择器 `$(".prev + div")` `.prev` 后面第一个`div`
* 一般兄弟选择器 `$(".prev ~ div")` `.prev` 后面所有`div`

## jQuery 筛选选择器
|选择器|描述|
|:------------- |:---------------:| 
|`$(':first')`|匹配第一个元素|
|`$(':last')`|匹配最后一个元素|
|`$(':not(selector)')`|选择所有元素并去除不匹配给定的选择器元素|
|`$(':eq(index)')`|在匹配的集合中选择索引值为index的元素|
|`$(':gt(index)')`|匹配大于索引值的元素|
|`$(':lt(index)')`|匹配小于索引值的元素|
|`$(':even')`|选择索引值为偶数的元素,从0开始计数|
|`$(':odd')`|选择索引值为奇数的元素,从0开始计数|
|`$(':header')`|选择所有标题元素,h1,h2,h3|
|`$(':lang(language)')`|选择指定语言的所有元素|
|`$(':root')`|选择该文档的根元素|
|`$(':animated')`|选择正在执行动画效果的元素|
|`$(':contains(text)')`|选择所有包含指定文本的元素(可以是子元素包含指定文本)|
|`$(':parent')`|选择所有含有子元素或者文本的元素|
|`$(':empty')`|没有子元素的元素(包括文本节点)|
|`$(':has(selector)')`|选择至少包含一个匹配指定选择器的元素的容器|
|`$(':visible')`|选择所有显式的元素|
|`$(':hidden')`|选择所有隐藏的元素|

## jQuery 属性选择器
|选择器|描述|
|:------------- |:---------------:| 
|`$("[attribute|='value']")`|选择指定属性值等于给定字符串或以该文字串为前缀(该字符串后跟一个连字符`-`)的元素|
|`$("[attribute*='value']")`|选择指定属性具有包含一个给定的子字符串的元素(选择给定的属性是以包含某些值的元素)|
|`$("[attribute~='value']")`|选择指定属性用空格分隔的值中包含一个给定值的元素|
|`$("[attribute='value']")`|选择指定属性时给定值的元素|
|`$("[attribute!='value']")`|选择不存在指定属性,或者指定的属性值不等于给定值的元素|
|`$("[attribute^='value']")`|选择指定属性是以给定字符串开始的元素|
|`$("[attribute$='value']")`|选择指定属性是以给定值结尾的元素,这个比较区分大小写|
|`$("[attribute]")`|选择所有具有指定属性的元素,该属性可以是任何值|
|`$("[attribute1][attribute2]")`|选择匹配所有指定的属性筛选器的元素|

## 子元素筛选选择器
|选择器|描述|
|:------------- |:---------------:| 
|`$(':first-child')`|选择所有父级元素下的第一个子元素|
|`$(':last-child')`|选择所有父级元素下的最后一个子元素|
|`$(':only-child')`|选择所有父级元素下唯一的子元素|
|`$(':nth-child(n)')`|选择所有父级元素的第n个子元素|
|`$(':nth-last-child(n)')`|选择所有父级元素的第n个子元素,从后往前计数|

## 表单元素选择器
|选择器|描述|
|:------------- |:---------------:| 
|`$(':input')`|所有input,textarea,select和button|
|`$(':text')`|所有文本框|
|`$(':password')`|所有密码框|
|`$(':radio')`|所有单选按钮|
|`$(':checkbox')`|所有复选框|
|`$(':submit')`|所有提交按钮|
|`$(':image')`|所有图像域|
|`$(':reset')`|所有重置按钮|
|`$(':button')`|所有按钮|
|`$(':file')`|所有文件域|

## 表单对象属性选择器

|选择器|描述|
|:------------- |:---------------:| 
|`$(':enabled')`|选取可用的表单元素|
|`$(':disabled')`|选取不可用的表单|
|`$(':checked')`|选取被选中的`<input>`元素|
|`$(':selected')`|选取被选中的`<option>`元素|

## DOM操作
* `.attr()` 和 `.removeAttr()` 获取、添加、删除attribute
* `.html()` 和 `.text()` get set html text
* `.val()` 处理表单元素的value
* `.hasClass()` `.addClass()` `.removeClass` `.toggleClass(className)` 判断、添加、删除Class
* `.css(propertyName, value)` 添加样式
* `$container.append($child)` 容器添加子节点到末尾
* `$child.appendTo($container) 子节点添加到容器
* `$(ele).before(content)` `$(ele).after(content)` 前面插入html, 后面插入html
* `.prepend($child)` `.prependTo($container)`  容器添加子节点到前面
* `.insertBefore($ele)` `.insertAfter($ele)`  插入到元素前面/后面
* `.empty()` 移除所有子元素包括文本
* `.remove()` 将元素自身及其子元素移除
* `.detach()` 从当前页面移除该元素,但保留这个元素的内存模型对象(包括事件) 
* `$('div').clone()` // 只克隆结构,事件丢失 `$('div').clone(true)` // 结构事件都克隆
* `.replaceWith(newContent)` 用提供的content替换集合中所有匹配的元素并返回被删除元素的集合
* `.replaceAll(selector)` 用集合的匹配元素替换每个符合selector的元素
* `$('p').wrap('<div></div>')` 给p外层包裹div 只针对单个元素, 多个用`wrapAll('<div></div>')`
* `$('p').unwrap()` 把p外部包裹元素删除
* `$('p').wrapInner('<div></div>')` 给p内部包裹div
* `$(ul).parent(selector)` 查找符合条件的父级节点
*  `$(ul).parents(selector)` 会一级一级向上查找到根节点返回一个符合条件的父级节点集合
*  `$("div").closet("li')` 会一级一级向上寻找直到找到一个符合条件的父级节点
*  `$('.item-2').next(':first')` 可接筛选选择器 紧邻的后一个元素
*  `$('.item-2').next(':first')` 可接筛选选择器 紧邻的前一个元素
*  `$('.item-2').siblings(':first')` 可接筛选选择器 所有同辈元素
*  `$('li').add('p')` 用来创建一个新的jQuery对象 ，元素添加到匹配的元素集合中
* `.each()` 遍历jquery集合

	```
    $("li").each(function(index, element) {
     index 索引 0,1
     element是对应的li节点 li,li
     this 指向的是li
	})
	```
* triggerHandler与trigger的用法是一样的, triggerHandler不会触发浏览器的默认行为,
* .trigger() 会影响所有与 jQuery 对象相匹配的元素，而 .triggerHandler() 仅影响第一个匹配到的元素
* 使用 .triggerHandler() 触发的事件，并不会在 DOM 树中向上冒泡。 如果它们不是由目标元素直接触发的，那么它就不会进行任何处理
* 与普通的方法返回 jQuery 对象(这样就能够使用链式用法)相反，.triggerHandler() 返回最后一个处理的事件的返回值。如果没有触发任何事件，会返回 undefined	

## DOM 遍历
* `$("div").children(".selected")` 查找合集里面的第一级子元素，此时可以用children()方法。这里需要注意：`.children(selector)` 方法是返回匹配元素集合中每个元素的所有子元素
* `$("div").find(".selected")` find查找范围包括子节点的所有后代节点

## jQuery 动画
* `hide()` `show()` `toggle()`
* `slideDown()` `slideUp()` `slideToggle()`
* `fadeIn()` `fadeOut()` `fadeToggle()` `fadeTo(duration, opacity, callback)`
*  `.animate( properties ,[ duration ], [ easing ], [ complete ] )`
*  `.animate( properties, options )`

	```
	.animate({
	    left: 50, 
	    width: '50px'   
	    opacity: 'show',  
	    fontSize: "10em",
	}, 500);
	```

	```
	$('#elem').animate({
	    width: 'toggle',  
	    height: 'toggle'
	  }, {
	    duration: 5000,
	    specialEasing: {
	      width: 'linear',
	      height: 'easeOutBounce'
	    },
	    complete: function() {
	      $(this).after('<div>Animation complete.</div>');
	    }
	  });
	```

## 数据存储
* `$.data(element, key, value)`
* `$(element).data(key, value)`
* `$(element).data(key)`
* `$(element).removeData(key)`

## JQuery 核心
* `$.each(array | object, callback)`
* `$.inArray( value, array ,[ fromIndex ] )` 返回index
* `$.trim()`
* `$(a).get(1)` 获取第二个元素
* `$("li").index($("#test2"))  //结果:1`

	```
	<ul>
	    <a></a>
	    <li id="test1">1</li>
	    <li id="test2">2</li>
	    <li id="test3">3</li>
	</ul>
	```
	
## JQuery AJAX
* `$.load(url,[data],[callback])`
* `$.getJSON(url,[data],[callback])`
* `$.getScript(url,[callback])` 异步加载js并执行
* `$.get(url,[callback])`
* `$.post(url,[data],[callback])`
* `$(selector).serialize()`
* `$.ajax([settings])`

	```
	$.ajax({
	    url: 'data/action',
	    data: { num: $("#txtNumber").val() },
	    dataType: 'text',
	    success: function (data) {
	        $("ul").append("<li>你输入的<b>  "
	        + $("#txtNumber").val() + " </b>是<b> "
	        + data + " </b></li>");
	    }
	});
	```
* `$.ajaxSetup([options])` 可以设置ajax全局默认选项

## 其他
* `$.support.boxModel` 检测浏览器是否属于标准的w3c盒子模型。IE模型宽高包括padding 和 border
* `$.isEmptyObject(obj);`  检测一个对象的内容是否为空
* `$.isPlainObject(obj)` 能检测对象是否为通过{}或new Object()关键字创建的原始对象
* `$.contains (container, contained);` 检查包含关系
* `$. param (obj);` 序列化对象,序列化为queryParameter
* `$. extend(obj)` 自定义jquery方法
* `$.extend (obj1,obj2,…objN); ` 对象扩展