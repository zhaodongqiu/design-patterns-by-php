### 第十四章 老板回来，我不知道 －－－ 观察者模式

```php
<?php

/**
 * 事件产生类
 * Class EventGenerator
 */
abstract class EventGenerator
{
    private $ObServers = [];

    //增加观察者
    public function add(ObServer $ObServer)
    {
        $this->ObServers[] = $ObServer;
    }

    //事件通知
    public function notify()
    {
        foreach ($this->ObServers as $ObServer) {
            $ObServer->update();
        }
    }

}

/**
 * 观察者接口类
 * Interface ObServer
 */
interface ObServer
{
    public function update($event_info = null);
}

/**
 * 观察者1
 */
class ObServer1 implements ObServer
{
    public function update($event_info = null)
    {
        echo "观察者1 收到执行通知 执行完毕！\n";
    }
}

/**
 * 观察者1
 */
class ObServer2 implements ObServer
{
    public function update($event_info = null)
    {
        echo "观察者2 收到执行通知 执行完毕！\n";
    }
}

/**
 * 事件
 * Class Event
 */
class Event extends EventGenerator
{
    /**
     * 触发事件
     */
    public function trigger()
    {
        //通知观察者
        $this->notify();
    }
}

//创建一个事件
$event = new Event();
//为事件增加旁观者
$event->add(new ObServer1());
$event->add(new ObServer2());
//执行事件 通知旁观者
$event->trigger();
```
一句话概括

> 当对象间存在一对多关系时，每个子类都有一个接收通知的方法，父类改变某些信息时，通过这个方法接收信息。

总结：
> ***观察者模式***，定义了一种一对多的依赖关系，让多个观察者对象同时监听某一个主题对象。这个主题对象在状态发生变化时，会通知所有观察者对象，使它们能够自动更新自己。

> 将一个系统分割成一系列相互协作的类有一个很不好的副作用，那就是要维护相关对象间的一致性。我们不希望为了维持一致性而使各类紧密耦合，这样会给维护、扩展和重用都带来不便。

> 观察者模式所做的工作其实就是在接触耦合。让耦合的双方都依赖于抽象，而不是依赖于具体。从而使得各自的变化都不会影响另一边的变化。

上一章：[第十三章 好菜每回味不同 －－－ 建造者模式](https://github.com/zhaodongqiu/design-patterns-by-php/blob/master/files/chapter13.md)

下一章：[第十五章 就不能不换DB吗？ －－－ 抽象工厂模式](https://github.com/zhaodongqiu/design-patterns-by-php/blob/master/files/chapter15.md) 