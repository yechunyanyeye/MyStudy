##### 3.6   语句



###### 3.6.4   for循环语句

学习的知识与c语言的知识区别不大,但是需要特别注意的:

​             因为ECMAScript中不存在着块级的作用域,所以,在循环体外部可以访问循环体内部定义的变量,比如了:

<script>
    var count=10;
    for( var i=0;i<count;i++){
        alert(i);
    }
    alert(i);   //会输出10

​        


```javascript

```
</script>



###### 3.6.5  for-in 语句

用处  :  枚举对象的属性;

示例 :

<script>
    //循环输出对象的属性,每个属性输出一遍
    for ( var propName in window){
        document.write(propName);
    }
</script>



要注意的: 

​     如果对象是null 或者 undefined  使用的时候要特别注意,可能会报错,也可能不会执行.



###### 3.6.6 label  语句



作用: 在代码中添加标签,一般和循环语句一起用.



###### 3.6.7  break/continue



这俩语句也可以和label语句一起用:

​          break;   同时把内外两个语句都退出

​          continue ; 退出内部循环,执行外部循环.





###### 3.6.8  with语句



 作用:  可以把作用域设置到一个特定的对象中,也可以使代码更加简洁哦

比如说  :

<script>
    var qs=location.search.substring(1);
    var hostName=location.hostname;
    var url=location.href;
</script>

他就可以通过with语句,简洁为:

<script>
    with(location)
        {
            var qs=search.substring(1);
            var hostName=hostname;
            var url=href;
        }

​    


        

</script>

严格模式下,不可以使用的,会报出语法错误,  (不建议使用with语句)



###### 3.6.9 switch语句



用法和C语言里面的区别不大,但还是要注意的点:

 switch语句可以使用任何数据类型的.

switch语句使用的使全等的操作符,不会进行类型转换哦



##### 3.7  函数



###### 3.7.1  理解参数

1. 参数的个数嘛,虽然定义函数的时候写了几个,但是!!!  在用函数的时候,你既可以传超多参数,也可以不传参数.   为啥呢?    因为参数都是放在一个数组里面的,函数接收的时候,只关心数组...

2. 参数这个特性嘛,有点像函数的重载.

3. arguments对象可以和命名的参数一起使用,比如了:

   ​    num1,  arguments[0]   表示的是一样的东西

4. 它的值和对应的命名参数的值是同步的,就是说,如果你改变了数组的第二个值,number2  也会发生变化.

    但是,他们的内存空间是独立的,只是保持着值是一样的.

5. 没有传递值得命名参数会被自动赋予undefined.

6. 严格模式下,有限制!!!

      假设把arguments[1],设置为10,number 2  也是不会改变的.  其次,重写arguments的值会导致语法错误.



###### 3.7.2 没有重载  没有重载   没有重载

如果js中,定义了俩同名的函数,那这个名字,只属于后面定义的那个函数  (就是被覆盖啦 )

那我们怎么达到重载的效果呢    ?     就是根据传入参数的类型和数量作出不同的反应啦.





 