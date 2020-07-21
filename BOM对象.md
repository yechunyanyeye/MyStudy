###  第八章



#### window对象

* `BOM`的核心对象是` window`

* 所有在全局作用域中声明的变量, 函数都会变成` window`对象的属性和方法 .

* 例子

  * ``` js
    var age = 29;
    
    function sayAge(){
        alert(this.age);
    }
    
    alert(window.age); //29
    sayAge();          //29
    window.sayAge();   //29
    
    ```

* 全局变量不能通过` delete` 操作符删掉 , 而直接在` window` 对象上的定义的属性可以

  * ``` js
    var age = 29;
    window.color = "red";
    
    //在IE<9 时抛出错误 ,在其他所有浏览器里面返回false
    delete window.age;
    
    //在IE<9 时抛出错误 ,在其他所有浏览器里面返回true
    delete window.color;
    
    alert(window.age);   //29
    alert(window.color); //undefined
    ```



##### 窗口关系及框架

* ` frame` 标签可以嵌套窗口 , 每个窗口都有` window` 对象 .
* 创造的对象都保存在` frames` 伪数组里面.
* 访问的话 ,可以用` frames[下标]`  , ` frames["name"]` 
* 如何管理
  * ` top` 对象始终指向浏览器窗口 ,也就是最外层的对象
  * ` parent`  对象始终指向当前框架的直接上层框架
  * ` self` 始终指向` window`.
* 每个` window` 对象里面都包含原生类型的构造函数 



#####  窗口位置

*  ` screenLeft` 和` screenTop` 分别用于表示窗口相对于屏幕左边和上边的位置
* 用之前先判断 , 而且也得不到精确的坐标值



##### 窗口大小

* 取得不准的
* 各个浏览器也不一样 ,也比较少用



##### 导航和打开窗口

* ` window.open()` 方法.
  * 4个参数 , (要加载的URL ,窗口目标 ,特性字符串,布尔值)
  * 返回值也是一个`window` 对象
  * 可以用` close()` 方法关掉



##### 间歇调用和超时调用

* `js`不是多线程

* 超时调用

  * 在指定的时间过后,执行代码

  * 对应的函数被挪到所有代码的最底下

  * ` setTimeout()` 方法 , 2个参数 ,第一个是要执行的代码 ,第二个是 时间

  * ``` js
    setTimeout("alert('hello world')" , 1000) ;    //直接传递字符串 ,不推荐
    
    setTimeout(function(){
        alert("hello world");
    },1000);
    ```

  * 使用` clearTimeout()` 方法取消超时调用

    * ``` js
      
      var timeoutId = setTimeout (function(){
          alert("hello world");
      },1000);
      
      clearTimeout(timeoutId);
      ```



* 间歇调用
  * 表示每隔一段时间,就执行一次代码 
  * 具有累积效应 , 有可能会一直执行里面的函数 (所以被替代啦)
  * ` setInterval()`方法和` setTimeout()` 用法差不多的
  * ` clearInterval()` 方法取消
  * 使用` setTimeout`来代替.
    * ` setTimeout(argument.callee ,时间)`    //写在函数最后一行 .
* 可能会造成动画卡顿 
  * 使用`CSS3` 来解决
  * `requset` 来解决



##### 系统对话框

* ` alert()` 
  * 只用于提示
* ` comfirm()` 
  *  有确认,取消按钮
    * 确认就返回` true`
* ` prompt()`
  * 第一个参数,要显示的文本提示 , 文本输入框默认值
* 这些对话框,是阻断的, 显示对话框,代码会停止运行
* 对话框样式由浏览器来定





#### location对象



* 即是` window`对象的属性,也是` document` 对象的属性
* 有8个属性,常用的有` hash`,` href`,` search`
  * 属性是可写的,写后,页面会刷新(`hash`不会刷新哈)



##### 位置操作

* ` assign` 方法 
  * ` location.assign("http://www.wrox.com");`
  * 在历史记录中生成一条记录,'后退' 会回到前一个页面
* ` replace` 方法
  * ` location.replace("http://www.wrox.com");`
  * 不会生成历史记录 , '后退' 不能回到前一个页面
* ` reload()` 方法
  * 重新加载当前显示的页面
  * 布尔参数,表示是否绕过缓存,默认` false`





#### history对象



``` js
//后退一页
history.go(-1);
history.back();


//前进一页
history.go(1);
history.forward();
```





