**笔记杂记**

在rust中的数字类型组要有以下这些,
i8,i16,i32,i64(有符号整型),以及无符号整型u8,u16,u32,u64.

使用let关键字声明变量
~~~
let a:i32=1;
//等同于 int a=1;
//也可以这样
let a=1;
//Rust将会自己类型推断
~~~
Rust默认情况下所有变量都是constant,需要加mut关键字使之可变
~~~
let mut a=1;
~~~
string在rust中有点差别,有两种str
~~~
let s:&str="hello world";
let mut s:String=String::from("hello");
上面一种相当于是C中的字符串常量,只读
下面的则是可变字符串
~~~
存储一系列事物的方式
~~~
//变长数组
let mut v:Vec<i32>=Vec::new()
v.push(2)
v.push(3)
//定长数组
let mut arr: [i32; 4] = [0, 2, 4, 8];
arr[0] = -2;
println!("{}", arr[0] + arr[1]);
~~~
循环遍历的方法
~~~
//采用iterator遍历数组
for i in v.iter()
    println("{}",i);
//while循环
while i<20{
    i+=1;
}
//rust内独有的loop循环,相当于while(true)
loop {
    i+=1;
    if i==10 {break;} 
}
~~~
最后是rust的函数
~~~
//像这样声明

fn sum(a: i32, b: i32) -> i32 {
    a + b
}

// Void function (no "->")
fn main() {
    // do stuff...
}
~~~
上述有两个关键点
* 你需要指定返回值的类型
* 没有return 关键字,以及没有分号!
以下有两个关键点
~~~
对于C语言,
int x=if(some){
    2;
}else{
    4
};
以上无法编译通过,因为if是语句(statements),不求值(evaluate to value)
但是对于rust而言,一切都是表达式(expression),因此以下代码是合理的
let x =if somebool{2}else{4}(受到了函数编程思想的影响)
~~~
在rust中,函数就是一系列的expression,并以分号隔开,然后计算最后一个expression的值,故最后一个expression不需要分号(有分号反而会报错)
~~~
一个递归的例子
fn fib(n:i32)->i32{
    if n<=1 {n}else{fib(n-1)+fib(n-2)}
}
~~~