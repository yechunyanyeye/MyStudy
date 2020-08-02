### JS 的滚动操作

------

下面的方法/属性,都可以通过元素调用;



方法 :

* ` scrollIntoView()`  滚动到视窗当中.  (最常用的  ,  谁叫他所有浏览器都支持呢)

  * 对元素调用这个方法后,这个元素便会呈现在当前的视窗中.  (不一定能看到 , 可能被挡住了)
  * 滚动的过程是没有动画的.
  * 可以接受一个 布尔类型的参数, ( true/无参数)会让元素顶端和页面顶端对齐 . false 的话,则会跟页面底部对齐.
  * 在火狐浏览器里面 , 参数还可以是一个Object  .  Object的 `behavior` 属性 , 默认是auto , 设为` instant`  就是立即滚动 ;设为` smooth` 就是平滑滚动 .(可以自己加动画) .` block`属性 ,设置为`star` 滚动到开始 ,` end`滚动到结束.
  * 注意点
    * 这个方法基于DOM , 如果节点` display:none` 的话 ,方法就不能实现. ` visibility:hidden` 是可以实现的.
    * 对横向和纵向滚动条都会发生变化.
    * 如果元素本来就在页面当中 ,比如在中心. 页面还是会滚动 , 滚动到顶部/底部 .  (那我们此时不希望这个元素滚动,如何处理 ?  )
    * 对于已经在页面里面的元素 , 我们不希望它滚动到顶部/底部 , 我们可以使用` scrollIntoViewIfNeeded()` 方法 .

* ` scrollIntoViewIfNeeded()`方法

  * Chrome浏览器独有 ,其他浏览器调用会报错.
  * 和` scrollIntoView()`方法差不多的 , 就1个区别:
    * 当元素已经在当前页面里边 , 这个方法不会把元素滚动到页面顶部/底部.

* ` scrollByLines(lineCount)`  

  * `lineCount `  可以是正数,也可以是负数.  表示向上/向下滚动多少行.
  * Chrome浏览器独有 ,其他浏览器调用会报错.

* ` scrollByPages(pageCount)`

  * ` pageCount`可以是正数,也可以是负数.  表示向上/向下滚动多少页.
  * Chrome浏览器独有 ,其他浏览器调用会报错.

  

  

  #### 定点滚动

  ------

  

  

  * ` scrollTo()`
    * 可以接受两个数字作为参数 ,参数不可以省略.
    * 参数  (横坐标,纵坐标)
  * ` scrollBy()` 
    * 往某一个方向滚动 , 调用一次滚动一次.
    * ( x方向的偏移量,  y方向的偏移量)

  

  这2个是` window`属性,比如 ` window.scrollTo()`.

  







属性 :

* ` scrollTop` 

  * 读写

  * 获取/设置某一个元素内容的垂直滚动像素 ,滚动条距离容器顶部的值

  * 赋值会产生滚动

  * 兼容性: 有些获得` html`,有些获得` body`  .之前遇见过,可以这么写:

    * ```js
      this.scrollTop =
                      window.pageYOffset ||
                      document.documentElement.scrollTop ||
                      document.body.scrollTop;
      ```

* ` scrollLeft` 

  * 和` scrollTop`用法差不多.
  * 读写

* ` scrollHeight`

  * 只读
  * 返回的值是不包括滚动条空间的 .