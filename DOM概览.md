### DOM

* ` DOM`节点是` node`类型
* ` node`有12种,常用的只有3种.
* 节点2之间的关系,父子节点,兄弟节点



下面是3种常用的` node`节点类型

* ` Document` 类型

  * 重要的属性
    * ` document.documentElement` 访问` HTML`整个
    * ` document.body` 对应` HTML`中` body` 的东西
    * ` document.title` 对应`head` 的标题
    * ` document.domain` 得到域名信息,只能从低级往高级改.
    * ` referrer` 保存着连接到当前页面的URL,即前一个页面的地址

*   `Text`类型

  * 属性
    * ` nodeType` 为3
    * ` nodeName`为` #text`;
    * ` nodeValue` 的值为节点包含的文本
  * 方法 不常用

* ` Element`类型

  

  * `node`节点的属性,有值就返回,没有就` null`

    * ` nodeType`
    * ` nodeName`  返回节点名称
    * ` nodeValue`  结点值
    * `childNodes` 保存着一个类似数组的东西,存着节点
    * ` parentNode` 指向父节点
    * 访问兄弟节点
      * ` previousSibling` 访问前一个兄弟节点
      * ` nextSibling` 访问后面一个兄弟节点
      * 第一个和最后一个都是` null`
    * ` firstChild` 第一个节点
    * ` lastChild` 最后一个节点
    * ` ownerDocument`可以直接访问文档节点

  * ` attributes` 属性

    * 获得伪数组,可以通过下标访问

  * 节点的公共方法

    * ` hasChildNodes`   看有没有子节点 , 返回布尔类型,有则` true`
    * ` appendChild` 在末尾插入节点,返回节点
    * ` insertBefore` 俩参数,第一个是要插入的节点,第二个是参照节点
    * ` removeChild` 删掉子节点 , 参数为父节点
    * ` replaceChild`  替换节点,参数是 要插入的节点, 要替换的节点  .返回被替换的节点并移除.
    * ` cloneNode()` 
      * 浅拷贝 ,参数为` false`  ,只复制节点本身,返回这个节点
      * 深拷贝 , 参数为` true` ,复制节点及其整个子节点树

  * ` Element`

    * 属性

      * ` nodeType` 的值为1
      * ` nodeName` 为元素的标签名 , 但是结果是大写的
      * ` nodeValue` 为` null`

      

      * ` id` 得到` ID`信息
      * ` title` 对节点进行说明
      * ` dir` 语言的方向,默认从左往右
      * ` className` 通用的` class`  ,得到对应的字符串

    * 如何获取` Element`节点

      * ` getElementById`  查找ID,唯一的
      * ` getElementsByName` 得到数组
      * ` getElemenstByClassname`
      * ` getElementsByTagName`
      * ` querySelect` 参数为    . 类名
      * ` querySelectAll` 得到所有同类名的数组

    * 如何创建

      * ` document.createElement()` ,参数是要创建元素的标签名

      * ``` js
        var div = document. createElement("div");
        ```

      * 创建后,再插入到` DOM`树中

    * 取得特性.得到的都是字符串.

      * ` getAttribute()`

        * ``` js
          var div =  document.getElementById("myDiv");
          
          alert(div.getAttribute("id"));  //'myDiv'
          //想要获取class  要用class
          ```

      * ` setAttribute()`

        * ``` js
          div.setAttribute("id","someOtherId");  //参数,(特性名,替换值)
          //有这个特性 ,就被修改
          //没有这个特性,就添加这个特性
          
          
          ```

      * ` removeAttribute()`

        * ``` js
          div.removeAttribute("class");  //彻底删除元素的特性 
          ```

      * ` hasAttribute`   

      

      

      

      

      

      

      

      

