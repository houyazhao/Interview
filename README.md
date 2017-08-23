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
#### 7、


