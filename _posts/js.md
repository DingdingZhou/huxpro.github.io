* 带有 src 属性的 <script> 元素不应该在其 <script> 和 </script> 标签之间再包含额外的 JavaScript 代码。如果包含了嵌入的代码,则只会下载并执行外部脚本文件,嵌入的代码会被忽略。
* 如果想包含来自不同域的代码,则要么你是那个域的所有者,要么那个域的所有者值得信赖。
* 无论如何包含代码,只要不存在 defer 和 async 属性,浏览器都会按照 <script> 元素在页面中出现的先后顺序对它们依次进行解析。
* 一般应该把 <script> 元素放在页面最后,即主要内容后面, </body> 标签前面。
* defer属性的用途是表明脚本在执行时不会影响页面的构造,相当于告诉浏览器立即下载,但延迟执行。
* 把延迟脚本放在页面底部仍然是最佳选择
* 建议异步脚本不要在加载期间修改 DOM
* ECMAScript 中的一切(变量、函数名和操作符)都区分大小写
* 按照惯例,ECMAScript 标识符采用驼峰大小写格式,也就是第一个字母小写,剩下的每个单词的首字母大写
* ECMAScript 使用 C 风格的注释,包括单行注释和块级注释。
* ECMAScript 5 引入了严格模式(strict mode)的概念,要在整个脚本或函数中启用严格模式,可以在顶部添加如下代码,作为编译指示:"use strict";
* ECMAScript 中的语句以一个分号结尾;如果省略分号,则由解析器确定语句的结尾(不推荐),虽然语句结尾的分号不是必需的,但我们建议任何时候都不要省略它
* ECMAScript 的变量是松散类型的,所谓松散类型就是可以用来保存任何类型的数据。每个变量仅仅是一个用于保存值的占位符而已。
* 用 var 操作符定义的变量将成为定义该变量的作用域中的局部变量。如果在函数中使用 var 定义一个变量,那么这个变量在函数退出后就会被销毁,
* 省略 var 操作符可以定义全局变量,但这也不是我们推荐的做法
* ECMAScript 中有 5 种简单数据类型(也称为基本数据类型): Undefined 、 Null 、 Boolean 、 Number 、 String
* 1 种复杂数据类型 —— Object , Object 本质上是由一组无序的名值对组成的
* typeof 操作符用来检测给定变量的数据类型
* 即便未初始化的变量会自动被赋予 undefined 值,但显式地初始化变量依然是明智的选择。如果能够做到这一点,那么当 typeof 操作符返回 "undefined" 值时,我们就知道被检测的变量还没有被声明,而不是尚未初始化。
* 从逻辑角度来看, null 值表示一个空对象指针,而这也正是使用 typeof 操作符检测 null 值时会返回 "object" 的原因,
* 如果定义的变量准备在将来用于保存对象,那么最好将该变量初始化为 null 而不是其他值。这样一来,只要直接检查 null 值就可以知道相应的变量是否已经保存了一个对象的引用,
* undefined 值是派生自 null 值的,因此 ECMA-262 规定对它们的相等性测试要返回 true,尽管 null 和 undefined 有这样的关系,但它们的用途完全不同。
* 只要意在保存对象的变量还没有真正保存对象,就应该明确地让该变量保存 null 值,以与 undefined 区分。
* 可以对任何数据类型的值调用 Boolean() 函数,而且总会返回一个 Boolean 值。  

```
数据类型             转换为true的值                         转换为false的值

Boolean                 true                                 false
String              任何非空字符串                          "" (空字符串)
Number           任何非零数字值(包括无穷大)           0和 NaN (参见本章后面有关NaN的内容)
Object               任何对象                                  null
Undefined             n/a                                   undefined
```

* 永远不要测试某个特定的浮点数值
* 如果某次计算的结果得到了一个超出 JavaScript 数值范围的值,那么这个数值将被自动转换成特殊的 Infinity 值。
* NaN ,即非数值(Not a Number)是一个特殊的数值
* NaN 本身有两个非同寻常的特点。1.任何涉及 NaN 的操作(例如 NaN /10)都会返回 NaN; 2.NaN 与任何值都不相等,包括 NaN 本身。
* 把非数值转换为数值: Number() 、 parseInt() 和 parseFloat()
* 一元加操作符的操作与 Number() 函数相同。
* 不指定基数意味着让 parseInt() 决定如何解析输入的字符串,因此为了避免错误的解析,建议无论在什么情况下都明确指定基数。
* parseFloat() 只解析十进制值
* 用双引号表示的字符串和用单引号表示的字符串完全相同
* ECMAScript 中的字符串是不可变的,也就是说,字符串一旦创建,它们的值就不能改变。要改变某个变量保存的字符串,首先要销毁原来的字符串,然后再用另一个包含新值的字符串填充该变量,




要把一个值转换为一个字符串有两种方式。第一种是使用几乎每个值都有的 toString() 方法



在不知道要转换的值是不是 null 或 undefined 的情况下,还可以使用转型函数 String() ,这个
函数能够将任何类型的值转换为字符串。



对象可以通过执行 new 操作符后跟要创建
的对象类型的名称来创建。而创建 Object 类型的实例并为其添加属性和(或)方法,就可以创建自定
义对象



即在 ECMAScript 中,Object 类型是所有它的实例的基础。换句话说,
Object 类型所具有的任何属性和方法也同样存在于更具体的对象中



var o = new Object; // 有效,但不推荐省略圆括号

即在 ECMAScript 中,
(就像 Java 中的 java.lang.Object 对象一样) Object 类型是所有它的实例的基础。

Object 类型所具有的任何属性和方法也同样存在于更具体的对象中



1. 相等和不相等
ECMAScript 中的相等操作符由两个等于号( == )表示,如果两个操作数相等,则返回 true 。而不
相等操作符由叹号后跟等于号( != )表示,如果两个操作数不相等,则返回 true 。这两个操作符都会
先转换操作数(通常称为强制转型)
,然后再比较它们的相等性。





2. 全等和不全等
除了在比较之前不转换操作数之外,全等和不全等操作符与相等和不相等操作符没有什么区别。全
等操作符由 3 个等于号( === )表示,它只在两个操作数未经转换就相等的情况下返回 true


for-in 语句



虽然 ECMAScript 中的 switch 语句借鉴自其他语言,但这个语句也有自己的特色。首先,可以在
switch 语句中使用任何数据类型(在很多其他语言中只能使用数值)
,无论是字符串,还是对象都没有
问题。其次,每个 case 的值不一定是常量,可以是变量,甚至是表达式



switch 语句在比较值时使用的是全等操作符,因此不会发生类型转换(例如,
字符串 "10" 不等于数值 10)。








这个事实说明了 ECMAScript 函数的一个重要特点:命名的参数只提供便利,但不是必需的
在函数体内可以通过 arguments 对象来
访问这个参数数组,从而获取传递给函数的每一个参数。



这是因为 arguments 对象的长度是由传入的参数个数决定的,不是由定义函数时的命名
参数的个数决定的。



没有传递值的命名参数将自动被赋予 undefined 值。这就跟定义了
变量但又没有初始化一样




ECMAScript 中的所有参数传递的都是值,不可能通过引用传递参数。


如果在 ECMAScript 中定义了两个名字相同的函数,则该名字只属于后定义的函数



ECMAScript 变量可能包含两种不同数据类型的值:基本类型值和引用类型值。基本类型值指的是
简单的数据段,而引用类型值指那些可能由多个值构成的对象。



5 种
基本数据类型: Undefined 、 Null 、 Boolean 、 Number 和 String 。这 5 种基本数据类型是按值访问
的,



在操作对象时,实际上是在操作对象的引用而不是实际的对象。
为此,引用类型的值是按引用访问的 1 。




对于引用类型的值,我们可以为其添加属
性和方法,也可以改变和删除其属性和方法



我们并不是想知道某个值是对象,而是想知道它是什么类型的对象

ECMAScript
提供了 instanceof 操作符,其语法如下所示:
result = variable instanceof constructor



根据规定,所有引用类型的值都是 Object 的实例




每个执行环境都有一个
与之关联的变量对象(variable object)
环境中定义的所有变量和函数都保存在这个对象中






每个函数都有自己的执行环境。






标识符解析是沿着作用域链一级一级地搜索标识符的过程。搜索过程始终从作用域链的前端开始,
然后逐级地向后回溯,直至找到标识符为止






虽然执行环境的类型总共只有两种——全局和局部(函数),但还是有其他办法来延长作用域链。






JavaScript 没有块级作用域经常会导致理解上的困惑。在其他类 C 的语言中,由花括号封闭的代码
块都有自己的作用域

在使用 for 语句时尤其要牢记这一差异,




使用 var 声明的变量会自动被添加到最接近的环境中。


不声明而直接初始化变量是一个常见的错误做
法,因为这样可能会导致意外。






很明显,访问局部变量要比访问全局变量更快,因
为不用向上搜索作用域链




JavaScript 中最常用的垃圾收集方式是标记清除(mark-and-sweep)。








而优化内存占用的最佳方式,就是为执行
中的代码只保存必要的数据。一旦数据不再有用,最好通过将其值设置为 null 来释放其引用——这个
做法叫做解除引用(dereferencing)。这一做法适用于大多数全局变量和全局对象的属性。局部变量会在
它们离开执行环境时自动被解除引用,








解除引用的真正作用是让值脱离
执行环境,以便垃圾收集器下次运行时将其回收。







基本类型值在内存中占据固定大小的空间,因此被保存在栈内存中;








对象是某个特定引用类型的实例
新对象是使用 new 操作符后跟一个构造函数来创建的。
构造函数本身就是一个函数,只不过该函数是出于创建新对象的目的而定义的。







创建 Object 实例的方式有两种。第一种是使用 new 操作符后跟 Object 构造函数,
var person = new Object();
person.name = "Nicholas";
person.age = 29;


另一种方式是使用对象字面量表示法。对象字面量是对象定义的一种简写形式,目的在于简化创建
包含大量属性的对象的过程。

var person = {
name : "Nicholas",
age : 29
};

属性名会自动转换为字
符串


关于对象字面量语法,我们推
荐只在考虑对象属性名的可读性时使用



一般来说,访问对象属性时使用的都是点表示法,这也是很多面向对象语言中通用的语法。不过,
在 JavaScript 也可以使用方括号表示法来访问对象的属性。在使用方括号语法时,应该将要访问的属性
以字符串的形式放在方括号中


alert(person["name"]);
alert(person.name);
6
7
8
9
//"Nicholas"
//"Nicholas"


从功能上看,这两种访问对象属性的方法没有任何区别。但方括号语法的主要优点是可以通过变量
来访问属性



如果属性名中包含会导致语法错误的字符,或者属性名使用的是关键字或保留字,也可以使用方括
号表示法。






通常,除非必须使用变量来访问属性,否则我们建议使用点表示法。





但与其他语言不同的是,ECMAScript 数组的每一项可以保存任何类型的数据。也
就是说,可以用数组的第一个位置来保存字符串,用第二位置来保存数值,用第三个位置来保存对象






创建数组的基本方式有两种。第一种是使用 Array 构造函数,

var colors = new Array("red", "blue", "green");



创建数组的第二种基本方式是使用数组字面量表示法。

var
colors = ["red", "blue", "green"];





var values = [1,2,];
// 不要这样!这样会创建一个包含 2 或 3 项的数组


Array.isArray() 方法


而如果使用 join() 方法,则可以使用不同的分隔符来构建这个字符串。 join() 方
法只接收一个参数,即用作分隔符的字符串,然后返回包含所有数组项的字符串。



队列方法
push
shift


前段插入
unshift()




reverse() 和 sort(



reverse() 和 sort() 方法的返回值是经过排序之后的数组




splice() 的主要用途是向数组的中部插入项



indexOf() 和 lastIndexOf() 。这两个方法都接收
两个参数:要查找的项和(可选的)表示查找起点位置的索引




迭代方法




 every() :对数组中的每一项运行给定函数,如果该函数对每一项都返回 true ,则返回 true 。
 filter() :对数组中的每一项运行给定函数,返回该函数会返回 true 的项组成的数组。
 forEach() :对数组中的每一项运行给定函数。这个方法没有返回值。
 map() :对数组中的每一项运行给定函数,返回每次函数调用的结果组成的数组。
 some() :对数组中的每一项运行给定函数,如果该函数对任一项返回 true ,则返回 true 。




使用正则表达式字面量和使用 RegExp 构造函数创建的正则表达式不一样



ECMAScript 5 明确规定,使用正则表达式字面量必须像直接调用 RegExp 构造函数一样,每次都创
建新的 RegExp 实例。



正则表达式的第二个方法是 test() ,它接受一个字符串参数。在模式与该参数匹配的情况下返回
true ;否则,返回 false 。在只想知道目标字符串与某个模式是否匹配,但不需要知道其文本内容的
情况下,使用这个方法非常方便。因此, test() 方法经常被用在 if 语句中,



说起来 ECMAScript 中什么最有意思,我想那莫过于函数了——而有意思的根源,则在于函数实际
上是对象。每个函数都是 Function 类型的实例



由于函
数是对象,因此函数名实际上也是一个指向函数对象的指针,不会与某个函数绑定


另外,还要注意函数末尾有一个分号,就像声明其他变量时一样。

var sum = function(num1, num2){
return num1 + num2;
};


var sum = new Function("num1", "num2", "return num1 + num2"); // 不推荐

不过,这种语法对于理解“函数是对象,函数名是指针”的概念倒是非常直观的







解析器在向执行环
境中加载数据时,对函数声明和函数表达式并非一视同仁。解析器会率先读取函数声明,并使其在执行
任何代码之前可用(可以访问);至于函数表达式,则必须等到解析器执行到它所在的代码行,才会真
正被解释执行。



除了什么时候可以通过变量访问函数这一点区别之外,函数声明与函数表达式的语法其实是等价的




在函数内部,有两个特殊的对象: arguments 和 this






请读者一定要牢记,函数的名字仅仅是一个包含指针的变量而已。因此,即使是
在不同的环境中执行,全局的 sayColor() 函数与 o.sayColor() 指向的仍然是同一
个函数。





caller 。除了 Opera 的早期版本不支持,其他
浏览器都支持这个 ECMAScript 3 并没有定义的属性。这个属性中保存着调用当前函数的函数的引用,
如果是在全局作用域中调用当前函数,它的值为 null











在 ECMAScript 5 中, prototype 属性是不可枚举的,因此使用 for-in 无法发现



所有在全局作用域中定义的属性和函数,都是 Global 对象的属性




ECMA-262 把对象定义为:“无序属性的集合,其属性可以包含基本值、对象或者函数。
”



对象字面量成为创建这种对象的首选
模式

var person = {
name: "Nicholas",
age: 29,
job: "Software Engineer", 
sayName: function(){
alert(this.name);
} 
};





按照惯例,构造函数始终都应该以一个
大写字母开头,而非构造函数则应该以一个小写字母开头。








构造函数与其他函数的唯一区别,就在于调用它们的方式不同。


任何函数,只要通过 new 操作符来调用,那它就可以作为构造函数;







当在全局作用域中调用一个函数时, this 对象总是指向 Global 对象(在
浏览器中就是 window 对象)。




构造函数模式虽然好用,但也并非没有缺点。使用构造函数的主要问题,就是每个方法都要在每个
实例上重新创建一遍。

我们创建的每个函数都有一个 prototype (原型)属性,这个属性是一个指针,指向一个对象,
而这个对象的用途是包含可以由特定类型的所有实例共享的属性和方法。


。换句话说,不必在构造函数中定义对象实例的信息,而是
可以将这些信息直接添加到原型对象中





无论什么时候,只要创建了一个新函数,就会根据一组特定的规则为该函数创建一个 prototype
属性,这个属性指向函数的原型对象





每当代码读取某个对象的某个属性时,都会执行一次搜索,目标是具有给定名字的属性。搜索首先
从对象实例本身开始。如果在实例中找到了具有给定名字的属性,则返回该属性的值;如果没有找到,
则继续搜索指针指向的原型对象,在原型对象中查找具有给定名字的属性。如果在原型对象中找到了这
个属性,则返回该属性的值。




这种构造函数与原型混成的模式,是目前在 ECMAScript 中使用最广泛、认同度最高的一种创建自
定义类型的方法。可以说,这是用来定义引用类型的一种默认模式。





稳妥构造函数模式提供的这种安全性,使得它非常适合在某些安全执行环



ECMAScript 中描述了原型链的概念,并将原型链作为实现继承的主要方法。其基本思想是利用原
型让一个引用类型继承另一个引用类型的属性和方法



闭包是指有权访问另一个
函数作用域中的变量的函数。



后台的每个执行环境都有一个表示变量的对象——变量对象





作用域链本质上是一个指向变量对象的指针列表,它只
引用但不实际包含变量对象。





在另一个函数内部定义的函数会将包含函数(即外部函数)的活动对象添加到它的作用域链中





作用域链的这种配置机制引出了一个值得注意的副作用,即闭包只能取得包含函数中任何变量的最
后一个值。别忘了闭包所保存的是整个变量对象,而不是某个特殊的变量




在全局函数中, this 等于 window ,而当函数被作为某个对象的方法调用时, this 等
于那个对象


匿名函数的执行环境具有全局性,因此其 this 对象通常指向 window 1 。






JavaScript 从来不会告诉你是否多次声明了同一个变量;遇到这种情况,它只会对后续的声明视而不
见(不过,它会执行后续声明中的变量初始化)
。


(function(){
//这里是块级作用域
})();
以上代码定义并立即调用了一个匿名函数

将函数声明包含在一对圆括号中,表示它实际上是一个
函数表达式

紧随其后的另一对圆括号会立即调用这个函数


理解:用变量代替函数名




任何在函数中定义的变量,都可以认为是私有变量,因为不能在函数的外部访问这些变量。






按照惯例,JavaScript 是以对象字面量的方式来创建单例对象的。






在浏览器中, document 对象是 HTMLDocument (继承
自 Document 类型)的一个实例,表示整个 HTML 页面。




作用域扩展
<form method="post">
<input type="text" name="username" value="">
<input type="button" value="Echo Username" onclick="alert(username.value)">
</form>





使用 DOM0 级方法指定的事件处理程序被认为是元素的方法。因此,这时候的事件处理程序是在
元素的作用域中运行;换句话说,程序中的 this 引用当前元素




















































