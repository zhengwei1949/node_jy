# 代码下载地址

[下载链接](https://github.com/zhengwei1949/node_code_new)

# 为什么要学习Node.js
- 学会es6语法

```javascript
//下面这段代码是什么含义
const foo = ({hello:{world:bar}})=>({bar});
```
- 在以后使用vue.js,angular.js,react.js，包括webpack,gulp之类的构建工具的时候，能够更好的看懂里面的代码和参数配置项
- 了解后端在做什么(我们在课程的后半部分会用前后端混写+前后端分离两种方式写一个小的展示型网站)
- 在没有后端帮助的情况下自己给自己写测试接口(有些小一点的公司如果人数不够有可能接口需要自己来模拟)
- 为简历加分
- todo:讲一下如何结合node.js和微信公众号进行开发项目

# 推荐编辑器
- vsCode(适合电脑内存小)
    + 开源，来自微软公司
    + 全平台支持(linux,mac,windows)
    + 便于调试代码
    + 代码出错了可以即时看到错误提示
    + 安装插件超级方便(开箱即用)
    + 默认中文，无需汉化破解
- webstorm(适合电脑内存大)
- https://github.com/zhengwei1949/myblog/issues/60


## 常用操作推荐
- 分屏(左侧老师代码，右侧自己的代码对比着练习)

# 课前预习
- 《Node.js前置知识.doc》 <-- 晚上的时候可以看一看

# 课程主线
- Node.js基础知识、模块化、es6 **
- 文件操作、npm与包 **
- 开发网站(主要为了了解原理，以后不会这样写代码的) **** 
- express框架 + mysql数据库(重、难点) ****

# day01
## 课程主题
- Node.js基础
- Node.js模块化相关
- ES6相关

## 01-Node.js基础 - 初识Node.js 15:57
### 问题
1. Node.js到底是一个什么东西?
2. Nodejs主要是用来干什么的?

### 总结
1. Node.js如何理解
为什么电影格式的文件可以播放 --> 播放器引擎 --> 只要有js引擎的东西就可以执行js文件 --> 浏览器是常见的js执行环境 --> Node.js也一个js执行环境
2. Node.js应用(课程中主要涉及到)
    - 做网站、写api接口
    - 命令行工具(比如gulp,webpack等)

## 02-Node.js基础 - 终端基本使用 14:03
### 总结
1. 打开应用(不用记，这块用得不多)
    - notepad 记事本
    - mspaint 画图
    - calc 计算器
    - write 写字板
    - sysdm.cpl 打开环境变量设置窗口
2. 常用命令(不用记，这块用得不多)
    - md或mkdir 创建目录(推荐掌握)
    - rmdir(rd) 删除目录、目录内必须没有文档
    - echo on a.txt 创建空文件
    - del 删除文件
    - rm 文件名 删除文件
    - cat 文件名 查看文件内容
    - cat > 文件名 向文件写内容
3. 注意
- 这几个名词，指的是同一个意思：命令行、DOS、控制台、终端、terminal
- 终端如果嫌字太小，可以调节(把鼠标放到状态栏 --> 右键 --> 属性)
4. 常用的命令(视频没有，我加的)
    - 换盘符: D:、C:
    - 列出当前目录下的文件及文件夹: dir
    - 退回上一级目录：cd .. 或者 cd ..\
    - 保持原样: cd .
    - 退回盘符根目录:cd \
    - 退出命令行:exit
    - 清屏:cls
    - ipconfig /all

## 03-Node.js基础 - 环境安装配置 24:16(不讲、慎操作(如果你电脑有尽量不要尝试否则会出问题))
### 总结
1. 普通安装方式
2. nvm(不推荐，在win10有的win7电脑上测试过有bug 参考https://cnodejs.org/topic/580ad5b605dbe08f50be31f7)
3. 推荐安装稳定版即可，版本太低必须要升级，6.1.10以上即可,否则对es6支持程度太差

## 04-Node.js基础-代码执行顺序 12:13
### 前置问题
- 如何在浏览器端执行js代码?

### 总结
- repl方式
- 执行文件的方式
    1. 创建一个js文件(不要用中文、文件名不要起得太特殊)
    2. 按住shift键+在当前文件夹右键打开命令行工具
    3. 输入`node 文件名.js` 

## 05-Node.js基础 - 全局成员概述 15:12
### 前置问题
- js由哪三部分组成?

### Node.js特有的api
- __dirname(掌握),__filename(了解即可)

```javascript
//包含文件名的全路径
console.log(__filename);
//当前文件的路径
console.log(__dirname);
```

- global全局对象

```javascript
//global相当于浏览器端的window
global.console.log(123);
global.setTimeout(function(){
    console.log(666);
},1000);
```

> 注意点：global：表示Node所在的全局环境，类似于浏览器的window对象。需要注意的是，如果在浏览器中声明一个全局变量，实际上是声明了一个全局对象的属性，比如var x = 1等同于设置window.x = 1，但是Node不是这样，至少在模块中不是这样（REPL环境的行为与浏览器一致）。在模块文件中，声明var x = 1，该变量不是global对象的属性，global.x等于undefined。这是因为模块的全局变量都是该模块私有的，其他模块无法取到。


- process.argv(了解)

通过做一个命令行加法计算器的demo(体会一下process.argv的作用)

```javascript
//执行方式: node 文件名.js 1 2 3 和prompt进行类比记忆
//argv是一个数组，默认情况下，前两项分别是：Node.js环境的路径、当前执行的js文件的全部路径
console.log(process.argv);
``` 

## 06-Node.js基础-初识模块化 13:30

掌握模块化只需要掌握三大块：如何创建一个模块+如何把当前模块的属性或方法导出（暴露）出去+如何引第三方模块(可以复习一下require.js代码)

### 模块化规范
- amd --> require.js
- cmd --> sea.js
- es6规范
- commonjs --> node.js
- 相关文章
    + http://www.ruanyifeng.com/blog/2012/10/javascript_module.html
    + http://island205.github.io/HelloSea.js/getting-started.html


1. 如何创建模块：在Node.js中一个文件就是一个模块
2. 如何把当前模块的属性或方法导出（暴露）

```javascript
//导出
var sum = function(a,b){
    return parseInt(a) + parseInt(b);
}

exports.sum = sum;

//或者
module.exports.sum = sum;
```

3. 如何引第三方模块

```javascript
//导入
var calc = require('./calc.js');
```

## 07-Node.js基础-模块成员导出详解 15:45
- 本质上用的是module.exports
- 快捷方式：exports
- 类比：和对象的引用很像
```javascript
var obj = {name:'itcast'};//类比module.exports
var obj1 = obj;//obj1类比exports
```

- 以module.exports为准
- 用exports的时候记得一定不要直接让exports等于谁，这样会改变地址指向
- 永远只用module.exports就永远不会出错

### 注意
以exports导出的模块的话，导出什么就能用什么，没导出的就不能用

## 08-Node.js基础-模块化细节补充
- 利用global实现文件(在Node.js中一个文件就是一个模块)间共享数据 --> 不推荐这样玩，不好，容易造成全局变量污染和全局global挂太多变量，了解即可
- js扩展名后缀可以省略的(尽量不要省，性能更好一些)
- 模块文件有三种类型：js代码文件>json代码文件>node代码文件(c++编译成二进制的代码)
- 模块分类：(类比jquery的内置插件和第三方插件)
    + 自定义模块
    + 内置模块:fs,path,http...

### 补充：
#### node架构理解
- 和jquery很像，核心(core) + 扩展
- 目的：为了最好的性能减少冗余代码

#### 如何使用path内置模块
- 为什么要使用path.join
我们如果想拼一个路径的话，如果是windows电脑，中间用\隔开，如果是mac,则是用/隔开，所以在拼路径的时候，没办法实现同一套代码
在mac,windows共用，所以，可以考虑使用path.join

![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-28/29628469.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-28/31222427.jpg)

```javascript
console.log(path.join('a','b'));
```

- path.extname

```javascript
console.log(path.extname('a.js'));
console.log(path.extname('a.html'));
```

```javascript
var path = require('path');
```

- path.resolve
    + 返回值是一个绝对路径
    + path.join(__dirname,'a.js')和path.resolve(__dirname,'a.js')是一个意思

### require(这里面的叫模块标识符)
- 如果是绝对路径,并且带扩展名(.js,.json,.node) --> 去找对应的文件
- 如果是绝对路径，不带扩展名 --> .js > .json > .node
- 如果是相对路径,,并且带扩展名(.js,.json,.node) --> 去找对应的文件
- 如果是相对路径，不带扩展名 --> .js > .json > .node
- 如果是require('a')这种形式的 --> 内置模块，比如fs、path、http之类的


## 接下来要学习的是ES6相关的语法(作为一个中级前端，一定要习惯喜欢上es6的语法)
- 学习技巧：
    + [在线playground](http://babeljs.io/repl/)
    + [es5转es6](http://lebab.io/try-it)
- 编辑器配置
    + webstorm --> 如何设置防止报错(http://www.jianshu.com/p/b4390919a5b5)

## 09-Node.js基础-ES6-let和const使用规则-13:30
### let相关知识点
- **let不存在变量预解析**

```javascript
console.log(flag);//存在预解析，代码不会报错
var flag = 123;
```

```javascript
console.log(flag);//不存在预解析，代码会报错
let flag = 456;
```

- **let声明的变量不允许重复声明(可以重复赋值)**

```javascript
let flag = 123;
let flag = 456;
console.log(flag);//会报错
```

```javascript
if(true){
    var flag = 123;
}
console.log(flag);//123
```

```javascript
if(false){
    var flag = 123;
}
console.log(flag);//undefined,因为存在变量预解析
```

```javascript
if(true){
    let flag = 123;
}
console.log(flag);//会报错,因为let会导致花括号形成局部作用域
```

```javascript
{
    var a = 100;
    let flag = 2;
}
console.log(a);//100
console.log(flag);//报错
```

```javascript
for(var i=0;i<3;i++){
    console.log(i);
}
console.log(i);//3
```

```javascript
//for循环括号中声明的变量只能在循环体中使用
for(let i=0;i<3;i++){
    console.log(i);
}
console.log(i);//报错
```

```javascript
//在块级作用域中，变量只能先声明再使用
if(true){
    console.log(flag);
    let flag = 123;
}
```

### const知识点
- **const不能重复声明、也不能重复赋值，其他的和let一样**

```javascript
const n = 1;
n = 2;
```

#### const应用
- 引入其他模块的时候，一般用const
- 常量用const,比如Math.PI
- 由于const最严格，所以默认全用const，只有当值会变化或者复合数据类型的地址会变化的时候，才考虑用let

## 10-Node.js基础-变量的解构赋值-12:52
### 前置问题

- 如何把数组中的各项的值赋值给其他变量

```javascript
let arr = [2,3,4];
let a = arr[0];
let b = arr[1];
let c = arr[2];
```

- 如何把对象中各项的值赋值给其他变量

```javascript
let obj = {name:'itcast',subject:'frontend'};
let name = obj['name'];
let subject = obj['frontend'];
```


### 什么是解构赋值
解构赋值允许你使用类似数组或对象字面量的语法将数组和对象的属性赋给各种变量。这种赋值语法极度简洁，同时还比传统的属性访问方法更为清晰。

```javascript
//数组解构赋值
let [a,b,c] = [1,2,3];
console.log(a,b,c);
```

```javascript
//数组解构赋值
let [a=123,b,c] = [,2,];
console.log(a,b,c);
```

```javascript
//对象解构赋值(按需加载)
let {bar,foo} = {bar:"itcast",foo:"hi"};
console.log(foo,bar);
```

```javascript
//对象解构赋值
let {foo,bar} = {bar:"itcast",foo:"hi"};
console.log(foo,bar);
```

```javascript
//对象解构赋值
//abc是别名，如果有了别名，那么原来的名字就无效了
let {foo:abc,bar} = {bar:"itcast",foo:"hi"};
console.log(foo,bar);
```

```javascript
//对象解构赋值
let {cos,sin,random} = Math;
console.log(typeof cos);
console.log(typeof sin);
console.log(typeof random);
```

```javascript
//字符串解构赋值(了解即可)
let [a,b,c,d,e] = "hello";
console.log(a,b,c,d,e);
```

```javascript
let {length} = "hi";
console.log(length);
```

## 11-Node.js基础-ES6字符串相关扩展-14:13
### 对象解构赋值补充

```javascript
//对象解构赋值 - 默认值
let {bar='hello',foo} = {bar:"itcast",foo:"hi"};
console.log(foo,bar);
```

```javascript
//对象解构赋值 - 默认值
let {bar='hello',foo} = {foo:"hi"};
console.log(foo,bar);
```

### 字符串相关扩展
- includes

```javascript
console.log('hello world'.includes('world',6));
```

- startsWith

```javascript
let url = 'admin/index.php';
console.log(url.startsWith('admin'));
```

- endsWith

```javascript
let url = 'admin/index.php';
console.log(url.endsWith('php'));
```

- 模板字符串

```javascript
let obj = {
    username:'lisi',
    age:'12',
    gender:'male'
};

let fn = function(info){
    return info + '666';
}

let tpl = 
`
    <div>
        <p><span>${obj.username}</span></p>
        <p><span>${obj.age}</span></p>
        <p><span>${obj.gender}</span></p>
        <p><span>${fn('nihao')}</span></p>
    </div>
`

console.log(tpl);
```

## 12-Node.js基础-ES6-函数相关扩展 13:38
- 参数默认值

```javascript
//之前的写法
function foo(param){
    let p = param || 'hello';
    console.log(p);
}

foo();
foo('hi');
```

```javascript
//ES6的写法
function foo(param = 'nihao'){
    console.log(param);
}

foo();
foo('hi');
```

- 参数解构赋值

```javascript
//这块比较难理解：前面的{}意思是要传入的是一个对象，如果不传会报错，中间的张三、13是默认值，后面的意思是如果不传，则默认值是{}
function foo({uname='张三',age=13}={}){
    console.log(uname,age);
}

foo({uname:'zhangsan'});
```


- rest参数(剩余参数)

```javascript
function foo(a,...param){
    console.log(a,param);
}

foo(1,2,3,5,6);
```

```javascript
function foo(a,b,...param){
    console.log(a,b,param);
}

foo(1,2,3,5,6);
```


- ...扩展运算符

```javascript
function foo(a,b,c,d,e){
    console.log(a+b+c+d);
}

foo(1,2,3,4,5,6)
```

```javascript
function foo(a,b,c,d,e){
    console.log(a+b+c+d);
}
let arr = [1,2,3,4,5];
foo.apply(null,arr);
```

```javascript
function foo(a,b,c,d,e){
    console.log(a+b+c+d);
}
let arr = [1,2,3,4,5];
foo(...arr);
```


# day02
## 注意
- 今天前半天的课程是为了后面的课程铺垫的，特点是知识点比较零碎，可能在学的时候不知道是为了干嘛的，这块大家了解一下不用觉得茫然 ---> 解释一下为什么需要学习(我们需要从后端返回一个页面内容，那肯定要把内容进行读取，所以涉及到了文件的读写操作)

## 01-Node.js基础-ES6-箭头函数-17:39
### 上面的视频的补充
```javascript
let arr1 = [1,2,3];
let arr2 = [4,5,6];
let arr3 = [...arr1,...arr2];
console.log(arr3);
```

```javascript
const arr = [2,3,4];
const arr1 = [].concat(arr);
//现在可以这样写：
const arr3 = [...arr];
```


### 箭头函数

```javascript
// function foo(){
//     console.log('hello');
// }
// foo();

//相当于
let foo = ()=>console.log('hello');
foo();
```

```javascript
//function foo(v){
//    return v;
//}

//相当于
let foo = v=>v;
```

```javascript
let foo = (a,b)=>console.log(a+b);
foo(1,2);
```


```javascript
let foo = (a,b)=>{
    let c = 1;
    console.log(a+b+c);
}
foo(1,2);
```

```javascript
let arr = [123,456,789];
// arr.forEach(function(element,index){
//     console.log(element,index);
// });
arr.forEach((element,index)=>{
    console.log(element,index);
});
```

### 箭头函数
- 箭头函数中this取决于函数的定义，而不是调用

```javascript
function foo(){
    console.log(this);//global对象
}

foo();
```

```javascript
function foo(){
    //之前学过的知识点：函数中的函数中的this代表的是全局window对象
    setTimeout(function(){
        console.log(this.num);//打印结果：undefined
    },100)
}
foo.call({num:1});
```

```javascript
//这个代码应该比较难看懂，多花些时间
function foo(){
    //使用call调用foo时，这里的this其实就是call的第一个参数
    setTimeout(()=>{
        console.log(this.num);//打印结果：1
    },100)
}
foo.call({num:1});
```

- 箭头函数不可以new

```javascript
let foo = ()=>{this.num=123;}
new foo()//报错
```

- 箭头函数不可以使用arguments获取参数列表，可以使用rest代替

```javascript
let fn = (...rest)=>{
    console.log(rest instanceof Array);
}
fn();
```

```javascript
let foo = (...param)=>{
    console.log(param);
}
foo(123,456);
```


## 02-Node.js基础-类与继承-12:31
- 复习
    + 构造函数
    + 如何理解静态方法
    + 如何实现继承 -> https://github.com/zhengwei1949/learn_javascript_oop_the_easy_way

```javascript
function Animal(name){
    this.name = name;
}
Animal.prototype.showName = function(){
    console.log(this.name);
}
var a = new Animal('Tom');
a.showName();
var a1 = new Animal('Jerry');
a1.showName();
```
![](http://www.listverse.info/wp-content/uploads/2014/11/4-tom-and-jerry-logo-4-300x210.png)

```javascript
class Animal{
    constructor(name){
        this.name = name;
    }

    showName(){
        console.log(this.name);
    }
}

let a = new Animal('spike');
a.showName();
```

![](http://img1.imgtn.bdimg.com/it/u=3885866757,4217768438&fm=26&gp=0.jpg)

```javascript
//静态方法
class Animal{
    //静态方法只能通过类名调用，不可以通过实例对象调用
    static showInfo(){
        console.log('hi');
    }
    constructor(name){
        this.name = name;
    }

    showName(){
        console.log(this.name);
    }
}

let a = new Animal('spike');
a.showName();
Animal.showInfo();
```

### 继承

```javascript
class Animal{
    //静态方法只能通过类名调用，不可以通过实例对象调用
    static showInfo(){
        console.log('hi');
    }
    constructor(name){
        this.name = name;
    }

    showName(){
        console.log(this.name);
    }
}

class Dog extends Animal{
    constructor(name,color){
        super(name);//super用来调用父类
        this.color = color;f
    }

    showColor(){
        console.log(this.color);
    }
}

let d = new Dog('doudou','yellow');
d.showName();
d.showColor();
Dog.showInfo();
```

## 练习
1. 箭头函数支持的两种写法是什么？箭头函数里的this指向谁？

2. 如何用es6的方法定义一个类(要包含继承)？
3. 以下str用es6的方法怎么写？

```javascript
var name='cat',age=1,
var str=name+'is'+age+'years old'

```

4. 以下数组怎么用解构赋值的方法怎么解析成一个个变量？

```javascript
    var ary=['cat','dog','fox']
    
```

5. es6函数怎么定义默认参数？怎么传任意参数的？（写个函数小例子）


6. 写一下let和const的区别

7. 将下面的代码翻译为es5，只要求实现功能即可，不要求翻译质量

```javascript
class Animal{
    constructor(...args){
        [this.name, this.gender, this.age] = args;
    }

    getInfo(){
        console.log(`A ${this.age} years old ${this.gender} ${this.name}`);
    }
}

new Animal('cat', 'male', 'two').getInfo(); // A two years old male cat
```

8. 说出下面代码的意思(难度级别：五星 主要考察的是解构赋值，如果不会，可以把代码粘贴到http://babeljs.io/repl/看看转换成es5的样子)

```javascript
const foo = ({hello:{world:bar}})=>({bar})
```

## 编码

### Buffer-操作二进制

电脑只存存二进制数据

![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-28/96573603.jpg)

正如hash表示的是锚点值(location.hash),在Node.js当中，二进制叫Buffer

![](https://imgsa.baidu.com/exp/w=480/sign=850d8379384e251fe2f7e5f09787c9c2/d1160924ab18972b103e2189eecd7b899e510a68.jpg)

### node.js中与编码相关的api --> Buffer
- 在node.js当中，使用Buffer这个构造器来把字符类型的数据转换成二进制的数据

```javascript
var buf = new Buffer('abc','utf8');//默认就是utf8格式的，后面的可以不用写的
console.log(buf);
console.log(buf.toString());//可以把二进制的转换成utf8格式的数据
```

或者

```javascript
var buf = Buffer.from('abc');
console.log(buf);
console.log(buf.toString());
```

## 03-Node.js基础-异步编程概念分析-11:25

### 感性的认识异步
火车站买票的例子(同步) vs 银行叫号排队的例子(异步)

### 通过一个例子来理解js执行代码的流程(不考虑预解析)

```javascript
var a = 1;
console.log(a);
var xhr = new XMLHttpRequest();
xhr.open('GET','./a.json');
xhr.onreadystatechange = function(){
    if(xhr.status === 200 && xhr.readyState === 4){
        console.log(xhr.responseText);
    }
}
xhr.send(null);
setTimeout(function(){
    console.log('定时器执行');
},200);
var b = 2;
console.log(b);
```

#### 预置知识点
要想理解这个过程，必须要明白下面几个东西：
1、js是单线程的，也就是一次只能执行一件事情
    + 单线程：一个车间，一次只能做一件事情
    + 多进程：有一堆的车间，可以给每个任务分配一个车间执行相应的任务
2、浏览器是多线程(进程)的，有的进程用来渲染css,有的进程用来渲染html,有的进程用来请求ajax,有的进程用来请求页面的图片、js、css等静态文件资源
3、event loop用来管理我们的异步的代码的，它会把它们放在一个线程池当中

#### 理解整个流程
1. 浏览器加载当前的js文件，主js线程可以从上往下运行
2. 执行`var a = 1`
3. 执行`console.log(a)`
4. 创建一个xhr对象，把这个对象的相关操作和onreadystatechange后面的回调函数放到事件循环event loop当中
5. 把定时器和对应的回调函数放到我们的event loop当中
6. event loop会管理我们的异步的任务，当异步任务执行完了（如果是定时器则是定时器到期了）之后，把对应的回调函数放到一个叫回调函数队列当中
7. 当主js线程中的代码全部执行完了之后，处于空闲状态，去回调函数队列当中去找有没有任务可以执行，如果有的话就取出来靠最前面的拿出来执行

#### 如何理解I/O
- input --> 把内容写入文件、请求报文
- output --> 读取文件中的内容、响应报文

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1505670692729&di=3e98401665992190ef8804d664e7f741&imgtype=0&src=http%3A%2F%2Fpimg.haitao.com%2Fimg%2F0%2F10%2F10351%2F10351_0.jpg)

![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-14/38065358.jpg)

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1505670716687&di=5b0307ce47a30c7cda3766e94edd866f&imgtype=0&src=http%3A%2F%2Fimgsrc.baidu.com%2Fimgad%2Fpic%2Fitem%2Fb7003af33a87e950c7e6a44b1a385343fbf2b420.jpg)

## 04-Node.js基础-查看文件状态-14:05

这个api不用记，后面用不上，主要是为了体会Node.js的代码的写法

```javascript
//通过此代码理解回调函数的第一个参数错误对象
const fs = require('fs');
fs.stat('./data.txt',(err,stats)=>{
    //一般回调函数的第一个参数是错误对象，如果没有出错正确执行了，则err表示null,否则就是一个错误对象了
    console.log(err);
});
```

```javascript
//判断是文件还是目录
const fs = require('fs');
fs.stat('./data.txt',(err,stats)=>{
    //一般回调函数的第一个参数是错误对象，如果没有出错正确执行了，则err表示null,否则就是一个错误对象了
    if(err)return;
    if(stats.isFile()){
        console.log('是文件');
    }else if(stats.isDirectory()){
        console.log('是目录');
    }
});
```

### 补充:同步的方式

```javascript
const fs = require('fs');
//同步操作
let ret = fs.statSync('./data.txt');
console.log(ret);
```

![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-14/58989951.jpg)


## 05-Node.js基础-读文件操作-9:28(掌握)

```javascript
//异步操作方式
const fs = require('fs');
const path = require('path');

let strpath = path.join(__dirname,'data.txt');
fs.readFile(strpath,(err,data)=>{
    if(err) return;
    console.log(data.toString());
})
```

```javascript
//异步操作方式
const fs = require('fs');
const path = require('path');

let strpath = path.join(__dirname,'data.txt');
fs.readFile(strpath,'utf8',(err,data)=>{
    if(err) return;
    console.log(data);
})
```

```javascript
//同步操作方式
const fs = require('fs');
const path = require('path');

let strpath = path.join(__dirname,'data.txt');
let ret = fs.readFileSync(strpath,'utf8');
console.log(ret);
```

## 06-Node.js基础-写文件操作-8:27

### 注意事项
- 如果该文件存在，则是覆盖内容
- 如果不存在，则node会帮我们创建这个文件

```javascript
//写文件的异步操作方式
const fs = require('fs');
const path = require('path');

let strpath = path.join(__dirname,'data.txt');
// fs.writeFile(strpath,'hello nihao','utf8',(err)=>{
//     if(!err){
//         console.log('文件写入成功');
//     }
// });

let buf = Buffer.from('hi');
fs.writeFile(strpath,buf,'utf8',(err)=>{
    if(!err){
        console.log('文件写入成功');
    }
});
```

```javascript
//写文件的同步操作方式
const fs = require('fs');
const path = require('path');

let strpath = path.join(__dirname,'data.txt');
fs.writeFileSync(strpath,'tom and jerry');
```

## 07-Node.js基础-文件的流式操作-13:00

### 使用fs.readFile不能读取超大文件
演示一下用fs.readFile读取超大文件 --> 失败 --> 原因：读文件需要把整个文件读入内存，我们的操作系统给node.js分配的最大限度的内存没这么多，出错 ---> 流式操作

### 流式操作
- fs.createReadStream  --> 创建可读流
- fs.createWriteStream --> 创建可写流

### 如何理解
- 传统读写文件 --> 直接把一大坨东西移到另一个地方，如果不是大力士根本搞不定
- 流式操作文件 --> 把大文件想像成是一个大的冰块，我们融化它，然后慢慢的一点点用瓢舀过去

![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/76013854.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/47168490.jpg)


```javascript
const path = require('path');
const fs = require('fs');

let spath = path.join(__dirname,'../03-source','file.zip');//源路径
let dpath = path.join('C:\\Users\\www\\Desktop','file.zip') //目标路径

let readStream = fs.createReadStream(spath);//创建可读流
let writeStream = fs.createWriteStream(dpath);//创建可写流

//基于事件的处理方式
// $('input[type=button]').on('click',function(){
//     console.log('hello');
// })

let num = 1;
//chunk就是舀出来的每一小块数据
//这块data,end事件的代码是重点，要能自己写出来
readStream.on('data',(chunk)=>{
    num++;
    writeStream.write(chunk);
});

readStream.on('end',()=>{
    console.log('文件处理完成');
})
```

### 管道的方式
- 复习gulp的玩法

```javascript
const path = require('path');
const fs = require('fs');

let spath = path.join(__dirname,'../03-source','file.zip');//源路径
let dpath = path.join('C:\\Users\\www\\Desktop','file.zip') //目标路径

let readStream = fs.createReadStream(spath);//创建可读流
let writeStream = fs.createWriteStream(dpath);//创建可写流

readStream.pipe(writeStream);
```

## 08-Node.js基础-初识包概念-5:36
### 复习前面讲过的模块
- 内置模块：fs,path
- 自定义模块(也就是一个js算一个模块，意味着自己写的js文件)

### 复习gulp的用法
- 思考：我们通过npm进行下载gulp,gulp-uglify,然后通过require进行引入，但是引入的既不是内置模块，也不算是自定义模块，那算什么东西呢?

### 如何理解包
- 模块可以理解成文件，包可以理解成文件夹（里面有很多文件）
- 不过，在很多书或文章里面，包和模块这二个是同一个意思，了解即可

## 09-Node.js基础-npm基本使用-11:22(主要讲全局方式)
### 常用npm命令
- `npm install -g 包名称@版本号`
- `npm update -g 包名` --> 更新到最新版
- `npm install -g 包名@latest` 更新到最新版(推荐使用)
### 视频中涉及到的两个工具
- https://github.com/ruanyf/es-checker
- https://github.com/i5ting/tocmd.npm

## 10-Node.js基础-npm基本使用-11:24(主要讲本地模式)
- scripts属性的作用(体会一下作用，方便我们操作)
### 在node.js中使用art-template(这个网站打不开的话，必须要翻墙，这块代码因为之前玩过，如果感觉熟悉可以不练习)
### 包的查找机制(当我们看到require(标识符)的时候，我们去哪找?)
- 如果是相对绝对路径，则去找自定义模块(js>json>node)
- 如果是不带任何相对绝对路径字样，则先判断是不是内置模块，如果不是则去找第三方的包，去当前找一个叫node_modules里面去找文件夹名字叫这个的，如果找到了，先看看有没有一个叫package.json的文件，如果有，则去里面找main里面的配置的文件，如果没有package.json,则去找index.js文件 

## 11-Node.js基础-npm基本使用-7:04(讲--save和--save-dev的区别)
- jquery,zepto,angular --> --save
- webpack,gulp --> --save-dev

## 12-Node.js基础-修改npm镜像地址-11:41
- 设置registry镜像源(最方便，适合网不快的情况下) 上课的时候设置一下这个即可

```shell
npm config get registry --> 查看镜像
npm config set registry https://registry.npm.taobao.org --> 设置镜像为taobao
```

- cnpm(最稳定),推荐使用这个，因为如果只是通过set registry修改镜像源经测试不能解决node-sass安装的问题

```shell
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

- nrm(我用了一段时间，感觉这种方式比较坑，有时间下载包的话经常会报错，建议不要用

## 13-Node.js基础-yarn基本使用-7:12

对npm的要求是掌握会用，对yarn的要求是了解即可，因为以后百分之九十的情况下用的是npm,yarn很少用

- npm init --> yarn init
- npm install 包名 --save --> yarn add 包名
- npm uninstall 包名 --> yarn remove 包名
- npm update 包名 --> yarn upgrade 包名
- npm install 包名 --save-dev --> yarn add 包名 -dev
- npm install -g 包名 --> yarn global add 包名
- npm config set registry https://registry.npm.taobao.org --> yarn config set registry https://registry.npm.taobao.org
- npm install --> yarn install
- npm run --> yarn run

### 补充一个命令rimraf(超好用)
    + 作用：删除node_modules文件夹

## 14-Node.js基础-自定义包案例
这里面要理解的是包没什么神秘的，只要符合我们刚才说的规范，我们也可以自己搞出来一个包

### 包的规范
- package.json必须在包的顶层目录下
- 二进制文件应该放在bin目录下
- js代码要放在lib目录下
- 文档放在doc目录下
- 单元测试文件放在test目录下(和我们没有关系，和测试人员有关)

### package.json字段分析
- name:包的名称，必须是唯一的，由小写字母、数字和下划线组成，不能包含空格
- description:包的简要说明
- version:符合语义化版本识别规范的版本字符串
- keywords:关键字数组，通常用于搜索(无用)
- maintainers:维护者数组(无用)
- contributors:贡献者数组(无用)
- bugs:(无用)
- licences(无用)
- repositories(无用)
- dependencies:生产环境包的依赖，一个关联数组，由包的名称和版本号组成
- devDependencies:开发环境包的依赖，一个关联数组，由包的名称和版本号组成

### 综合案例

#### 思考
- markdown-it可以让一个markdown的字符串转换成html
- 我们如何拥有一个markdown字符串? ---> 把markdown文件读取进来 --> 使用fs.readFile模块 
- 转换完之后，我们如何写入文件当中 --> fs.writeFile

https://github.com/markdown-it/markdown-it#readme

```javascript
const path = require('path');
const fs = require('fs');

let tplpath = path.join(__dirname,'tpl.html');
let mdpath = path.join(__dirname,'demo.md');
let targetpath = path.join(__dirname,'demo.html');

var md = require('markdown-it')();
// var result = md.render('## markdown-it rulezz!');
// console.log(result);

//获取markdown文件
fs.readFile(mdpath,'utf8',(err,data)=>{
    if(err)return;
    //对markdown内容进行转换操作
    let result = md.render(data);
    //读取模板内容
    let tpl = fs.readFile(tplpath,'utf8',(err,tplData)=>{
        if(err)return;
        tplData = tplData.replace('<%content%>',result);
        //生成的最终页面写入目标文件
        fs.writeFile(targetpath,tplData,(err)=>{
            console.log('转换完成');
        });
    });
});
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <%content%>
</body>
</html>
```

```markdown
# 一级标题
## 二级标题
### 三级标题
- 列表信息
    + 二级列表
        + 三级列表
```



# day03
## 注意
- 今天的比较难，是为了讲原理，这块代码大家写一次以后不太有机会写了，所以自己写不出来没关系，以能理解为主

## 01-Node.js-web开发-初识服务器模型-4:56
- 其他的后端语言像php的服务器直接安装apache即可，但是node.js这块的功能必须自己用代码完成 --> 如何理解?如果我们用的是php,我们的html,js,css直接放到apache就可以访问了，但是如果用的是apache,则必须用代码实现能让我们可以通过浏览器进行访问
- 这块写一个代码演示一下，只需要把js文件放在文件夹，运行一下就能把当前文件夹作为服务器

![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/86259757.jpg)

## 02-Node.js-web开发-初步实现服务器功能-8:57

### 普通写法
```javascript
const http = require('http');
//创建服务器实例
let server = http.createServer();
//绑定请求事件
server.on('request',(req,res)=>{
    res.end('hello');
})
//监听端口
server.listen(3000);
```

### 链式写法
```javascript
const http = require('http');
http.createServer((req,res)=>{
    res.end('ok');
}).listen(3000,'你的ip地址,这个最好不要写',()=>{
    console.log('running...');
});
```

### 如何通俗的理解
你想吃好吃的 --> 你打了一个电话给外卖(请求报文) --> 你必须要告诉外卖员你要吃的那家店地地址，不幸的是，所以首先你要知道门牌号(域名)，不幸的是，这个地址有一堆卖吃的，所以你还得告诉外卖员你要吃的那家的是哪个房间，比如8080房间(端口号) --> 外卖员在电话旁边等着，一有客人的电话就要进行服务(请求报应会触发回调函数)


### 问题
- 我们平时上网的时候，url不一样，得到的内容不一样
- 但是我们自己实现的却是不管什么url,得到的内容全是一样的

> 下面这几个视频主要讲的是如何实现一个类似apache一样的，把文件扔进www就可以访问的功能
## 03-Node.js-web开发-请求路径分发处理-7:47

> 这块大家经常会搞混，总是觉得文件夹里面有一个文件夹叫abc,就一定可以访问，一定要注意我们的url不管怎么写，其实不代表我们的文件夹里面真的有一个这个文件或文件夹，只是一个标识符而已，所有的url不管怎么样都要进来我们的回调函数里面[重点]

- req对象：请求报文
    + req.url
- res对象：响应报文

```javascript
const http = require('http');
http.createServer((req,res)=>{
    console.log(req.url);
    res.end('ok');
}).listen(3000);
```

```javascript
const http = require('http');
http.createServer((req,res)=>{
    //req.url可以获取URL中的路径（端口后的部分）
    //req.end(req.url)
    if(req.url.startsWith('/index')){
        //write向客户端响应内容，可以写多次
        res.write('hello');
        res.write('hi');
        res.write('nihao');
        // end方法用来完成响应,只能执行一次
        res.end('ok');
    }else if(req.url.startsWith('/about')){
        res.end('about');
    }else{
        res.end('no content');
    }
}).listen(3000);
```

## 04-Node.js开发-初步实现静态资源功能-13:18
- res.writeHead(200,{'Content-Type':'text/plain;charset=utf8'})

### 这样实现的问题
- 如果有一堆的静态资源文件怎么办
- 静态资源文件的类型是不确定的，比如图片、mp3等

## 05-Node.js开发-优化静态资源功能-14:01(使用mime)
 
## 06-Node.js开发-静态资源服务器功能模块封装-14:01

> 接下来这块咱们是要实现php的$_GET,$_POST的功能
## 07-Node.js开发-get参数处理-12:16

### 先思考一下我们如果是浏览器端怎么处理?
- location.href
- location.hash
- location.search --> 如何转换成对象?

```javascript
const url = require('url');
let str = 'http://www.baidu.com/abc/qqq?flag=123&keyword=java';
let ret = url.parse(str);
console.log(ret);
```

```javascript
const http = require('http');
const path = require('path');
const url = require('url');

http.createServer((req,res)=>{
    let obj = url.parse(req.url,true);
    res.end(obj.query.username + '======' + obj.query.password);
}).listen(3000,()=>{
    console.log('running...');
});
```

## 08-Node.js开发-post参数处理-13：27
- querystring.parse

```javascript
const querystring = require('querystring');

let param = 'username=lisi&password=123';
//parse的作用就是把字符串转换成对象
let obj = querystring.parse(param);
console.log(obj);
```

- querystring.stringify

```javascript
const querystring = require('querystring');

let param = 'username=lisi&password=123';
//stringify的作用就是把对象转换成字符串
let obj1 = {
    flag:'123',
    abc:['hello','hi']
}
let str1 = querystring.stringify(obj1);
console.log(str1);
```

![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/45755237.jpg)

```javascript
const querystring = require('querystring');
const http = require('http');

http.createServer((req,res)=>{
    if(req.url.startsWith('/login')){
        let pdata = '';
        req.on('data',(chunk)=>{
            pdata+=chunk;
        });

        req.on('end',()=>{
            console.log(pdata);
            let obj = querystring.parse(pdata);
            res.end(obj.username+'---'+obj.password);
        })
    }
}).listen(3000,()=>{
    console.log('running...');
})

```

### 补充 post数据提交的形式的区别
- http://blog.csdn.net/ye1992/article/details/49998511

## 09-Node.js-web开发-登陆验证案例-13:22

## 10-Node.js-web开发-初步实现动态网站

### 动态网站的本质
根据不同的请求路径和参数的传递来得到不同的内容，并且我们的浏览器端的内容是动态生成的，并不是像静态资源一样是提前写好的

## 11-Node.js-web开发-后台模板引擎基本使用-12:59

## 12-Node.js-web开发-使用模板引擎查询成绩案例

## 13-Node.js-web开发-Express-初识web框架-12:42

## 14-Node.js-web开发-Express-托管静态资源-12:34

## 15-Node.js-web开发-Express-路由处理-11:20

### 补充 - 把路由提取到一个公共的文件里面去
```javascript
var express = require('express');
var router = express.Router();

// 该路由使用的中间件
router.use(function timeLog(req, res, next) {
  console.log('Time: ', Date.now());
  next();
});
// 定义网站主页的路由
router.get('/', function(req, res) {
  res.send('Birds home page');
});
// 定义 about 页面的路由
router.get('/about', function(req, res) {
  res.send('About birds');
});

module.exports = router;
```

```javascript
var birds = require('./birds');
...
app.use('/birds', birds);
```

# 图书管理系统数据库sql导入语句
大家只需要把book数据库创建好即可

```sql
-- phpMyAdmin SQL Dump
-- version 4.7.2
-- https://www.phpmyadmin.net/
--
-- Host: localhost:3306
-- Generation Time: Sep 19, 2017 at 10:05 AM
-- Server version: 5.6.35
-- PHP Version: 7.1.6

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET time_zone = "+00:00";

--
-- Database: `book`
--

-- --------------------------------------------------------

--
-- Table structure for table `book`
--

CREATE TABLE `book` (
  `id` int(11) NOT NULL,
  `name` varchar(100) COLLATE utf8_bin NOT NULL,
  `author` varchar(100) COLLATE utf8_bin NOT NULL,
  `category` varchar(100) COLLATE utf8_bin NOT NULL,
  `description` varchar(1000) COLLATE utf8_bin NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- Dumping data for table `book`
--

INSERT INTO `book` (`id`, `name`, `author`, `category`, `description`) VALUES
(1, '三国演义', '罗贯中', '文学', '一个杀伐纷争的年代'),
(2, '水浒传', '施耐庵', '文学', '108条好汉的故事'),
(3, '西游记', '吴承恩', '文学', '佛教与道教的斗争'),
(4, '红楼梦', '曹雪芹', '文>学', '一个封建王朝的缩影'),
(5, '天龙八部', '金庸', '文学', '武侠小说'),
(6, '明朝那些事', '当年明月', '文学', '明朝的历史'),
(7, '明朝那些事', '当年明月', '文学', '明朝的历史'),
(8, '明朝那些事', '当年明月', '文学', '明朝的历史'),
(9, '明朝那些事', '当年明月', '文学', '明朝的历史'),
(10, '明朝那些事', '当年明月', '文学', '明朝的历史'),
(11, '明朝那些事', '当年明月', '文学', '明朝的历史'),
(12, '明朝那些事', '当年明月', '文学', '明朝的历史'),
(13, '明朝那些事', '当年明月', '文学', '明朝的历史');

-- --------------------------------------------------------

--
-- Table structure for table `user`
--

CREATE TABLE `user` (
  `id` int(11) NOT NULL,
  `username` varchar(100) COLLATE utf8_bin NOT NULL,
  `password` varchar(100) COLLATE utf8_bin NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- Dumping data for table `user`
--

INSERT INTO `user` (`id`, `username`, `password`) VALUES
(1, 'admin', '123456');

--
-- Indexes for dumped tables
--

--
-- Indexes for table `book`
--
ALTER TABLE `book`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `user`
--
ALTER TABLE `user`
  ADD PRIMARY KEY (`id`);

--
-- AUTO_INCREMENT for dumped tables
--

--
-- AUTO_INCREMENT for table `book`
--
ALTER TABLE `book`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=14;
--
-- AUTO_INCREMENT for table `user`
--
ALTER TABLE `user`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;
```



## 示例代码
# 用http.request api 做反向代理
# 补充 - request第三方模块的使用
[文档](https://github.com/request/request)

```javascipt
var request = require('request');
//观察第一个参数，理解解决了什么问题 --> 简化http.request的配置项
request('http://shoes-bags.vip.com/?ff=index_new', function (error, response, body) {
  console.log('error:', error); // Print the error if one occurred
  console.log('statusCode:', response && response.statusCode); // Print the response status code if a response was received
  console.log('body:', body); // Print the HTML for the Google homepage.
});
```

## cors的使用
# promise - 异步编程解决方案

### 问题

```javascript
console.log('定时器开始');
setTimeout(()=>{
    console.log('定时器进行中');
},1000);
console.log('定时器结束');
//我们在编写异步程序时，最头痛的就是不知道结果什么时候返回给我们，然后执行后面的操作，很多时候只能把后面的操作放到返回成功的函数里
```

```javascript
//如果我们想要实现，只能如下这样来做
console.log('定时器开始');
function myTime(callback){
    setTimeout(()=>{
        console.log('定时器进行中');
        endTimer();
    },1000);    
}
function endTimer(){
    console.log('定时器结束');
}
myTime(endTimer);
```

```javascript
//如果再复杂一些
console.log('定时器1开始');
//传说中的回调地狱.....
function myTime(callback){
    setTimeout(()=>{
        console.log('定时器1进行中');
        endTimer1(()=>{
            console.log('定时器2开始');
            setTimeout(()=>{
                console.log('定时器2进行中...');
                endTimer2(()=>{
                    console.log('定时器3开始');
                    setTimeout(()=>{
                        console.log('定时器3进行中');
                        endTimer3();
                    })
                })
            })
        });
    },1000);    
}
function endTimer1(callback){
    console.log('定时器1结束');
    callback();
}
function endTimer2(callback){
    console.log('定时器结束...');
    callback();
}
function endTimer3(){
    console.log('定时器3结束')
}
myTime(endTimer1);
```

> 于是，promise就被发明出来了


想象你是一个孩子。你老妈承诺下礼拜 给你买个新手机。你 [不知道] 你是否会得到手机直到下礼拜。你老妈可以真的买你一个全新的手机，也可以让你滚蛋并告诉你不买了（如果她不高兴了）。

```javascript
var isMomHappy = confirm('要不要买手机')
 
var willGetNewPhone = new Promise(function(resolve,reject){
console.log(isMomHappy);
if(isMomHappy){
  var phone = {
      brand:'三星',
      color:'黑色'
  };
  resolve(phone);//成功
}else{
  var reason = new Error('mom is not happy');
  reject(reason);//失败
}  
});

 

willGetNewPhone.then(function(res){console.log(res)},function(res){console.log(res)});
```


```javascript
console.log('定时器开始');
var timerPromise = new Promise((resolve,reject)=>{
    setTimeout(()=>{
        console.log('定时器进行中');
        resolve();
    },1000);
})

timerPromise.then(()=>{
    console.log('定时器结束');
})
```


```javascript
const fs = require('fs');
const path = require('path');

var readFile = function (fileName) {
  return new Promise(function (resolve, reject) {
    fs.readFile(fileName, function(error, data) {
      if (error) return reject(error);
      resolve(data);
    });
  });
};

readFile(path.join(__dirname,'aaa.js'))
.then(res=>{
    console.log(res.toString());
    console.log('====')
    return readFile(path.join(__dirname,'index.html'));
})
.then(res=>{
    console.log(res.toString())
})
.catch(err=>{
    //err
})
```

```javascript
function getURL(URL) {
    return new Promise(function (resolve, reject) {
        var req = new XMLHttpRequest();
        req.open('GET', URL, true);
        req.onload = function () {
            if (req.status === 200) {
                resolve(req.responseText);
            } else {
                reject(new Error(req.statusText));
            }
        };
        req.onerror = function () {
            reject(new Error(req.statusText));
        };
        req.send();
    });
}
// 运行示例
var URL = "http://httpbin.org/get";
getURL(URL).then(function onFulfilled(value){
    console.log(value);
}).catch(function onRejected(error){
    console.error(error);
});
```
# async/await(了解)

```javascript
function myFetch(url){
    return new Promise((resolve,reject)=>{
        fetch(url)
            .then(res=>{
                return res.json();
            })
            .then(res=>{
                resolve(res);
            })
    })
}

//async表示函数里有异步操作
const fn = async function(){
//await表示紧跟在后面的表达式需要等待结果
    let data1 = await myFetch('https://api.github.com/users/zhengwei1949');
    console.log(data1);
    console.log(123);
    let data2 = await myFetch('https://api.github.com/users/github');
    console.log(data2);
    console.log(456);
}

fn();
```

# fetch

```javascript
        let url = 'https://api.github.com/users/zhengwei1949';
        
        fetch(url)
        .then(res=>{
            return res.json()
        }).then(res=>{
            console.log(res)
        })
```

# pm2工具的使用

```
➜  promise_demo pm2 start s.js
[PM2] Applying action restartProcessId on app [s](ids: 0)
[PM2] [s](0) ✓
[PM2] Process successfully started
┌──────────┬────┬──────┬───────┬─────────┬─────────┬────────┬─────┬──────────┬──────┬──────────┐
│ App name │ id │ mode │ pid   │ status  │ restart │ uptime │ cpu │ mem      │ user │ watching │
├──────────┼────┼──────┼───────┼─────────┼─────────┼────────┼─────┼──────────┼──────┼──────────┤
│ s        │ 0  │ fork │ 31180 │ online  │ 0       │ 0s     │ 0%  │ 2.2 MB   │ zw   │ disabled │
│ s1       │ 1  │ fork │ 0     │ stopped │ 0       │ 0      │ 0%  │ 0 B      │ zw   │ disabled │
└──────────┴────┴──────┴───────┴─────────┴─────────┴────────┴─────┴──────────┴──────┴──────────┘
 Use `pm2 show <id|name>` to get more details about an app

➜  promise_demo pm2 list
┌──────────┬────┬──────┬───────┬────────┬─────────┬────────┬─────┬───────────┬──────┬──────────┐
│ App name │ id │ mode │ pid   │ status │ restart │ uptime │ cpu │ mem       │ user │ watching │
├──────────┼────┼──────┼───────┼────────┼─────────┼────────┼─────┼───────────┼──────┼──────────┤
│ s        │ 0  │ fork │ 31068 │ online │ 0       │ 2m     │ 0%  │ 31.3 MB   │ zw   │ disabled │
│ s1       │ 1  │ fork │ 31121 │ online │ 0       │ 76s    │ 0%  │ 28.5 MB   │ zw   │ disabled │
└──────────┴────┴──────┴───────┴────────┴─────────┴────────┴─────┴───────────┴──────┴──────────┘
 Use `pm2 show <id|name>` to get more details about an app
➜  promise_demo pm2 stop all
[PM2] Applying action stopProcessId on app [all](ids: 0,1)
[PM2] [s](0) ✓
[PM2] [s1](1) ✓
┌──────────┬────┬──────┬─────┬─────────┬─────────┬────────┬─────┬────────┬──────┬──────────┐
│ App name │ id │ mode │ pid │ status  │ restart │ uptime │ cpu │ mem    │ user │ watching │
├──────────┼────┼──────┼─────┼─────────┼─────────┼────────┼─────┼────────┼──────┼──────────┤
│ s        │ 0  │ fork │ 0   │ stopped │ 0       │ 0      │ 0%  │ 0 B    │ zw   │ disabled │
│ s1       │ 1  │ fork │ 0   │ stopped │ 0       │ 0      │ 0%  │ 0 B    │ zw   │ disabled │
└──────────┴────┴──────┴─────┴─────────┴─────────┴────────┴─────┴────────┴──────┴──────────┘
 Use `pm2 show <id|name>` to get more details about an app
```

# 类中的this的问题
类的方法内部如果含有this，它默认指向类的实例。但是，必须非常小心，一旦单独使用该方法，很可能报错。

```javascript
class Logger {
  printName(name = 'there') {
    this.print(`Hello ${name}`);
  }

  print(text) {
    console.log(text);
  }
}

const logger = new Logger();
const { printName } = logger;
printName(); // TypeError: Cannot read property 'print' of undefined
```

上面代码中，printName方法中的this，默认指向Logger类的实例。但是，如果将这个方法提取出来单独使用，this会指向该方法运行时所在的环境，因为找不到print方法而导致报错。

一个比较简单的解决方法是，在构造方法中绑定this，这样就不会找不到print方法了。

```javascript
class Logger {
  constructor() {
    this.printName = this.printName.bind(this);
  }

  // ...
}
```

另一种解决方法是使用箭头函数。

```javascript
class Logger {
  constructor() {
    this.printName = (name = 'there') => {
      this.print(`Hello ${name}`);
    };
  }

  // ...
}
```


# 参考资料
- 《mysql必知必会》
- 《图解http协议》
- http://island205.github.io/HelloSea.js/index.html

![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/81575811.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/60672638.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/94288711.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/20876511.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/5960758.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/3765828.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/73427594.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/64644425.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/748435.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/56447944.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/11657382.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/1545306.jpg)
![](http://7fvanf.com1.z0.glb.clouddn.com/17-8-16/33598977.jpg)


# 概念理解
- 目录 --> 和文件夹是同一个意思
- webapi --> 接口
- restful
- 前后端分离

# 常见问题
- node.js安装不成功，提示204,205错误
- ls,cat等命令用不了
- vsCode不能打开终端

# 代码辅助阅读器
- https://github.com/Jianru-Lin/lambda-view

# 不错的资源
- https://www.kancloud.cn/kancloud/javascript-standards-reference/46532


# express不错的插件
- http-proxy-middleware

