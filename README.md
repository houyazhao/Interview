# Interview
### 1、iframe有那些缺点？
- iframe会阻塞主页面的Onload事件；
- 搜索引擎的检索程序无法解读这种页面，不利于SEO;
- 会影响页面的并行加载。

### 2、盒子模型你是怎么理解的？
#### 盒子模型有两种，W3C和IE盒子模型
- W3C定义的盒子模型包括margin、border、padding、content ，元素的width=content的宽度
- IE盒子模型与W3C的盒子模型唯一区别就是元素的宽度，元素的width=content+padding+border

#### 3、元素定位有哪些？
position为元素定位属性，包含 absolute绝对定位、fixed  固定定位（老IE6不支持）、relative相对定位、static

#### 4、样式导入有哪些方式？
- link
```
<link href="index.css" rel="stylesheet">
```
- import
```
<style type="text/css">  
@import "index.css";  
</style> 
```
不同点
- link除了引用样式文件，还可以引用图片等资源文件，而import只引用样式文件
- 兼容性不同，link不存在兼容性的问题，import在IE5以上支持，是css2.1新增的
- link引用CSS时，在页面载入时同时加载；@import需要页面网页完全载入以后加载

#### 5、::before 和:before有什么区别？
相同点
- 都可以用来表示伪类对象，用来设置对象前的内容
- :befor和::before写法是等效的
不同点
- :befor是Css2的写法，::before是Css3的写法
- :before的兼容性要比::before好 ，不过在H5开发中建议使用::before比较好
```
.test:hover::before { /* 这时animation和transition才生效 */ }  
```

#### 6、如何居中一个元素（正常、绝对定位、浮动元素）?
#### 7、清除浮动
.clearfix{zoom:1;}
.clearfix:after{display:block;clear:both;content:"";visibility:hidden;height:0}

#### 8、JavaScript中如何翻转一个字符串？
```
//str=hello  
  function reverseString(str) {   
      return str.split('').reverse().join('');;  
  }  
```
#### 9、怎样创建、添加、移除、移动、和查找节点?
createElement()
parentNode.removeChild(childNode)
parentNode.replaceChild(newChild,oldChild);//替换元素
parentNode.insertBefore(newChild,refChild)//在refChild前插入节点
parentNode.appendChild(childNode)

#### 10、事件是什么？如何阻止事件冒泡？
##### 事件是什么？ 
事件用于监听浏览器的操作行为，浏览器触发动作时被捕捉到而调用相应的函数。
##### 事件执行三个阶段
- 事件捕获阶段 
- 处于目标阶段
- 事件冒泡阶段
捕获型事件是自上而下，而冒泡型事件是自下而上的，而我们程序员通常要做的就是第二阶段，完成事件的动作。而第一、三阶段由系统封装自动调用完成。
冒泡阻止
event.stopPropagation()
IE浏览器
event.cancelBubble = true; 
阻止默认事件
e.preventDefault(); 


#### 11、谈一下Jquery中的bind ，on的区别？
##### bind：把事件绑定到每一个匹配的元素上，主要特点
1.兼容性比较好
2.绑定事件到所有选出来的元素上
3.不会绑定事件到动态添加的那些元素上
4.当元素很多时，会出现效率问题，特别是嵌套层次比较深的元素。

##### On：是jQuery1.7中新增的，前面的三种方法都是依赖on方法来实现的。，主要特点：
1.事件的添加和卸载都要是通过on来实现的，提供一种统一的事件处理方法。
2.增加了使用的难度，对于不熟悉on的使用的，很有可能就勿用，导致性能下降。


#### 12、JSON 格式是什么？你了解吗？
##### JSON是什么
JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。它是基于javascript的一个子集。数据格式简单, 易于读写, 占用带宽小。是前后台数据交互最常见的一种数据格式。
##### 数据格式转换
1.JSON字符串转换为JSON对象:
  var obj =eval('('+ str +')');
  var obj = JSON.parse(str);

2.JSON对象转换为JSON字符串：
  var last=JSON.stringify(obj);

3.数组转json字符串
  var array=[1,2,3,4];
  JSON.stringify($(array));

4.json字符串转数组，使用jQuery
  $(JSON.parse('{"0":1,"1":2,"2":3,"length":3}')); 


#### 13、原型是什么？原型链是什么？

##### 原型是什么？
在JavaScript中原型是一个prototype对象，用于表示类型之间的关系。

##### 原型链是什么？
对象之间的继承关系，在JavaScript中是通过prototype对象指向父类对象，直到指向Object对象为止，这样就形成了一个原型指向的链条，专业术语称之为原型链。

```
var Person = function(){this.age="匿名"};  
var Student = function(){};  
//创建继承关系,prototype执行Person的一个实例对象  
Student.prototype=new Person();
```

#### 14、什么是闭包，为什么要用它？
##### 闭包是什么
闭包是就是函数中的函数，里面的函数可以访问外面函数的变量，外面的变量的是这个内部函数的一部分。
```
<script>  
    function  outer(){  
        var num=0;//内部变量  
       return  function add(){//通过return返回add函数，就可以在outer函数外访问了。  
            num++;//内部函数有引用，作为add函数的一部分了  
           console.log(num);  
        };  
    }  
    var func1=outer();//  
    func1();//实际上是调用add函数， 输出1  
    func1();//输出2  
    var func2=outer();  
    func2();// 输出1  
    func2();// 输出2  
</script>
```

##### 闭包的作用
1.使用闭包可以访问函数中的变量。
2.可以使变量长期保存在内存中，生命周期比较长。

#### 15、Ajax 是什么?
Ajax 是一种异步请求数据的一种技术，对于改善用户的体验和程序的性能很有帮助。

#### 16、JavaScript有几种类型的值？你能画一下他们的内存图吗？

##### 两大类：
栈：原始数据类型（Undefined，Null，Boolean，Number、String）
堆：引用数据类型（对象、数组和函数）

##### 区别：
两种类型的区别是：存储位置不同；
- 原始数据类型直接存储在栈(stack)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；
- 引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定,如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体

#### 17、谈谈你对this的理解
##### this的指向
this表示当前对象，this的指向是根据调用的上下文来决定的，默认指向window对象，指向window对象时可以省略不写，例如：
```
 this.alert() <=> window.alert()<=> alert(); 
```
##### 调用的上下文环境包括全局和局部
全局环境就是在<script></script>里面，这里的this始终指向的是window对象
局部环境
1）在全局作用域下直接调用函数，this指向window
```
function func(){  
 console.log(this) ;//this指向的还是window对象  
}  
func();  
```
2）对象函数调用，哪个对象调用就指向哪个对象
```
<input type="button"id="btnOK" value="OK">  
<script>  
varbtnOK=document.getElementById("btnOK");  
btnOK.onclick=function(){  
console.log(this);//this指向的是btnOK对象  
}  
</script>  
```
3）使用 new 实例化对象，在构造函数中的this指向实例化对象。
```
var Show=function(){  
    this.myName="Mr.Cao";   //这里的this指向的是obj对象  
}  
var obj=new Show();  
```
4）使用call或apply改变this的指向
```
var Go=function(){  
     this.address="深圳";  
}  
var Show=function(){  
     console.log(this.address);//输出 深圳  
}  
var go=new Go();  
Show.call(go);//改变Show方法的this指向go对象 
```
#### 18、同步和异步有什么区别？
##### 同步的概念
同步，一种线性执行的方式，执行的流程不能跨越。一般用于流程性比较强的程序，我们做的用户登录功能也是同步处理的，必须用户通过用户名和密码验证后才能进入系统的操作。
#### 异步的概念
异步，是一种并行处理的方式，不必等待一个程序执行完，可以执行其它的任务。在程序中异步处理的结果通常使用回调函数来处理结果。在JavaScript中实现异步的方式主要有Ajax和H5新增的Web Worker。

#### 19、谈谈你对模块化开发的理解？
##### 什么是模块化
所谓的模块化开发就是封装细节，提供使用接口，彼此之间互不影响，每个模块都是实现某一特定的功能。模块化开发的基础就是函数 

#### 20、call() 和 apply() 的区别？
相同点：两个方法产生的作用是完全一样的，都用来改变当前函数调用的对象。
不同点：调用的参数不同，比较精辟的总结：
```
foo.call(this,arg1,arg2,arg3) == foo.apply(this, arguments)==this.foo(arg1, arg2, arg3)
```

1.call的使用

语法
call([thisObj[,arg1[, arg2[, [,.argN]]]]])
参数
thisObj  可选项。将被用作当前对象的对象。
arg1,arg2, , argN  可选项。将被传递方法参数序列。
说明
call 方法可以用来代替另一个对象调用一个方法。call 方法可将一个函数的对象上下文从初始的上下文改变为由 thisObj 指定的新对象。如果没有提供 thisObj 参数，那么 Global 对象被用作 thisObj。

```
<input id="myText">  
<script>  
    function Obj()  
    {  
       this.value="对象！";  
    }  
    varvalue="global 变量";  
    function Fun1(a,b){  
       alert(this.value);  
    }  
    window.Fun1();   //global 变量  
    Fun1.call(window,1,2);  //global 变量  
    Fun1.call(document.getElementById('myText'));  //input text  
    Fun1.call(new Obj());   //对象！  
</script>  
```

2.apply()
apply与call的功能几乎一样，第一个参数意义都一样，只是第二个参数有点不同apply传入的是一个参数数组，也就是将多个参数组合成为一个数组传入，call从第二个参数开始，依次传值给调用函数的参数 
```
function print(a, b, c, d){  
  alert(a + b + c + d);  
}  
functionexample(a, b , c , d){  
 //用call方式借用print,参数显式打散传递  
 print.call(this, a, b, c, d);  
 //用apply方式借用print, 参数作为一个数组传递,  
 //这里直接用JavaScript方法内本身有的arguments数组  
 print.apply(this, arguments);  
 //或者封装成数组  
 print.apply(this, [a, b, c, d]);  
}  
//下面将显示”智学无忧”  
example("智" , "学" , "无", "忧");  
```


#### 21、["1", "2", "3"].map(parseInt) 答案是多少？
map方法的使用 
语法
array.map(callback[,thisArg]);
对数组的重新映射。将数组的各个元素依次传入到回调函数callback，回调函数返回的结果依次替换原数组对应的元素。
回调函数callback 会被自动传入三个参数：数组元素，元素索引，原数组本身。
map(function(T=,number=, Array.<T>=))
T:表示元素
number:元素的下标
Array.<T>：表示数组原始值
 
parseInt()方法的使用
语法
parseInt(s,radix)解析一个字符串，并返回一个整数。
参数
s：表示字符串
radix：表示其它进制转十进制的基数，范围在2-36，不在这个范围的返回NaN。该参数可以省略或为0，这种情况会根据字符串的开头来判断基数，规则如下：
题目的结果推导
```
["1","2", "3"].map(parseInt)
[0]=parseInt(“1”,0);//1*100=1*1=1
[1]=parseInt(“2”,1);//radix不在2~36的返回NaN
[2]=parseInt(“3”,2);//二进制数没有3，只有0 1 ，所以NaN 
```
所以最终的结果是 [1,NaN,NaN]


#### 22、eval是做什么的？
##### eval()的作用
把字符串参数解析成js代码并运行，并返回执行的结果；
```
eval("2+3");//执行加运算，并返回运算值。  
eval("var age=10");//声明一个age变量  
```
##### eval的作用域
```
function a(){  
 eval("var x=1"); //等效于 var x=1;  
 console.log(x); //输出1  
}  
a();  
console.log(x);//错误 x没有定义 
```
说明作用域在它所有的范围内容有效
##### 注意
应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。
##### 其它作用
由JSON字符串转换为JSON对象的时候可以用eval，例如
```
var json = "{name:'Mr.CAO',age:30}";  
var jsonObj = eval("("+json+")");  
console.log(jsonObj);  
```


#### 23、new操作符具体干了什么呢?
```
var Func = function(){};  
var func = new Func(); 
```
##### new共经过了4几个阶段
1、创建一个空对象
```
var obj=new Object();  
```
2、设置原型链
```
obj.__proto__= Func.prototype;  
```
3、让Func中的this指向obj，并执行Func的函数体。
```
var result =Func.call(obj); 
```
4、判断Func的返回值类型：
如果是值类型，返回obj。如果是引用类型，就返回这个引用类型的对象。
```
if (typeof(result) == "object"){  
  func=result;  
}  
else{  
    func=obj;;  
}  
```

#### 24、CSS3有哪些新特性？
1.CSS3的选择器
1）E:last-child 匹配父元素的最后一个子元素E。
2）E:nth-child(n)匹配父元素的第n个子元素E。 
3）E:nth-last-child(n) CSS3 匹配父元素的倒数第n个子元素E。
2. 圆角
3.阴影（Shadow）
4.CSS3 的渐变效果 
5.css弹性盒子模型
6. CSS3制作特效

#### 25、html5有哪些新特性？
##### H5新特性
增强了图形渲染、影音、数据存储、多任务处理等处理能力主要表现在
1)  绘画 canvas;
2)  本地离线存储 localStorage
3)  sessionStorage的数据在浏览器关闭后自动删除;操作参考localStorage
4)  用于媒介回放的 video和 audio 元素;
5)  语意化更好的内容元素，比如article、footer、header、nav、section;
6)  表单控件，calendar、date、time、email、url、search;
7)  Geolocation 地理定位

#### 26、请描述一下 cookies，sessionStorage 和 localStorage 的区别？
相同点：都存储在客户端
不同点：
1.存储大小
cookie数据大小不能超过4k。
sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。
2.有效时间
localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
sessionStorage  数据在当前浏览器窗口关闭后自动删除。
cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭
3. 数据与服务器之间的交互方式
cookie的数据会自动的传递到服务器，服务器端也可以写cookie到客户端
sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。

cookie的表示方式示例
```
var name = "jack";  
var pwd = "123";  
var now = new Date();  
now.setTime(now.getTime() +1 * 24 * 60 * 60 * 1000);//转毫秒  
var path = "/";//可以是具体的网页  
document.cookie = "name=" + name + ";
expires=" + now.toUTCString() + ";
path=" + path;//姓名  
document.cookie= "pwd=" + pwd + ";
expires=" + now.toUTCString()+ ";
path=" + path; //密码  

var data = document.cookie;//获取对应页面的cookie  
//解析cookie
//方式1：截取字符串
function getKey(key) {  
    var data = document.cookie;  
    var findStr = key + "=";  
    //找到key的位置  
    var index = data.indexOf(findStr);  
    if (index == -1)  
        return null;  
    var subStr = data.substring(index +findStr.length);  
    var lastIndex = subStr.indexOf(";");  
    if (lastIndex == -1) {  
        return subStr;  
 } else {  
        return subStr.substring(0,lastIndex);  
 }  
}  
//方式2：使用正则表达式+JSON
function getKey(key) {  
    return JSON.parse("{\"" +document.cookie.replace(/;\s+/gim, "\",\"").replace(/=/gim, "\":\"") + "\"}")[key];  
}  
//清除cookie
var name = null;  
var pwd = null;  
var now = new Date();  
var path = "/";//可以是具体的网页  
document.cookie= "name=" + name + ";expires=" + now.toUTCString()+ ";path=" + path;//姓名  
document.cookie = "pwd=" + pwd + ";expires=" + now.toUTCString()+ ";path=" + path; //密码  
```

#### 27、页面渲染原理是什么？
##### 渲染引擎
不同的浏览器有不同的渲染引擎，对于渲染引擎的使用总结如下：
Trident(MSHTML)内核：IE,MaxThon,TT,The World,360,搜狗浏览器等
Gecko内核：Netscape6及以上版本，FF,MozillaSuite/SeaMonkey等
Presto内核：Opera7及以上
Webkit内核：Safari,Chrome等

##### 渲染主流程
第一步：渲染引擎开始解析html，根据标签构建DOM节点
第二步：根据css样式构建渲染树，包括元素的大小、颜色，隐藏的元素不会被构建到该树中。
第三步：根据css样式构建布局树，主要是确定元素要显示的位置。
第四步：根据前面的信息，绘制渲染树。

#### 28、你了解跨域请求吗？
##### 什么是跨域请求
基于JavaScript的安全，JavaScript同源策略要求一个网站不能调用其它网站的js对象。构成跨域的条件就是一个页面的URL**协议、域名、端口**与另一个页面的URL只要有一个不同就构成了跨域请求。
##### 特别注意两点：
第一：如果是协议和端口造成的跨域问题“前台”是无能为力的，
第二：在跨域问题上，域仅仅是通过“URL的首部”来识别而不会根据域名对应的IP地址是否相同来判断。
“URL的首部”可以理解为“协议, 域名 和 端口 必须匹配”。

##### （一）JSONP
无法发送post请求
```
<script>  
    $.ajax({  
        url:"http://localhost:3000/users/userlist",  
        type:"get",  
        dataType:"jsonp",  
        success:function(e){  
            console.log(e);  
        }  
    });  
</script>  
```

##### （二）在服务器端设置同源策略地址
在响应头上添加Access-Control-Allow-Origin属性，指定同源策略的地址。同源策略默认地址是网页的本身。
#####（三）H5新特性postMessage


#### 29、页面优化有哪些方法
一、减少操作量
尽量减少 HTTP 请求
1) 合并文件，比如把多个 CSS 文件合成一个； 
2) CSS Sprites 利用 CSS background 相关元素进行背景图绝对定位； 
 不要在 HTML 中使用缩放图片
缩放图片并没有减少图片的容量，只是控制了图片的大小。
Image压缩
使用工具对图片进行压缩，保证质量的同时减少了图片的大小。
减少对DOM的操作
减少对DOM的操作，减少页面的重绘。
二、提前做加载操作
对域名进行预解析
例如京东的做法
<link rel="dns-prefetch" href="//misc.360buyimg.com" />  
预载入组件或延迟载入组件
把 CSS 放到代码页上端 
CSS 放到最顶部，浏览器能够有针对性的对 HTML 页面从顶到下进行解析和渲染。
使用 new Image对象，对图片进行缓存
三、提升并行加载
切分组件到多个域 ，提升服务器的响应能力

四、JavaScript和CSS优化
从页面中剥离 JavaScript 与 CSS
剥离后，能够有针对性的对其进行单独的处理策略，比如压缩或者缓存策略。
精简 JavaScript 与 CSS 
使用工具压缩JavaScript和CSS文件
脚本放到 HTML 代码页底部
减少对页面的阻塞。
五、异步加载
  使用Ajax实现异步加载，例如，滚动页面加载后面的内容，这种也比较常见。
  





