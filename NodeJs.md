# NodeJs后端实习面试终结
 &#x1F4C2; 本人在找实习面试全栈的适合的一些小总结，也是面试官问的，现在回来回顾一下;
 &#x1F389; 主要是Nodejs+Express+MongoDB+Vue2/Vue3+ES6+JavaScript的一些基础知识，说不上难,但是是唯一检验你的程度的最好方法;
 
 ## &#x1F308;ES6的新特性有哪些&#x2753;
 1. let和const关键字：let声明变量，const声明常量。**块级作用域**；
<br>
2. 箭头函数：使用箭头（=>）语法定义函数，简化了函数的书写和this绑定。**箭头函数没有自己的this值，它继承外部作用域的this值，解决了传统函数中this指向的问题。**
<br>
 3. 类：引入了class关键字，用于定义类和面向对象编程的概念，包括构造函数、继承和方法等。
 <br>
 4. 模板字符串：使用反引号（`）包裹，可以在字符串中插入变量和表达式，同时支持多行字符串。
 <br>
 5. 解构赋值：可以从数组或对象中提取值，并赋给变量，简化了变量的声明和赋值。
 <br>
 6. 默认参数：在函数定义时可以为参数设置默认值，简化了函数调用时的参数传递。
 <br>
 7. 扩展运算符：使用三个点（...）可以将一个可迭代对象（如数组）展开为多个元素，或者将多个元素合并为一个数组。
 <br>
 8. Promise：用于处理异步操作的对象，提供了更方便和可读性更好的方式来处理回调函数。
 <br>
 9. 模块化：通过import和export关键字，支持模块化的开发方式，可以将代码分割成多个文件，提高代码的可维护性和复用性。

 ## &#x1F308; 既然你提到了类，那么我想问一下，JavaScript中的构造函数也是用new来实例化对象的，两者有什么区别吗&#x2753;
 1. 语法差异
    * 构造函数：构造函数是一种特殊的函数，使用关键词`function`定义，并以大写字母开头。在构造函数内部使用`this`关键字来定义实例化对象的属性和方法；
    * 类：类是ES6引入的新语法，使用关键字`class`定义，可以包含构造函数、实例方法和静态方法。类的实例化使用`new`关键字； 
 <br>
 2. 继承机制
    * 构造函数：通过原型链实现继承，使用`prototype`属性和`prototype`链来共享方法和属性；
    * 类：通过`extends`关键字和`super`关键字实现继承，可以使用`extends`关键字继承另一个类，并使用`super`关键字调用父类的构造方法和函数；
 <br>
 3. 类的特性
    * 类支持静态方法和静态属性，而构造函数没有直接的语法支持静态成员(**静态属性、静态方法**)；
    **静态属性**
    ```JavaScript
    class Student{
        static count=0;     //类自己的属性
        constructor(name){
            this.name=name;
            Student.count++;
        }
    }

    const student1=new Student('Mika');
    const student2=new Student('linghucong');
    ```

    **静态方法**
    ```JavaScript
    class Student{
        static add(a,b){
            return a+b;
        }
    }

    console.log(Student.add(1,2));  //3
    ```
    * 类中方法默认使用严格模式，构造函数中的方法不会自动启用严格模式。
 <br>
 4. 原型和实例
    * 构造函数：每个实例对象都有一个指向构造函数的原型链，可以通过原型链访问构造函数的属性和方法；
    * 类：类实例对象也有一个指向类的原型链，但是类的实例方法直接定义在类的原型上，而不是对象的实例上。

## &#x1F308;Vue2和Vue3的区别，为什么要出Vue3&#x2753;
1. 有更快的渲染性能：Vue3使用新的响应式系统，利用了==Proxy==对象和更加精确的依赖和追踪，从而提高了渲染性能；
🔥 **两者：** 首先我们要知道Vue2用的是 ==Object.defineProperty==，他监听的是整个对象，无论是访问还是修改，都是深度遍历。但是==Proxy==监听的是对象，而不是对对象每个属性逐一监听，这使得Vue3在响应式数据的访问和修改上更加高效；<br>
🔥 **相比之下** `Object.defineProperty`只能对已经存在的属性监听，不能监听属性的添加和删除，而且对于数组的变化需要额外的处理，而`Proxy`的出现就很好的解决这一问题；<br>
🔥 **Proxy：**
    ```javascript
    const obj={...}
    const proxy=new Proxy(obj,{
        get(target, property, receiver){
            //拦截对属性的操作
        },
        set(target, property, value, receiver){
            //拦截对属性的赋值操作
        },
        has(target, property){
            //拦截in运算符
        },
        deleteProperty(target, property){
            //拦截delete运算符
        },
        construct(target, argumentsList, newTarget){
            //拦截类的实例化操作
        }

    })
    ```
2. 更小的体积包：Vue3经过重新的设计和重构，使得核心库的体积更加小，同时提供了更好的**<font color="blue">Tree-shaking</font>**支持；<br>
3. **Composition API**：引入了一组新的函数式 API，例如 ```reactive、computed、watch``` 等，以及 ```setup``` 函数用于组件的逻辑组织。

## &#x1F308;使用vuex状态管理浏览器每次刷新都会被清空怎么解决这个问题&#x2753;
1. **利用路由守卫**：可以在路由切换时，将 Vuex 的状态保存到浏览器的本地存储。在路由切换完成后，再从本地存储中读取并恢复状态。可以使用 **beforeEach** 和 **afterEach** 路由守卫来实现这个过程。

## &#x1F308;那么Vue-router4中的hash和history路由有什么区别&#x2753;
1. URL格式：hash模式使用URL中的哈希部分(#)来模拟路由，例如`http://example.com/#/home`,而 history 模式使用 HTML5 的 History API，不需要哈希部分，例如 `http://example.com/home`。
<br>
2. 兼容性：*hash*模式在所有浏览器中都能正常工作，包括老版本的浏览器。而 *history* 模式需要浏览器支持 **History API**，对于不支持的浏览器，**会自动回退到 hash 模式**；

## &#x1F308;用户在图片上传的时候，突然断网了，后续断网了用户怎么继续维持断网前的状态继续上传&#x2753;
1. 断点续传：在客户端实现断点续传的功能，即将上传的文件分成多个小块进行上传，每次上传完成后记录已上传的位置，当网络中断后，重新连接后可以从上次中断的位置继续上传。这需要在客户端和服务器端都进行相应的实现；
<br>

2. 上传队列：在客户端实现上传队列的功能，将所有待上传的文件加入到队列中，每次上传完成后再继续上传下一个文件。当网络中断后，可以在重新连接后继续处理上传队列中未上传的文件。
<br>

3. 上传断点记录：客户端在上传过程中，可以将已上传的数据记录下来，并保存在本地，例如使用本地存储或者数据库。当网络重新连接后，客户端可以读取保存的记录，并继续上传未完成的部分。