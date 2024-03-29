# SIMS
> 基于java Swing + I/O的一个增删查改的学习信息管理系统
### 说明
##### jar包问题
* 文件中导入了两个包用来做柱状图：`jfreechart-1.0.2.jar;jcommon-1.0.21.jar`
* 所以在运行之前应该先下载并导入这两个jar包
##### 运行
* 可以通过IDE重新编译，不过还是那句话**需要导入两个jar包**
* 也可以通过命令行运行out目录里的`.class`文件，命令是 `java -classpath E:\SIMS\out\production\SIMS;E:\..自己jar包的位置..\jar\jfreechart-1.0.2.jar;E:\..自己jar包的位置..\jar\jcommon-1.0.21.jar view.LoginRun`
* view包里的loginRun.class是可运行的
##### 登录
* 通过root登录，密码是123456

### 功能

##### 安全
* 分为管理员root和普通学生
  * 学生
    * 查询成绩
    * 修改自己的登录密码
  * root
    * 修改所有人的登录密码
    * 对学生信息增删查改
    * 查看学生分析图表
    * 查看登录日志
* 验证码
    * 对于每次登录都需要输入验证码
    * 验证码背景有多达数十种线条和色彩进行干扰，有效防止机器爆破
* 日志
    * 管理员可以通过日志查询该系统的使用情况
    * 日期 — 对象 — 操作 — 对象
    * 操作包括
      * 增加
      * 删除
      * 登录
      * 退出
      * 查询
      * 修改
* 注册系统
    * 后台逻辑严密，只允许有成绩的学生注册
    * 当账号存在于后台成绩数据时才能注册
##### 方便
* 学生的Id是主码，不可重复
* 登录
  * 登录窗口和注册窗口都有密码核查功能
  * 验证码
  * 多用户
* 管理
  * 用户信息
    * 查看用户权限
    * 退出
  * 学生管理
    * 查看&修改&添加&删除学生登录密码
    * 查看&修改&增加&删除学生成绩
    * 通过柱状图对学生成绩进行分析
  * 帮助
    * 把本地的操作手册映射到窗口中
    * 管理员查看日志
* 删除信息
  * 一种方式是选中表格中的一行，进行删除
  * 另一种方式是点击删除按钮，输入ID进行删除
  * 此时时级联删除，当删除了学生成绩后，学生的注册信息也会被删除
  * 即被删除的学生登录不上该系统，即使ta之前注册过
* 修改信息
  * 修改登录的密码
  * 修改成绩，姓名，性别等一切除了ID之外的信息
* 查找
  * 可以只通过ID查询
  * 也可以通过性别，班级，姓名多个条件任选几个进行查询
* 成绩分析
  * 系统自动给出各个学生的GPA，并按照GPA由由高到低排序
  * 有专门的各个班级成绩分析系统的集成
  

#### 收获
- 最遗憾的是在写程序之前没有看设计模式，只是在有了一点思路就开始写，然后最后随着思路的不断成熟，程序不断重构，难过
- 以前总觉得学软工导论没啥用，看来这次要改变观点了
- 刚开始还不知道用字节流还是字符流存文件，为了清楚最初用了字符流，但是到最后发现我的IDEA是“UTF-8”，但是系统是GBK，一直爆乱码，Google之后渐渐锁定了问题，就在字符流前面加了一层字节流先强制转换编码
- 后端的增删查改代码有一点冗余，刚开始应该设一个接口，然后再加上泛型，但是等自己发现的时候已经来不及了，那时候已经写了2k+行了
- 由于Swing的格式参照核心卷1上来写，照猫画虎，解耦合比较好，但是又产生了变量无法共享的问题，只能设了好多的全局变量
- 锻炼了自己快速学习的能力，Swing3天掌握，边调用API边查，还导入了一个关于柱状图的包，查阅oracle官网的java11API等等
- 最恶心人的就是编码问题了，刚开始一直乱码，Google了好长时间，还是因为I/O掌握的不好，不过现在完全解决
- 但是发现自己还是太天真了，Jdk自带的一个命令具有规定编码555：`-Dfile.encoding=UTF-8`
- 对集合类又复习了一遍
- 这次确实把MVC运用到了程序当中，程序整体的解耦合还是蛮可以的
- 再一次学习了反射等等，然后也在swing中运用了lambda
- 对idea的操作更加熟悉
- 因为安装了阿里的编码约束插件，经过这近3k行代码的编写，编码更加规范，写完这个程序以后，感觉之前写的程序就是坨x
- 锻炼了自己锁定并解决问题的能力，有些模棱两可的问题直接查官方文档，有时候就会迎刃而解。官方文档可能并不适合初学者学习，但它作为一种工具文档还是绰绰有余
- 有些时候需要直面问题，它并没有想象的那么可怕

