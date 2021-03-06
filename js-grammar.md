# 《js基本语法》
## 1.表达式与语句
### 表达式,一般结果是个值，可以放在需要一个值的地方。
* 1+2=3，就是个值为3的表达式
* `add（1，2）`是一个值为函数add返回值的表达式
* `console.log`值为函数本身的表达式
* 特别需要注意的是`console.log(3)`这个表达式的值不是3.而是undefined

### 语句，一般会改变环境，如：声明，赋值
* `var a=1`,就是一个语句，他也有值，值为undefined
### 值得注意的是两者在书写时大小写要注意，大写与小写代表的不一样的东西，如：Object与object，大部分的空格与回车不影响结果的产生，但有一个例子绝对不能在后面加回车，那就试试return后面，如：
```JavaScript
function fn(){
    return 3;
}
```
该函数的返回值是3，但如果在return后加了回车键，就会返回undefined
## 2.标识符的规则
* 第一个字符必须是unicode字母（包含多个国家的字母）或$或_或中文
* 后面的字符除了第一个字符所说的以外还可以有数字，变量名就属于一种标识符，例：`var _=1`
* 注释通常用//表示单行注释，/**/表示多行注释
  ## 3.if else 语句
  ### 语法：if（表达式）{语句1}else{语句2}，（注：if后面只有一条语句是{}可以省略，但不建议这样写）主要意思是如果表达式为true，则执行语句1，不满足则执行语句2

  * ### 接下来讲一下最常见也是最推荐的一种使用方法
  ```JavaScript
  if(表达式1){
      语句1
  }else if(表达式2){
      语句2
  }else{
      语句3
  }

  ```
  * ### 将if嵌套语句放在函数里面的写法
  ```JavaScript
  function fn(){
      if(表达式){
          return 表达式
      }
      if（表达式）{
          return 表达式
      }
      return 表达式
  }
  ```
### 说一个if语句的坑
```JavaScript
var a=1
if(a===2)
console.log('a')
console.log('a等于2')
```
此结果谁输出'a等于2'，因为if省略掉了{}，从而跳出第一句`console.log`,但但如果在两句`console.log`之间加一个“，”号，输出结果就为undefined,因为用逗号连接的代表为一条句子
## 4.while for 循环语句
### while（循环）
* 语法：`while（表达式）{语句}`，判断表达式的真假，为真执行语句，执行完，在判断表达式，为假则跳出循环执行后面内容
  * ### 关于while语句的两个坑
  1.
  ```JavaScript
  var i=0
  while(i<10){
      console.log(i)
      i=i+1
  }
  ```
  此代码正常的运行结果应该是0-9，但是在Chrome浏览器的开发者工具是通常会有10出现，属于一个bug，可以在花括号外面加一句`console.log('done')`即可验证。
2.
```JavaScript
var a=0.1
while(a!==1){
console.log(a)
a=a+0.1
}
```
此代码会进入一个死循环，由于浮点数的原因，a是不会刚好等于1。
### for循环语句
* 语法：`for(语句1；表达式2；语句3){循环体}`
  
  注意：语句1，表达式2，语句3均可以忽略不写，但是表达式2与语句3不写会出现死循环。
  * ### 有关for语句的两个坑
  1.
  ```JavaScript
  for(var i=0;i<5;i++){
      console.log(i)
  }
  ```
执行结果为0，1，2，3，4，但最终i的值为5，因为执行完`console.log(i)`后还会执行一次i++
2.
```JavaScript
for(var i=0;i<5;i++){
    setTimeout(()=>{
        console.log(i+'随机数'+Math.random())
    },0)
}
```
会打印出来5个5，因为setTime代表的是过一会执行，只有执行完for循环过一会后才执行setTime。(将var改为let，则可以打出0,1,2,3,4)
## 5.break语句
break语句主要用于跳出循环语句，注意的是跳出整个循环。
## 6.continue语句
是推出当前一次的循环而不是整个循环，与break不同
## 7.label标记语句
就是在一条语句前面加个可以引用的标识符。

