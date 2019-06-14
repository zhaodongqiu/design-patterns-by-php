### 第十一章 无熟人难办事 －－－ 迪米特法则

总结：

> ***迪米特法则***，如果两个类不彼此直接通信，那么这两个类就不应当发生直接的相互作用。如果其中一个类需要调用另一个类的某一个方法的话，可以通过第三者转发这个调用。

> 在类的结构设计上，每一个类都应当 尽量降低成员的访问权限

> 类之间的耦合越弱，越有利于复用，一个处在弱耦合的类被修改，不会对有关系的类造成波及。


上一章：[第十章 考题抄错会做也白搭 －－－ 模版方法模式](https://github.com/zhaodongqiu/design-patterns-by-php/blob/master/files/chapter10.md)

下一章：[第十二章 牛市股票还会亏钱 －－－ 外观模式](https://github.com/zhaodongqiu/design-patterns-by-php/blob/master/files/chapter12.md)