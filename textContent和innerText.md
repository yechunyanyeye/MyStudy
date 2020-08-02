###  textContent和innerText

------



起因 : 火狐浏览器把innerText换成了textContent  ,  但 其他浏览器上面,也是可以使用textContent的 .



平常我们使用的时候 , 一般都是先判断浏览器是否支持` textContent`   ,那` textContent`和` innerText`有什么区别呢 ?





二者区别:

* ` textContent` 返回的包括<script>和<style>标签的内容 , ` innerText`则是不包含的.
* (最重要的区别) ` innerText`返回的值,依赖于页面的显示. ` textContent`依赖于代码的内容
* 在使用` innerText`设置值的时候 , 会触发"回流"操作  ,但是在` textContent`里面 , 设置值不一定会触发""回流''操作	
  * 回流是啥 ?  当我们重新设置了` innerText` 后 , DOM树会从当前节点回溯到根结点 , 然后从根结点再运行一次(这里又渲染了一遍页面) ,影响整个页面 !
  * 重绘是啥 ? 对一个DOM节点往子节点进行排列 . 重绘只是影响页面的一部分 .  回流会引起重绘 , 但重绘不一定引起回流.
  * ` textContent`对页面的影响小一些,所以先判断的` textContent`.
* ` innerText`的返回值会被格式化 ,但是` textContent`的返回值不会被格式化.
* ` innerText`会把页面里的空标签当作换行处理,  ( 一个空标签是一行 , 连续的多个空标签也是一行)   ,但是` textContent`就返回一行文本(有子标签才会返回多行文本) .
* 获取文本内容的时候 ,我们还可以直接找到文本节点,再使用`nodeValue`,但这个方式不能获得DOM内容. 这样获得的东西跟` textContent` 获得的相似.







### 自闭和元素的处理

------



有一些标签不是成对出现的 , 也叫无内容元素 ,比如<br> 

不建议对这些标签使用` innerText`,` textContent`啥的 ,影响很不好.

