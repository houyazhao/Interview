# Interview
### 1、iframe有那些缺点？
- iframe会阻塞主页面的Onload事件；
- 搜索引擎的检索程序无法解读这种页面，不利于SEO;
- 会影响页面的并行加载。

### 2、盒子模型你是怎么理解的？
#### 盒子模型有两种，W3C和IE盒子模型
- W3C定义的盒子模型包括margin、border、padding、content ，元素的width=content的宽度
- IE盒子模型与W3C的盒子模型唯一区别就是元素的宽度，元素的width=content+padding+border
