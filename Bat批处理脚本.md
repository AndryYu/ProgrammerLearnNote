## Bat批处理脚本

#### 1 批处理初体验

批处理脚本格式如下

```
@echo off

···
pause
```

window命令不区分大小写

输出不显示任意键结束 可以使用``pause > null``



#### 2 批处理运算操作

1. 算术运算需要调用``set /a``

   ```
   set /a var = 10 * 10 - 6
   echo %var%
   ```

2. 重定向运算

   ``>`` 与``<``   覆盖原来文件内容

   ``	>>`` 与``<<`` 追加到原来的文件内容

3. 多命令运算

   ``&&``  第一个命令错误不会执行第二个命令

   ``	||``   第一个命令执行成功就不会执行第二个命令

4. 管道符号

   ``|``   前一个命令输出作为后一个命令的输入



#### 3.批处理基本命令

1. 命令格式如下

   ```
   命令 子命令 参数 操作 [选项]
   命令帮助信息查看 /? /help获取详细的帮助信息
   ```

2. 批处理文件接受参数``%num``
3. 注释符拓展 ``rem``  comment
4. 炫酷命令提示符窗口 ``color``与 ``title``
5. 时间相关命令 ``date``  ``time``
6. 启动命令 ``start``
7. 调用其他bat文件 ``call``  无法传递参数
8. 任务列表查看命令 ``tasklist``
9. 任务关闭命令``taskkill``
10. 文件夹解构查看命令 ``tree``
11. 关闭命令 ``shutdown``
12. 计划任务命令 ``at``
13. 环境变量 ``set``



#### 4.文件夹或文件相关命令

1. 目录浏览命令 ``dir``
2. 目录新建与删除 ``mkdir`` 与``rmdir``
3. 目录切换命令 ``cd``
4. 目录重命名命令 ``ren``  ``rename``
5. 目录拷贝命令 ``copy``
6. 文件删除命令``del``
7. 文件剪切命令``move``



#### 5.网络常用命令

1. 用户操作命令 ``net user``

2. 用户组操作指令 ``net localgroup``

3. 主机连通性测试命令 ``ping``  icmp数据包

4. 网络连接命令 ``telnet``

5. 网络路由信息命令 ``tracert``

6. 网络适配器命令 ``ipconfig``

7. ARP信息命令 ``arp``

   

#### 6.条件判断结构

1. if-else结构

   ```
   set v=hello
   if %v%==hello (echo ok) else (echo no)
   ```

2. 判断文件是否存在 ``exist``

   ```
   if exist 1.bat (echo ok) else (echo no)
   ```

3. 文件判断删除



#### 7.循环结构

1. 循环遍历文件夹名称

   ```
   for /d  %%名称 in (路径/*) do 具体操作
   ```

2. 遍历文件夹下的文件

   ```
   for /r "目录路径" %%v  in (匹配规则 例如*.py) do 执行操作 %%v
   ```

3. 遍历数字操作

   ```
   for /L %%v in (start, step, end) do 具体操作
   ```

4. 遍历文件内容操作

   ```
   for /f %%v in (文件名) do 具体操作
   ```



#### 8.Virus脚本分析

1. 目录重复新建代码分析``goto``

   ```
   :loop
   md Virus
   cd Virus
   goto loop
   ```



#### 9.编程实际案例

1. 计算机信息展示

   ```
   @echo off
   echo. > log.txt
   echo Log File >> log.txt
   echo. >> log.txt
   echo User: %username% >> log.txt
   Date /t >> log.txt
   Time /t >> log.txt
   echo. >> log.txt
   echo Process Ran by %username% >> log.txt
   echo. >> log.txt
   tasklist >> log.txt
   echo. >> log.txt
   echo Network Activities >> log.txt
   netstat -s >> log.txt
   exit
   ```

2. 交互操作介绍

   ```
   @echo off
   
   echo 1.a
   echo 2.b
   
   :first
   echo Enter your option:
   set /p opt=
   if %opt%==1 goto one
   if %opt%==2 goto two
   echo Invalid option
   goto first
   
   :one
   echo your choice one
   pause>null
   exit
   
   :two
   echo your choice two
   pause>null
   exit
   
   ```

3. 计划执行操作

   ```
   @echo off
   at 10:00 AM /every:SU,M,TU,W,TH,F,SA "C:\1.bat"
   pause>null
   exit
   ```

4. Bat批处理脚本转Exe程序介绍

   bat to Exe Converter工具

   





