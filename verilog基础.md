verilog模块结构

~~~verilog
module MUX21a(a,b,s,y); # module 模块名 端口列表
    input a,b,s;    # 对端口列表声明
    output y;
    assign y=(s?a:b);# assign 语句
endmodule
# 2选1模块
~~~

assign 赋值目标=表达式

利用assign赋值目标必须是wire



算术型

~~~
*
/
+
-
%
**  //求幂
~~~

逻辑型 

~~~
！  逻辑非
&&  逻辑与
||  逻辑或
~~~

关系型

~~~
>
<
>=
<=
~~~

按位运算符

每一位进行逻辑运算，位数不同，位数小的自动左添0

~~~
~ 按位非
& 按位与
| 按位或
^ 按位异或    
~^ 按位同或
~~~

移位运算符

~~~
>>  右移
<<  左移
>>> 算术右移
<<< 算术左移
~~~

拼接复制

~~~
{}
y={4'b1001,2'b11};    结果为100111
{{}}
y={4{2'b01}};         结果是01010101
~~~

条件运算符

~~~
? :    用法和java等编程语言相同
~~~





语句块

always

~~~verilog
always @(signal)
	语句;
always @(posedge CLK)
    Q=D;
~~~

赋值目标是reg型



always激活条件用两种  边沿敏感  电平敏感

~~~verilog
# 边沿敏感
posedge 信号   # 信号上升沿到来
negedge 信号   # 下降
# 电平敏感
# always @(a,b,c)  当信号列表中的任一个信号有变化，触发
~~~

always中可以用if case for循环语句



assign连续赋值语句 总是处于激活状态，

只要操作数有变换马上进行赋值

always过程赋值语句 只有激活该过程，

才进行计算赋值



always语句块如果有多条赋值语句 必须用 begin end包括起来

~~~verilog
# begin end 之间赋值语句 阻塞赋值 非阻塞赋值
begin
	a=b;	
	c=d;
end  # 阻塞型赋值，赋值语句必须等上一条语句执行完成之后才能继续执行

begin
    a<=b;
    b<=c;
end  # 多条语句并行执行

~~~

设计组合电路常用阻塞赋值，时序电路常用非阻塞赋值



底层模块

~~~verilog
端口映射

# 命名法
DFF dff1(.CLK(clk),D(d),Q(q));
# 顺序法
DFF dff(a,b,c);
~~~

门原语

~~~
and or xor(异或) nand(与非) nor(或非) xnor(同或)
and(out,in1,in2) 
门原语可以省略实例名，端口只能采用顺序法映射
门原语赋值目标必须是wire型
~~~



数据类型

net类    wire

variable类  reg



数字

<位宽>‘ <进制><数字>

~~~verilog
2' b00    二进制
5' d8     十进制
# 有符号数  sb
8' sb1011011 

~~~



逻辑值

~~~
1
0
x  不确定
z  高阻态
~~~



if 判断语句 和编程语言类似

case 和switch类似









