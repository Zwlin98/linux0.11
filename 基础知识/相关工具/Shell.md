## GNU/Linux Shell

### 标准输入/输出/错误

-----

+ 标准输入`stdin`

+ 标准输出`stdout`

+ 标准错误 `stderr`

+ 重定向 `>`

----------------------------

#### 用于标准I/O的文件描述符

| 描述符 |       说明        |
| :----: | :---------------: |
|   0    |  标准输入`stdin`  |
|   1    | 标准输出`stdout`  |
|   2    | 标准错误 `stderr` |

#### 举例应用

```shell
prog > out
#标准输出重定向
prog >> out
#将输出信息添加到文件后
prog 2> err
#标准错误重定向
prog 1> out 2>&1
#将stdout，stderr重定向到同一文件
prog 1> &2
#将stdout重定向到sterr
prog 1> out 2>err
#将stdout和stderr分别重定向
prog 2> &1 1>out
#将stdout，stderr重定向到同一文件
```

### 环境变量

环境变量是包含信息的命名对象，这些信息由shell和其他应用程序使用，由很多标准环境变量，也可以为应用程序创建自己的环境变量(或改变已经存在的环境变量)。

#### Linux环境变量分类
+ 按照生命周期来分，Linux环境变量可以分为两类：
  - 永久的：需要用户修改相关的配置文件，变量永久生效。
  - 临时的：用户利用export命令，在当前终端下声明环境变量，关闭Shell终端失效。
+ 按照作用域来分，Linux环境变量可以分为：
  - 系统环境变量：系统环境变量对该系统中所有用户都有效。
  - 用户环境变量：顾名思义，这种类型的环境变量只对特定的用户有效。

#### Linux设置环境变量的方法

+ 在`/etc/profile`文件中添加变量 **对所有用户生效（永久的）**
   用vim在文件`/etc/profile`文件中增加变量，该变量将会对Linux下所有用户有效，并且是“永久的”。
   例如：编辑/etc/profile文件，添加CLASSPATH变量

```shell
  vim /etc/profile    
  export CLASSPATH=./JAVA_HOME/lib;$JAVA_HOME/jre/lib
```

​	注：修改文件后要想马上生效还要运行`source /etc/profile`不然只能在下次重进此用户时生效。

+ 在用户目录下的.bash_profile文件中增加变量 **对单一用户生效（永久的）**
   用`vim ~/.bash_profile`文件中增加变量，改变量仅会对当前用户有效，并且是“永久的”。

```shell
vim ~/.bash.profile
export CLASSPATH=./JAVA_HOME/lib;$JAVA_HOME/jre/lib
```

​	注：修改文件后要想马上生效还要运行$ source ~/.bash_profile不然只能在下次重进此用户时生效。

+ 直接运行export命令定义变量 **只对当前shell（BASH）有效（临时的）**
   在shell的命令行下直接使用`export 变量名=变量值`
   定义变量，该变量只在当前的shell（BASH）或其子shell（BASH）下是有效的，shell关闭了，变量也就失效了，再打开新shell时就没有这个变量，需要使用的话还需要重新定义。

#### 相关命令

```shell
export
#设置一个新的环境变量 export HELLO="hello" (可以无引号)
echo
#显示某个环境变量
env
#显示所有环境变量
set
#显示本地定义的shell变量
unset
#清除环境变量 unset HELLO
readonly
#设置只读环境变量 readonly HELLO


```

### Shell 命令

各个shell命令使用方法参见man手册，谷歌，网上相关教程。

### Shell 脚本

[参考链接](https://legacy.gitbook.com/book/tinylab/shellbook/details)