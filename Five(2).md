### 第五章

#### 5.5 Function 类型

* 函数是对象,函数名是指针

  * ##### 5.5.1 没有重载

    * 就是后面的被前面的覆盖了

  * ##### 5.5.2 函数声明与函数表达式

    *  这俩不一样的,函数声明会提升, 函数表达式就不行.
    * 解析器会率先把 函数声明读取了  ,  函数表达式就是执行到它了,才会执行.

  * ##### 5.5.3 作为值的函数

    * 函数名字本身也是变量 ,函数也可以当作值来使用.
    * 函数 (不要运行函数的那对  大括号 )  可以直接当作别的函数的参数.
    * 如果在函数内部嵌套函数  ,一定要在内部函数前面用 `return`   ! ! !
  
  * ##### 5.5.4  函数内部属性
  
    * 函数内部有俩对象  :  arguments   /  this
  
    * arguments :
  
      *  当用递归函数 , 不可避免会在一个函数内部里面再次提到函数名字   ,可以把内部的函数名字改为  : ` arguments.callee` 
  
      * ```  js
        //一个计算阶乘的函数
        funtion factorial (num){
            if(num<1){
                return 1;
            }else{
                return num*arguments.callee(num-1);
            }
        }
        
        //使用的好处
        var trueFactorial=factorial;
        factorial = function (){
            return 0;
        }; 
        
        alert(trueFactorial(5));   //120
        alert(factorial(5));  //0
        
        
        ```
  
    * this:
  
      * this 在全局环境里面引用的就是  `window` .
      * 假设一个函数在全局里面  ,然后我现在想在一个实例里面使用它 ?      我可以把这个函数绑定到这个实例对象里面去  ,就可以把`this`变成当前对象.
  
    * caller
  
      * 这是一个属性,保存的是   调用当前函数的的函数的引用  .
  
    * 在严格模式下,访问`arguments.callee`会报错
  
  * ##### 5.5.5 函数的属性和方法
  
    * length
  
      * 保存   函数接收的参数的数目.
  
    * prototype
  
      *  对于引用类型, prototype是保存他们所有的实例方法的.
      * 这不可以枚举.
  
    * 方法  :
  
      * `apply()`方法
  
        * 设置函数体内`this`的值
  
        * 俩参数 ,第一个表示作用域 ,第二个表示参数数组(arguments数组 / Array数组)
  
        * ``` js
          sum.apply(this , arguments);
          //表示在this环境下 ,给sum()函数传递参数 1,2 ;
          sum.apply(this,[1,2]);
          ```
  
        * 在严格模式下 ,没有确定环境对象,那`this`就不是表示`window`哦
  
      * `call()`
  
        * 设置函数体内` this`的值
        * 参数 ,第一个还是`this ` ,其他参数   必须必须必须 逐个列举!!!
  
      * 强大的地方 :   扩充函数的作用域
  
        * ``` js
          window.color="red";
          var o={ color: "blue"} ;
          
          function sayColor(){
              alert(this,color);
          }
          sayColor();   //red
          
          sayColor.call(this);  //red
          sayColor.call(window); //red
          sayColor.call( o );  //blue
          
          ```
  
        * 对象不需要与方法有任何耦合关系
  
      * `bind()`
  
        * 会创建一个函数的实例,把`this` 值绑定到`bind()` 函数.
  
        * ``` js
          window.color="red";
          var o={color: "blue"};
          
          funtion sayColor(){
              alert (this.color);
          }
          
          var objSayColor=sayColor.bind(o);
          objSayColor();  //blue
          ```
  
    ##### 
  
    #### 5.6 基本包装类型
  
    * 像这样的 ` var sl= "some text" `  这样的 ,访问` s1` 的时候
      * 创造一个String类的一个实例
      * 调用指定方法
      * 销毁这个实例  !!!!
      * 这一行代码完了  ,这个实例就不存在了哦
    * 这种自动创建的基本包装类的对象 ,就只存在于一行代码的执行瞬间,然后就被销毁了.
  
  * ##### 5.6.1 Boolean类型
  
    * ``` js
      var booleanObj= new Boolean(true);
      
      ```
  
    * 容易把对象和基本类型混淆 ,不要用
  
      
  
  * ##### 5.6.2 Number类型
  
    * ` toExponential()`方法
      * 返回用指数类型表示的字符串
    * ` toFixed()` 方法
      *  可以限定小数部分的位数
      * 用法 : ` num.toFixed(2)`  就是保留2位小数
    * ` toPrecision()` 方法
      * 就上面俩方法,它会按照我们的要求,自动选择一种方法
      * 参数1个 ,代表用几位有效数字来表示.
    * 不建议直接实例化!!!
  
  * ##### 5.6.3 String类型
  
    * ` var stringObj= new String ("hello world")` ; 实例化
  
    * 字符方法
  
      * ` chatAt()` 返回索引的的对应字符
      * ` charCodeAt()` 返回索引的字符的对应  字符编码
  
    * 字符串操作方法
  
      * ` concat()方法` ,连接字符串的,其实 " + "也用的多
      * 父字符串 创建  子字符串
        * 一共3个方法, 可以接受1-2个参数.
        *  ` slice()` 方法 ,
          * 第一个参数表示  开始地点   ,第二个参数表示   结束点 (不包括)
          *  要是是负数, 第一个加上字符串长度 ,第二个就是 7
        * `substring()` 方法
          * 第一个参数表示  开始地点   ,第二个参数表示   结束点 (不包括)
          * 要是负数,负数都变成0
        * ` substr()` 方法
          * 第一个参数是起始位置  , 第二个参数是  长度!!!
          * 负数的话,第一个加上字符串长度 , 第二个变成0
  
    * 字符串位置方法
  
      * 就之前介绍过 , `indexOf`  方法   ,` lastIndexOf()` 方法,前者  前---> 后  ,后者相反
      * 第二个参数表示 搜索的起始位置.
  
    * ` trim()` 方法
  
      * 删除字符串前后空格的
  
    * 字符串模式匹配 (没咋看懂的,懂了另写)
  
      
  
      * `match()` 方法,一个参数
      * ` search()` 方法 .用正则表达式
      * ` replace()`  方法,
      * `split()` 方法
  
      
  
      #### 5.7  单体内置对象
  
      - ##### 5.7.1 Global对象
  
        - 两种编码方法 , 并且有对应的解码方法
  
      - ` eval()` 方法
  
        -  可以在这个方法里面写正常代码 , 但是里面定义的变量不会提升.
        - 慎用
  
      - ##### 5.7.2 Math对象
  
        -  舍入方法  :
  
          -  `Math.ceil()` 向上取整
          - ` Math.floor()` 向下取整
          - `Math.round()` 四舍五入
  
        - ` random()` 方法
  
          - 随机数  0-1  ;
  
          - 与`floor`结合可以产生任意数段的随机数
  
            
  
      
  
      
  
      
  
      
  
      
  
      
  
      
  
      
  
      
  
      ​	
  
      
  
      
  
      
  
      
  
      
  
      
  
      
  
      
  
      
  
      
  
       