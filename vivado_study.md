##### 在学习完verilog基础之后，开始使用vivado软件编写代码。

###### 第一个项目

~~~
点击create project
project name and project location
//这里需要注意的是每个教程都提醒存储路径不能有中文路径，我也没有亲自去实验中文路径会出什么bug
选择RTL project
选择板卡
finish
add or create design source 
创建或者导入.v文件
双击.v文件，可以在右侧进行编写
//把默认编辑器换成了vscode
写完RTL代码后，编写testbench进行仿真
add or create simulation sources
{design_name}_tb作为仿真文件名
编写仿真文件
可以run simulation
出现波形图
run synthesis 
//综合这一步有的教程在simulation前就会run
schematic 可以查看synthesis 后的网表
......
(接下来的步骤还不清楚，先熟悉上面的这些步骤)
~~~

###### 使用vivado中出现的一些问题

###### 1

安装的时候双击 xsetup.exe 不起作用，后来网上查找的需要删除.bat文件的一段脚本才行

可能是权限问题  [vivado点击xsetup.exe没有反应——一些你忽略了的小细节_vivado安装点击xsetup没反应-CSDN博客](https://blog.csdn.net/CoderLiSmart/article/details/105306664)

###### 2

用户名和电脑名不能有中文，用户名不好改，重新创了个用户用来使用vivado

###### 3

因为是新的用户，在修改编辑器为vscode是，要为用户添加环境变量

###### 4

再三提醒，各个文件路径不能含有中文  会出现各种各样的小问题



##### 实例

###### design source 

~~~verilog
module gates1(
    input a,
    input b,
    output [6:0] y
    
    );
    
    assign y[0] = a & b;
    assign y[1] = ~(a & b);
    assign y[2] = a | b ;
    assign y[3] = ~(a | b);
    assign y[4] = a ^ b;
    assign y[5] = a ~^ b;
    assign y[6] = a+b;
  
endmodule
~~~

###### simulation source 

~~~verilog
`timescale 1ns/1ns
module test();
    reg a,b;
    wire [6:0]y;
    
    gates1 tsh(
        .a(a),
        .b(b),
        .y(y)
    );

    initial begin
        a=0;b=0;
        # 10;
        a=0;b=1;
        # 10;
        a=1;b=0;
        # 10;
        a=1;b=1;
        # 10;
        $stop;
    end
endmodule
//因为是第一次写测试模块，并没有按照name_tb 的命名格式
~~~

###### schematic after run synthesis



<img src="img\image-20240602105440298.png" alt="image-20240602105440298" style="zoom:50%;" />

//还生成的device我现在也看不懂

###### simulation

<img src="img\Snipaste_2024-06-02_10-58-28.png" style="zoom: 50%;" >



