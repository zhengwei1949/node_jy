# 一看就懂的promise教程

```javascript
console.log('定时器开始');
setTimeout(()=>console.log('定时器进行中'));
console.log('定时器结束');
```

上面的代码的问题是，我们期待的是先打印'定时器开始'，再打印定时器进行中，最后打印定时器结束，但是事实上却是'定时器开始'->'定时器结束'->'定时器结束'

为了解决这个问题，我们可以怎么办呢?来，我们把代码改造一下：

```javascript
console.log('定时器开始');
setTimeout(()=>{
    console.log('定时器进行中');
    endTimer();
})
function endTimer(){
  console.log('定时器结束');
}
```

是的，我们必须要用**回调函数**

但是，这种方式会带来什么问题呢?

我们如果要在这整个全部执行完之后再来执行其他的代码怎么办？这时候，我们必须又搞一个回调函数：

```javascript
function myTime(callback){
  console.log('定时器开始');
  setTimeout(()=>{
      console.log('定时器进行中');
      endTimer();
  })
  function endTimer(){
      console.log('定时器结束');
      callback();
  }
}

myTime(function(){
    console.log('定时器全部结束会执行这里的代码');
})
```

这时候，我们极端一些，假如我们把层次搞深一些：

```javascript
function myTime(callback){
    console.log('定时器开始');
    setTimeout(()=>{
        console.log('定时器进行中');
        endTimer();
    })
    function endTimer(){
        console.log('定时器结束');
        callback();
    }
}

myTime(function(){
    myTime(function(){
        myTime(function(){
            myTime(function(){
                myTime(function(){
                    myTime(function(){
                        
                    })
                })
            })
        })
    })
})
```

这时候我们会发现代码会变得极其的丑陋。由于在js当中，异步代码随处可见(事件、Node.js中的文件读写等操作、http操作、定时器等)，所以，回调函数无处不在，如果回调的层次不够深，我们还可以接受，但是一旦回调的层次太深了，我们就会写出诸如如上的代码。

怎么办? --> 用promise,我们来看一下如果使用了promise之后代码长得像什么样子：

```javascript
let myTime = function(){
    return new Promise((resolve,reject)=>{
        console.log('定时器开始');
        setTimeout(()=>{
            console.log('定时器进行中');
            resolve('定时器结束');
        })
    })
}

myTime()
.then((res)=>{
    console.log(res);
    return myTime();
})
.then((res)=>{
    console.log(res);
    return myTime();
})
.then((res)=>{
    console.log(res);
    return myTime();
})
.then((res)=>{
    console.log(res);
    return myTime();
})
.then((res)=>{
    console.log(res);
    return myTime();
})
.then((res)=>{
    console.log(res);
    return myTime();
});
```

perfect,完美有木有??

这里，我们可以直接上结论：

> promise的好处：解决了异步代码嵌套层次过深的问题，能让我们的代码看起来更加的扁平化

## fetch api

```javascript
fetch('./a.json')
.then((res)=>{
    return res.json();
})
.then((data)=>{
    console.log(data)
})
.catch((e)=>{
    console.log('出错啦');
})
```

## 扩展 async/await

```javascript
let myTime = function(){
    return new Promise((resolve,reject)=>{
        console.log('定时器开始');
        setTimeout(()=>{
            console.log('定时器进行中');
            resolve('定时器结束');
        })
    })
}


let fn = async function(){
    let ret;
    ret = await myTime();
    console.log(ret);
    ret = await myTime();
    console.log(ret);
    ret = await myTime();
    console.log(ret);
    ret = await myTime();
    console.log(ret);
}

fn()
```








