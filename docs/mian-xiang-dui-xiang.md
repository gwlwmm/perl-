# 为何用面向对象

仅从perl语言来看，在大型工程应用中，perl官方社区推荐的最佳实践是使用其面向对象编程。

# perl中的面向对象

要初步掌握perl面向对象的编程特性，请仔细阅读：[https://perldoc.perl.org/perlobj.html](https://perldoc.perl.org/perlobj.html)

# 扩展

面向对象编程是软件开发中的一种编码实现方式， 不只是perl语言。 仅仅学习perl语言的面向对象的一些语法或关键词，**并不能写好面向对象的代码**。

## 建议

* 面向对象的哲学核心在于抽象总结。对抽象总结，有很多种方法，如果您没有任何这类抽象总结的经验，有这样一个简单的建议：

* 对于多个事物，如果同属于某个集合，可以抽象一个集合类。例如身份证、账户余额、姓名，都属于某个客户，那就抽象一个客户类。

* 对于多个事物，如果有共同点，可以提取一个公共类。例如服务器需要接收数据，客户端需要发送数据，而在这个行为上有一个共同点，即客户端和服务器都要处理相同的数据（通常把这个叫做通信协议），因此可以抽象一个协议类。

* 对于任何时候，优先思考封装，例如需要设定一个永久变量，优先考虑作为类成员，而不是全局变量。

* 对于任何时候，优先思考局部化，即将大问题逐步分解。例如写一个服务器时，需要响应请求并处理请求，在编码时，应该将处理请求的整个过程作一个完整推演，并作为一个持续性编码任务，然后再逐个编码请求内容的处理细节，如果处理过程中有需要做数据存取，则又将数据存取作为持续性编码任务，通常这种思维叫做分层。非局部化的思维是：直接编码接受请求并处理请求。上述例子中就是把请求响应过程做逐步分解，而之所以要分层编码，是要编码者对各层严格定义输入输出，简化各个处理逻辑。

* 对接口编程，而不是对实现编程：如管理配置文件模块设计时，需要解析配置文件的内容，得到固定格式的配置结构表示，而配置文件内容有好几种形式（json、ini、...）。此时对接口编程的做法是，设计一个配置解析类，提供解析的接口，管理模块只调用该类的解析接口；对实现编程的做法是，管理模块里区分配置文件类型，调用不同的配置文件解析类。总而言之，当上层模块出现一类调用需求时（本例中是配置解析），需要进一步抽象为统一的接口，由接口内部实现具体的处理分类。

* 优先考虑对象组合，而不是继承：有一个通讯接口类，现在要增加另一种通讯协议，使用该通讯接口传递数据。继承的做法是：新建一个通讯协议类，继承自通讯接口类，再实现通讯协议；对象组合的做法是：新建一个通讯协议类，使用通讯接口类实例化一个对象，作为通讯协议类的类对象成员。

* 面向对象设计是一件伤神但是又很快乐的事情，往往一不留神，设计不合理就会引来诸多维护难题。已经有人总结了若干最佳实践，书名叫《设计模式》，其将事物分围三个大类：创建、结构、行为。 各个事物始于创建，若干事物在特定问题里组成了结构，而后这些事物会发生行为。值得一提的是，如果没有太多面向对象编码经验去看这本书，会理解地云里雾里。但是建议顺着思路做一些思考，以便在未来面向对象编码的道路上能对自己有一些约束力。当完成一些设计后，针对遇到的设计问题，将《设计模式》当成手册来查询，以寻找最佳设计。如此反复提升。

* 学会画图和看图，在表达面向对象设计时，常用uml建模：

[http://www.uml.org.cn/oobject/201211231.asp](http://www.uml.org.cn/oobject/201211231.asp)

[http://www.cnblogs.com/wolf-sun/p/3420120.html](http://www.cnblogs.com/wolf-sun/p/3420120.html)

上述链接介绍了大部分uml知识，但要想真正掌握，还是要靠练习，即多看、多画。

