###  脚本化CSS

------





通过`js`读取style :

#### 内联样式表要注意的地方

* 如果`css`里面包含了一个或者多个连字符的时候 , 属性名改成驼峰命名 , 比如` background-color`改成` backgroundColor` 
* `css`属性中 , 有些属性是`js`的保留字 , 创建的时候加个`css` 前缀  ,比如`float`, ` cssFloat`
* 所有的`style`对象的属性,都是可读可写的,更新了浏览器也会立马更新
* 对于一些代码上的错误 , 比如` float:123`  , 浏览器不会报错 , 也不会执行
* 在标准模式下 , 要设置单位 , 混合模式下就不要设置单位.
* 在`js`里面读取一个没有设置的样式, 读取会返回一个空的字符串
* 设置颜色 , 使用16进制 , 通过js读取时,有些返回16进制 .有些不是





#### style对象的属性和方法



* 属性
  * ` cssText ` 可以访问到`style` 里面的`css` 代码      (`IE8`返回的所有属性名称都是大写) .
  * ` length`  返回当前`css`属性的数量  (`IE8`不支持)
  * ` parentRule` 表示`css`信息的`CSSRule`对象  (   IE8 不支持)
* 方法
  *  6个 , IE8都不支持
  * ` getPropertyPriority(propertyName)`  如果这个属性使用了` !important` ,则返回` important` ,不然返回空字符串.
  * ` getPropertyValue(propertyName) ` 返回给定属性的字符串值 .
  * ` item(index)`  返回指定位置的`CSS`属性
  * ` removeProperty(propertyName)`  从样式表里面删除给定属性
  * ` set Property(propertyName,value, priority)` 将给定属性设置为相应的值 ,并加上优先权标志 (  " `imporyant `"  或者一个空的字符串  )
  * ` getPropertyCSSValue(propertyName) ` 返回包含给定属性值的`CSSValue`对象 (   不咋用   /兼容性还不好)  





#### 计算样式

* ` getComputedStyle()` 方法   (IE不支持)

  * 获得一个对象,包含当前元素的所有计算样式

  * 参数 ,要获取样式元素和一个伪元素字符串 , 第二个也可以是null .  

  * 使用方法

    * 使用` window.getComputedStyle()`
    * 直接使用` getComputedStyle()`
    * 使用` document.defaultView.getComputedStyle()`

  * IE8 的` currentStyle` 属性

    * ``` js
      var myDiv = document.getElementById("myDiv");
      var computedStyle = myDiv.currentStyle;
      
      alert(computedStyle.backgroundColor);
      alert(computedStyle.width);
      ```

* ` getComputedStyle()`需要注意的 :

  * 获取之后 , 里面所有的属性都是只读的
  * `CSS`里面有复合属性 , 比如`border`  .读取复合属性 , 不同浏览器返回的不一样 .
  * 返回的值 , 都是像素值 (  px  )
  * 如果一个DOM节点没有使用绝对定位 , 获取top值得时候 , 返回的会是auto
  * 虽然计算样式 , 是浏览器呈现的样式 , 但是也是不准确的.





#### 脚本化CSS类

* 使用DOM节点的` class ` 属性  ,但是js里面要用` className`
* 切换class类效果好点  .
* 赋值必须是字符串 , 不是字符串也会变成字符串 .
* 如果要给一个DOM节点添加属性 ,要先把之前的类名和要添加的类名拼成一个字符串 . 由此引入了`classList`.
  * ` classList`   这有add , contains ,remove, toggle ,replace   5种方法     (replace兼容性辣鸡).

