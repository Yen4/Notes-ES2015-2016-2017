# Notes-ES2015-2016-2017
## this
Never use `Arrow function` in method.

```Javascript
var instructor{
  firstname: "Elie",
  sayHi: () => "Hello ${this.firstname}";
}

instructor.sayHi();  //Hello undefined
```

But in this way. In a callback function, it's very useful.  
The key word `this` refers to the enclosing context(instructor object).  
More intuitive way than call, apply, bind.
```Javascript
var instructor{
  firstname: "Elie",
  sayHi: function(){
    setTimeout(() => {
      console.log("Hello " + this.firstname);
    }, 1000);
  }
}

instructor.sayHi();  //Hello Elie
```

`this` refer to the object when the method being involk. In this case, it's Window object in browser.
```Javascript
var instructor{
  firstname: "Elie",
  sayHi: function(){
    setTimeout(function(){
      console.log("Hello " + this.firstname);
    }, 1000);
  }
}

instructor.sayHi();  //Hello undefined
```

In js before ES2015, use `bind` to connect `this` keyword.  
Check `apply`, `call` too, these three are highly connected to `this`.
```Javascript
var instructor{
  firstname: "Elie",
  sayHi: function(){
    setTimeout(function(){
      console.log("Hello " + this.firstname);
    }.bind(this), 1000);
  }
}

instructor.sayHi();  //Hello Elie
```

## default parameter
```Javascript
function add(a=10, b=20){
  return a+b;
}

add();  //30
add(30);  //50
add(30, 40);   //70
```

## for...of iteration
for...of loop can't be used in object. Check the `__proto__`, no iteration method.
```Javascript
var arr = [1,2,3,4,5];

for(let val of arr){
  console.log(val)
}

//1
//2
//3
//4
//5
```





