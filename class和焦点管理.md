### DOM扩展

------



#### 选择符API



##### ` querySelector()` 方法

* 此方法接受一个css选择符 , 返回的是匹配的第一个.

* 没找到返回` null` 

* ``` js
  //取得body
  var body = document.querySelector("body");
  
  //取得ID为"myDiv"的元素
  var myDiv = document.querySelector("#myDiv");
  ```

* 通过` document`类型调用,在文档范围里面找 ,  通过` element` 类型调用,只会在该元素后代元素里面找.



##### ` querySeletorAll()` 方法

* 接受一个css选择符,返回的是一个` nodeList`的实例 , 也就是所有满足条件的

* ``` js
  //取得某<div>中的所有<em>元素 (类似于getElementByTagName("em"))
  var ems = document.getElementById("myDiv").querySelectorAll("em");
  
  //取得类为"selected"的所有元素
  var selected = document.querySelectorAll(".selected");
  
  //通过下面的方法取得每一个元素
  var i,len,em;
  for(i=0,len = ems.length; i<len;i++){
      em = ems[i];
  }
  ```



#### HTML5



##### ` getElementsByClassName()` 方法

* 可以通过`class`名字 , 访问元素 , 但是` IE9` 以下有问题
* IE9 以下如何处理:
  * 创建一个空的数组
  * ` getElementsByTagName(*)`   所有节点
  * 用循环,判断所有节点是否带有特定的` class`名字 ,有的话,就添加进空数组
  * 性能会下降.



##### ` classList`属性

* 可以获取到元素所有的` class` 名字
* 四种方法
  * ` add(value)`  将value添加到列表里面
  * ` contains(value)`  表示列表中是否存在给定的值
  * ` remove(value)` 从列表删除给定的字符串.
  * ` toggle(value)` 如果列表中有,就删除;  没有,就添加.
* 有兼容性问题
* 添加多个的话 , 重写方法 .
* 多个`class`添加 ,浏览器只渲染1次哦 ( 添加完了再渲染)





##### 焦点管理

* ` HTML5`添加了管理DOM的功能

  * ` document.activeElement` 属性

    * 始终引用DOM中当前获得了焦点的元素

    * 文档加载期间,属性的值是` null` , 文档加载完了 , 会指向` document.body` 元素

    * Tab和` focus()` 方法会让对应的元素获得焦点

    * 如何判断文档获得了焦点?

      * ` document.hasFocus()` 方法

      * ``` js
        var button = document.getElementById("myButton");
        button.focus();
        alert(document.hasFocus());   //true
        ```

      * 这个方法只能判断文档是否焦点

      * 浏览器处于激活状态,对应的事件才能触发

      * 这个方法是基于网页的,判断交互的位置是不是在网页里.

* 焦点管理的意义

  * 标准的焦点管理,开发会显得规范化.
  * 对残障人士的意义
  * 可以提升用户体验