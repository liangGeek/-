# Javascript设计模式
## 1. **单例模式**  
### 核心概念：  
确保只有一个实例，并提供全局访问。比如全局缓存、浏览器中window对象等。  
### 模型：  
```
var obj;
if ( !obj ){
  obj = xxx;
}
return obj;
```
### 高度抽象的单例模式代码，惰性单例的精髓：
```
var getSingle = function (fn) {
  var result;
  return function () {
    return result || ( result = fn.apply(this, arguments) );
  }
};
```
### 2. **策略模式**  
### 核心概念：
定义一系列的算法，把它们一个个封装起来，并且使它们可以相互替换。  
### 模型：  
```
var strategies = {
  A: fnA,
  b: fnB,
  ...
}
var calc = function(strategy, params) {
  return strategies[strategy](params);
}
```
### 优点：
* 策略模式利用组合、委托和多态等技术和思想，可以有效地避免多重条件选择语句。
* 策略模式提供了对开放-封闭原则的完美支持，将算法封装在独立的strategy中，使得它
们易于切换，易于理解，易于扩展。
* 策略模式中的算法也可以复用在系统的其他地方，从而避免许多重复的复制粘贴工作。
* 在策略模式中利用组合和委托来让 Context拥有执行算法的能力，这也是继承的一种更轻
便的替代方案。
### 缺点：
* 增加了许多策略类或者策略对象。
* 要使用策略模式，必须了解所有的strategy，违反了最少知识原则。