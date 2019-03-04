```javascript
Function.call2=function(context){
  var context= context || window; //作用域若没有则为window
  context.fn= this;//将执行函数赋值到对象上
  
  var args= [];
  for(var i=0; i<arguments.length; i++){
    args.push('arguments['+i+']');//获取函数入参
  }
  
  var result= eval('context.fn('+args+')');//执行方法
  delete context.fn;//删除对象函数
  
  return result;//返回值
}

function bar(name, age) {
    console.log(this.value);
    return {
        value: this.value,
        name: name,
        age: age
    }
}
bar.call2(null, 'jane',12); // 2

Function.apply2= function(context, arr){
  var context= context || window;
  var return;
  context.fn= this;
  if(!arr){
    result= context.fn();
  }else{
    var args= [];
    for(var i=0; i<arr.length; i++){
      args.push('arr['+i+']') 
    }
    result= eval('context.fn('+arr+')');
  }
  delete context.fn;
  return result;
}
function bar(name, age) {
    console.log(this.value);
    return {
        value: this.value,
        name: name,
        age: age
    }
}
bar.apply2(null, ['jane', 12]);
```
