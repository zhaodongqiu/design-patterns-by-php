### 第一章 代码无错就是优 －－－简单工厂模式

1.简单工厂模式
```php
<?php 

/**
 * Operation 
 */
class Operation
{
    protected  $a = 0;
    protected  $b = 0;

    public function setA($a)
    {
        $this->a = $a;
    }

    public function setB($b)
    {
        $this->b = $b;
    }

    public function getResult()
    {
        $result = 0;
        return $result;
    }
}

/**
 * Add 
 */
class OperationAdd extends Operation
{
    public function getResult()
    {
        return $this->a + $this->b;
    }
}

/**
 * Mul
 */
class OperationMul extends Operation
{
    public function getResult()
    {
        return $this->a * $this->b;
    } 
}

/**
 * Sub
 */
class OperationSub extends Operation
{
    public function getResult()
    {
        return $this->a - $this->b;
    }
}

/**
 * Div
 */
class OperationDiv extends Operation
{
    public function getResult()
    {
        return $this->a / $this->b;
    }
}

/**
 * Operation Factory
 */
class OperationFactory
{
    public static function createOperation($operation)
    {
        switch ($operation) {
            case '+':
                $oper = new OperationAdd();
                break;
            case '-':
                $oper = new OperationSub();
                break;
            case '/':
                $oper = new OperationDiv();
                break;
            case '*':
                $oper = new OperationMul();
                break;
        }

        return $oper;
    }
}

// 客户端代码
$operation = OperationFactory::createOperation('+');
$operation->setA(1);
$operation->setB(2);
echo $operation->getResult() . PHP_EOL;
```


一句话概括
> 就是一个工厂，产生多个产品

> 出自 https://blog.csdn.net/xdrt81y/article/details/81100527

```php
简单工厂：一个工厂类，一个产品抽象类。生活中的
工厂方法：多个工厂类，一个产品抽象类。生活中的
抽象工厂：多个工厂类，多个产品抽象类。生活中的

二、生活中的工厂模式

简单工厂类：一个麦当劳店，可以生产多种汉堡。

工厂方法类：一个麦当劳店，可以生产多种汉堡。一个肯德基店，也可以生产多种汉堡。

抽象工厂类：百胜餐饮集团下有肯德基和百事公司，肯德基生产汉堡，百事公司生成百事可乐。
```

总结

> 学会通过分封装，继承，多态把程序的藕合度降低

> 复用，不是复制！

> 高内聚，低耦合



下一章：[第二章 商场促销 －－－ 策略模式](https://github.com/zhaodongqiu/design-patterns-by-php/blob/master/files/chapter2.md)
