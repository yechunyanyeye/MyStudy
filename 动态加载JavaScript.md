 ### 动态加载JavaScript

* 创建动态脚本有两种方式: 插入外部文件   ,   直接插入` javascript` 代码
* 插入外部文件
  * 写标签 ,设置` type` 属性 ,利用` src` 插入代码
* 直接插入` javascript` 代码
  * 写标签,设置`type`属性 ,` js`代码作为文本节点 ,再插入标签中 (IE报错)
  * 针对` IE` , 写标签 , 设置` type` 属性 , 直接将` js` 代码转化为字符串 , 然后赋给` text` 属性 (Safari浏览器不兼容 , 用` try-catch` 来解决)
  * 当使用上述2种方法 , 代码性能会下降 . 



##### 如何判断` javascript`代码加载并完成呢 ?

script标签有两个属性:

* ` onload`  现代浏览器
* ` onreadystatechange `   IE
* 函数在JavaScript加载完后调用  , `readyState` 属性 发生变化,调用函数



##### 框架

* `Jquery`  框架里面的`  getScript() `函数
  * 2个参数,第一个是字符串,表示`js`文件地址 ,第二个是回调函数
  * 通过` ajax` 请求





异步加载 & 同步加载

异步: `ajax`  `jquery ` ,利用` src`    

同步 : 文本和` try-catch` JavaScript代码会立即执行.



以后可能可以用` import`  的方法





##### 加载与阻塞

* 通过` src` 属性 ,设置时不请求 , 插入完成后 , 下载 ,下载完后 ,立即执行
* 字符串,插入页面后,立即执行
* 动态加载在下载的时候不阻塞 , 执行会阻塞.

