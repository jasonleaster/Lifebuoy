# Lifebuoy 
菜鸟生存指南  (引到初入职场的同学了解常用的开发工具和技术点)

以下内容如果能在大学期间掌握更好，希望下面的一些小建议能帮助到你。


### 救生员第一定律
用英文简洁的表述你的问题，然后Google
### 救生员第二定律
对流传的解决方案保持怀疑，不可轻信，考虑方案存在的潜在问题
### 成为Nice的同事
* [学会问正确的问题](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way)
* 做技术终究要结合业务逻辑，技术服务于业务的，深入研究熟悉技术，提升开发效率和能力也是为了更好的服务于业务，也不能一味的抛弃技术思考，这样会设计方案的可行性终究要考虑在有限的时间内技术实现难度。
* 一个项目不只有代码，不仅仅有程序实现人员，还有市场支撑、产品设计等等其他项目成员

## Git 代码版本工具的使用

知道为什么需要版本控制？了解并体会Git工具是通过哪些基础的操作实现版本控制的需求，这样会让你更深刻的理解Git等版本控制工具
* [Git 实验室](https://learngitbranching.js.org/)
* [猴子都能懂的Git](https://backlog.com/git-tutorial/cn/)
* [Git 官方文档](https://git-scm.com/book/zh/v2)

常见毒瘤:
1. 请不要将IDE相关配置文件提交，任何文件一旦加入到git版本控制跟踪后，再去.gitignore添加该文件，祈求忽略该文件是无效的。一旦加入，无法忽略，除非你删除该文件。
2. 请不要随意修改包名或者删除文件，极易导致代码覆盖。

推荐: 创建一个实验性的Git项目，通过命令行完成并体会基础的版本控制操作。  
进阶: 了解Git的hooks机制，并尝试编写脚本，实现自定义版本控制工作流，做一些hack style的事情。同时建议深入了解[git对象原理](https://blog.csdn.net/i_enum/article/details/50557367)。  


## 开发工具
Java开发: Intellij IDEA 社区版.  不能像企业版一样自动发布到Tomcat，但是自己用Maven打个war包，部署至Tomcat的webapp目录，手动启动Tomcat也一样。社区版用的是ApacheLicense，不会担心由于版权问题公司层面禁止使用的问题。[Stack Overflow 关于Intellij Idea社区版用于商业公司开发的讨论](https://stackoverflow.com/questions/21967174/intellij-community-edition-for-work-in-company).

C语言开发: Vim + gcc + gdb 

Redis Desktop Manager Redis管理客户端  
MySQLWorkbench MySQL数据库管理客户端  
Wireshark 网络抓包分析利器  

## 包管理工具
软件可复用的重要形式之一就是直接使用(引用)别人编写的代码，而如果认为手动的管理公开的软件包会带来很多问题，因此衍生出“集中式”包管理工具。如下:
* Maven  [maven-in-five-minute](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html) 认真冷静的读完这个Guider。

我初次接触Maven是在2015年，记得当时非常不理解为什么要有这个东西，pom.xml （Project Object Model）文件有什么用？为什么不用JSON文件，xml很难看。Don't Panic ! 他就是个配置说明文件，一个星期，半个月你就熟悉了，如果连Java都没写过，可能需要更久，但是这是客观规律，急也没有用。

* Gradle 与Maven类似的包管理工具(了解即可)。

* npm (Node Package Manager)
 前端开发越来越工程化的时候就衍生出越来越多辅助工具了，npm也是这个过程中的产物。  
* pip python的包管理工具

## 熟悉Linux下的开发和维护方法

除了常用的cd、ls、cat命令之外，还要了解包括但不限于以下工具或命令:

* top 根据CPU消耗、内存占用率对进程进行排序
* grep
* ps
* kill 强制杀死进程之前考虑杀死进程会带来什么后果，切记。例如，锁、连接等是否能正确释放，如果不能请考虑正确结束程序的方式。
* scp Linux机器之间通过网络传输文件拷贝
* tmux 了解简单常用的分屏操作
* ssh 登录远端的机器
* netstat 本地网络端口使用统计情况
* tcpdump tcp抓包分析
* ipcs
* ipcrm

通过cat了解通过proc系统获取进程或系统相关信息。

如果`Linux鸟哥的私房菜`都没有读过几遍的建议抽时间多读读。并且了解Linux系统的架构。

## 开发编码建议

梁飞说过一段话我一直觉得非常棒，在此推荐

> 敲每个点号时，考虑：  
会不会出现空指针?  
有没有异常抛出?  
是不是在热点区域? 
在哪个线程执行?  
有没有并发锁间隙?  
会不会并发修改不可见?  
`-- 梁飞`

* 机器的资源始终是有限的, 关于程序需要消耗的资源使用要有预估，否则低级的性能问题由此而生 
* 团队引入`CheckStyle`、`FindBugs`、`JSLint`、[Sonar](https://www.sonarsource.com/plans-and-pricing/community/)等静态检查工具 
* **反复阅读并掌握** 《阿里巴巴Java编程规范》, 任何违反该规范的开发人员都是trouble maker。 

* 了解如何通过tcp端口远程调试java服务
 -Xdebug -Xrunjdwp:transport=dt_socket,suspend=n,server=y,address=8889

* [了解常见的HTTP响应状态码快速定位问题](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81)

* -Xmx 参数指明jvm运行时动态申请的最大堆内存，合理的规划部署机器确保对应的java进程能够用到足够的内存资源，Xmx仅是声明式的参数，而非抢占式的。  
gc日志永远都是我们排查gc问题最好的工具，所以强烈建议大家在线上配置-XX:+PrintGCDetails -Xloggc:/data/logs/gc.log

* [JAVA 常见问题排查方法](https://github.com/fujohnwang/wonderful-slides/blob/master/Java%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98%E6%8E%92%E6%9F%A5%5B%E6%AF%95%E7%8E%84%5D1397440786.pdf)

* [内存泄露的例子了解一下](https://gist.github.com/djangofan/2713839)

* 关于线程池队列的选择 http://hellojava.info/?p=13

* 数据库分页查询Tips
分页查询是个常用的功能，对于MySQL需要join很多表的情况，首先尝试优化SQL，并创建相应的索引如果实在还是不行，那就去将原来A、B、C、D、E、F等多个表join的情况先做”小范围的分页，再去join“，比方说分页的关键在于A B两个表，我们可以先将ABjoin的结果分页，再去做剩下表的join，”过滤核心数据，再做数据查询，减少数据查询的规模“。  
分页查询时先用子查询把数据规模最大的那张表的主键查出来，然后再和其他从表join. 参考Java开发规范，索引规约，第七条  
我做过MySQL数据库单表700w+规模数据的分压查询方案设计和实现，记录的总条数有时候是没有必要的，用户有时候不比执着于最后一页，分页查询的本质就是从海量数据中取少量数据做视察，参考业界搜索引擎的查询结果展示一般只会展示10页，把相关性强的有限展示出来。

* Mapper开发规则  
让MyBatis-Spring完成自动扫包，而不要去MyBatis的Configuration中自己去配置添加Mapper  
在mapper.xml中将namespace设置为mapper.Java的全限定名  
将mapper.java接口的方法名和mapper.xml中statement的id保持一致  
将mapper.java接口的方法输入参数类型和mapper.xml中statement的parameterType保持一致  
将mapper.java接口的方法输出 结果类型和mapper.xml中statement的resultType保持一致  

* Tomcat 
Tomcat 进阶 https://www.ntu.edu.sg/home/ehchua/programming/howto/Tomcat_More.html

* [面向对象三大特征、五大原则](https://blog.csdn.net/jiyiqinlovexx/article/details/46593053)

* [技术文档编写规范](https://github.com/ruanyf/document-style-guide)

## MySQL 数据库相关

* [MySQL各种不同语句执行落锁的情况](https://dev.mysql.com/doc/refman/5.7/en/innodb-locks-set.html)

* [自增长情况的处理说明](https://dev.mysql.com/doc/refman/5.7/en/innodb-auto-increment-handling.html)

* [explain的使用说明](https://www.slideshare.net/phpcodemonkey/mysql-explain-explained)

* [如何设计一个MySQL的索引, 这是我见过最好的文档，没有之一](https://www.slideshare.net/billkarwin/how-to-design-indexes-really)

* [实际工作中如何理解、运用数据库范式](http://kimi.it/418.html)

* [关于 mysql int(X)中X的理解](http://kimi.it/175.html)

* [淘宝数据库主备实践](http://mysql.taobao.org/monthly/2018/06/03/)

* [关系型数据库如何工作的](https://www.kancloud.cn/devbean/how-databases-work/145503)

* [Isolaion 隔离性](https://en.wikipedia.org/wiki/Isolation_(database_systems))

* JAVA 中数值对象都是有符号的，因此建议所有MySQL字段都声明为有符号的，特别是BigInt类型的数据库字段，否则会出现BigInt会无法映射到long类型而抛异常。

## 前端开发
* [JS 秘密花园](http://bonsaiden.github.io/JavaScript-Garden/zh/#object.forinloop)
* [JS6 入门](http://es6.ruanyifeng.com/?search=import&x=0&y=0)
* [最棒的CSS选择器实践](https://flukeout.github.io/)
* [CSS 布局](http://zh.learnlayout.com/)
* [`单线程`的JS如果处理多个任务 -- JavaScript 事件循环](https://vimeo.com/96425312)
* [chrome 浏览器开发说明文档才是最好的学习指南](
https://developers.google.com/web/tools/chrome-devtools/)
* [JS 的 new 到底是干什么的?](https://zhuanlan.zhihu.com/p/23987456?refer=study-fe)
* [跨域问题分析](https://amyfoxfn.github.io/amy-blog/)
* [fouber 的博客](https://github.com/fouber/blog)

## 管理好你的工作站

如果你的日常开发机器都一片混乱，想必你的开发效率和质量都很难得到保障。

学会管理好自己的工作站，不管是windows、Linux还是Mac，目录文件夹的分布和命名清晰合理是相当重要的，会对工作效率提升多很。磁盘的合理利用，比方说是不是C盘就被撑爆了。建议合理的做软件分类，开发软件、办公软件、开发代码、会议文档等等，按照特定属性属性特征，归纳放置，不要使用`文件夹1`、`文件夹2`类似的命令方式，这是非常糟糕的，就像编码变量名命名一样，好的程序肯定少不了一个直观表意的变量名，除了你其他人也应该能很快速的理解你的思路，否则过了一段时间你也会弄混的。

## 关于程序性能与开发效率的平衡

> It is always a good practice first to make your code right, and then make it fast. Even then, pursue optimization only if your performance measurements and requirements tell you that you must, and if those same measurements tell you that your optimizations actually made a difference under realistic conditions.

----

![images](/src/images/img_0179.jpg)

TODO 未完待续 : ) 2018.08.04 updated