# Javascript设计模式
## 1. **单例模式**  
### 核心：  
确保只有一个实例，并提供全局访问。比如线程池、全局缓存、浏览器中window对象等。  
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
定义一系列的算法，把它们一个个封装起来，并且使它们可以相互替换。  
