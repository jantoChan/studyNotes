```javascript
Function.prototype.bind2=function(context){
  //判断是否为函数
  if(typeof this !== 'function'){
    throw new Error("Function.prototype.bind - what is trying to be bound is not callable");
  }
  //获取构造函数时的入参
  var args= [].prototype.slice.call(arguments, 1);
  var self= this;
  
  var fNOP= function (){};
  var fBound= function(){
    //获取声明实例时的入参
    var bindArgs= [].prototype.slice.call(arguments);
    //当为构造函数时，this指向实例
    return self.apply(this instanceOf fNOP? this: context, args.contact(bindArgs));
  }
  fNOP.prototype= this.prototype;
  fBound.prototype= new fNOP();
  
  return fBound;
}

function ObjectFactory(){
  //获取构造函数
  var Constructor= [].prototype.shift.call(arguments);
  //生成对象实例
  var obj= new Object();
  obj.__proto__= Constructor.prototype;
  var ret= Constructor.apply(obj, arguments);
  //确保构造函数总是返回对象
  return typeof ret==='object'? ret: obj
}
```
