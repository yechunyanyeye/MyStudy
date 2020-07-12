### 第六章   面向对象的程序设计

#### 6.1 理解对象

* ##### 6.1.1 属性类型

  * 数据属性
    * Configurable  ;   表示能否通过delete删除属性从而重新定义属性
    * Enumerable  ;    表示能否通过for-in 循环返回属性
    * Writable         ;    表示能否修改属性的值.
    * Value              ; 包含这个属性的数据值
    * 要修改属性默认的特性,必须要用` Object.defineProperty() ` 方法.  三个参数  ,(属性所在对象, 属性的名字, 描述符)       , 描述符就是楼上四种 .
    * 一旦把Configurable属性定义为不可配置,就不能变回 可配置了  !!!
  * 访问器属性
    * Configurable  ;   表示能否通过delete删除属性从而重新定义属性
    * Enumerable  ;    表示能否通过for-in 循环返回属性
    * Get                 ;  读取,默认为undefined ;
    * Set                  ;  写入,默认为undefined ;
    * 访问器属性不能直接定义,必须使用`Object.defineProperty()` 方法来定义  .
    * _year 表示 只能通过对象方法来访问的属性 .
    * 设置一个属性的值,会导致其他的属性发生变化.
    * 不能支持`Object.defineProperty()`方法的 浏览器 ,不能修改前2个属性 .

* ##### 6.1.2 定义多个属性

  * 用` Object.defineProperties()` 方法来一次性定义多个属性  .

* ##### 6.1.3 读取属性的特性

  * 用` Object.getOwnPropertyDesscript()` 方法  ,可以取得描述符!!

  * 2参数, (属性所在的对象 ,属性名称)

    