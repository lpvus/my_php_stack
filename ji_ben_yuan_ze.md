# 基本原则

## 单一职责原则（SRP）
不要存在多于一个导致类变更的原因。通俗的说，即一个类只负责一项职责。

## 开放封闭原则（OCP） 
定义：一个软件实体如类、模块和函数应该对扩展开放，对修改关闭。

场景：在软件的生命周期内，因为变化、升级和维护等原因需要对软件原有代码进行修改时，可能会给旧代码中引入错误，也可能会使我们不得不对整个功能进行重构，并且需要原有代码经过重新测试。

建议：当软件需求变化时，尽量通过扩展软件实体的行为来实现变化，而不是通过修改已有的代码来实现变化。

## 里氏替换原则（LSP） 
定义：子类可以扩展父类的功能，但不能改变父类原有的功能。

当使用继承时，遵循里氏替换原则。子类继承父类时，除添加新的方法完成新增功能外，尽量不要重写父类的方法，也尽量不要重载父类的方法。

## 依赖倒置原则（DIP） 
定义：高层模块不应该依赖低层模块，二者都应该依赖其抽象；抽象不应该依赖细节；细节应该依赖抽象。

例如，业务逻辑层相对于数据层是高层模块，因为业务逻辑层需要调用数据层去连接数据库，但是要做到可扩展高复用，尽量不要让业务逻辑层依赖数据层（如数据库类型mysql,pgsql），可以在数据层抽象出一个接口(如pdo)，让业务逻辑层依赖于这个抽象接口(统一操作数据库方法名)。

## 接口隔离原则（ISP）
定义：客户端不应该依赖它不需要的接口；一个类对另一个类的依赖应该建立在最小的接口上。

注意：

接口尽量小，但是要有限度。对接口进行细化可以提高程序设计灵活性 是不挣的事实，但是如果过小，则会造成接口数量过多，使设计复杂化。所以一定要适度。
为依赖接口的类定制服务，只暴露给调用的类它需要的方法，它不需要的方法则隐藏起来。只有专注地为一个模块提供定制服务，才能建立最小的依赖关系。
提高内聚，减少对外交互。使接口用最少的方法去完成最多的事情。

## 迪米特法则（LKP）
定义：一个对象应该对其他对象保持最少的了解。

场景：类与类之间的关系越密切，耦合度越大，当一个类发生改变时，对另一个类的影响也越大。

简单的理解就是高内聚，一个类尽量减少对其他对象的依赖，并且这个类的方法和属性能用私有的就尽量私有化。
