
# The JS Notes

1.  [Arithmetic Operators. ( +, -, /, %, *)](#arithmetic-operators)
2.  [Comparison Operators](#comparison-operators)
3.  [Bitwise Operators](#bitwise)
4.  [Increment / Decrement Operators](#inc)
5.  [Logical Operator](#lo)
6.  [Ternary Operators](#ternary-operators)
7.  [Comma Operator](#comma-operator)
8.  ["this" Keyword](#this)
9.  [Scope and Scope Chaining](#scope)
10.  [Closures](#closures)
11.  [Typed Coercion](#typedc)
12.  [Promise](#promises)
13. [Async](#async)
14. [Syncronous Javascript](#syncJS)
15. [CallBack Hell](#callback-hell)
16. [Promise Chaining](#pchain)
17. [Async and await ](#)
18. [Event loop & Task Queue](#eventloop)



#### Arithmetic Operators

```javascript
console.log(2+3); 5
console.log(2-3); -1
console.log(2/3); 0.66666666666
console.log(2%3); 2
console.log(2*3); 6
```

#### Comparison Operators

```javascript
console.log(2>3); false
console.log(2<3); true
console.log(2>=3); false
console.log(2<=3); true
console.log(3<=3); true


  == and === != and !==
  (different kinds of operators in comparison)
  == and != always looks for values only and not the datatypes.
  === and !== always looks for both the values and the datatypes.
 console.log(3 == '3');true
 console.log(3 === '3');false
 console.log("hari" == "hari");true
  console.log("hari"=== hari);referenceError;
 console.log(3 != "3");false
 console.log(3 !== "3");true

```

#### Bitwise Operators (& ,| , !)<a name="bitwise"></a>

```javascript
console.log(2&3); 2
console.log(2|3); 3
console.log(!2); false
console.log(!0); true
console.log(!true); false

```

#### Increment Decrement Operators<a name="inc"></a>

> postfix and prefix operation  
> postfix increment or Postfix decrement var a; a++, a--  
> prefix increment or Prefix decrement var a, ++a, --a

```javascript

let a = 2;
console.log(a++);print the value of a, a=2 then goes for postfix operationa++a+2+a=3;
console.log(a);a=3; till this point in time a == 3
console.log(a++);print the value as a=3 a++ a+3 +a=4
console.log(a); a==4 a=4;
console.log(++a);++aa+4+a=5 print the value of a as 5.
console.log(++a);++aa+5+a=6 print the value of a as 6.

```

#### Logical Operator (&& , || , !) <a name="lo"></a>

```javascript
console.log( 5 && 3);
console.log( (3>2) && 3+);
console.log( (2>) && (3>2));
 left side value if 0, then the o/p is 0
 left side value if false, then the o/p is false
 left side value if non Zero, then the o/p is right side  value
 left side value if true, then the o/p is right side value

console.log( 5 || 3+0);true
console.log( true || 3);true
console.log( false || true);true
console.log( (2>3) || 3+);
console.log( (2>) || (3>2));
 left side value if false, then the o/p is right side value
 left side value if zero, then the o/p is right side value
 left side value if Nonzero, then the o/p is Non Zero left  side value itself
 left side value if true, then the o/p is true itself

```

#### Ternary Operators

> condition ? for true, this statement will be executed : for false, the last statement will be executed; any one of the statement is executed of the two, depending on the condition's value i.e true/false.

```javascript
let b = 3;45
b > 4 ? console.log("B is greater than the other no"):  console.log("B is smaller than the other no");

((b > 2) && (b++)) ? console.log(b++): console.log(++b);first print b = 4; b++
console.log(b);

```

#### Comma Operator

```javascript
let x = (6,7);
console.log(x); 7

x = (x++, x++, x);
x = (x++, x++, ++x);
x = (x++, x++, x++); postfix operation to the rightmost variable 'x' don't work;
console.log(x);9

```

----------

#### _This_ keyword <a name="this"></a>

> 'This' refers to the object in which it's used. Normally this refers to the window object only, whether in strict or non strict mode. It can have different values as per the method we call or invoke it. If inside the function, 'this' points to the global Object\[window\] but If used in strict mode then will be undefined.

```javascript
const student = {
     fName: "Ram",
     lName: "Kumar",
     fullName(){
         console.log(`${this.fName} ${this.lName} is the student's name`);
     }
 }

 student.fullName();
 let myName = "Sid";
if variable is declared with var  keyword or no keyword then it becomes the property of window object
else for let and const, it don't become the property for window object
 'use strict'
 console.log(this);window Object

 function Hello(){
     'use strict'
      console.log("hello");
     console.log(this);
 }
 Hello();

strict basically allows us to write our code in strict format.

 'use strict';
 myAge = 27;
 console.log(myAge);
 console.log(this);

Getters and Setters

 const employee = {
     fName: "Ramesh",
     lName: "Thakur",
     get fullName(){
         console.log(`${this.fName} ${this.lName} is the employee's name`);
     },
     set fullName(value){
         const names = value.split(" ");
         this.fName = names[0];
         this.lName = names[];
     }
 }
 console.log(employee.fullName);
 employee.fullName;
 console.log(employee.fName);

 employee.fullName = "Manoj Thakkar";
 console.log(employee);

```

#### Classes in Javascript

> In OOPS, a class is an extensible program code template for creating the objects, providing the initial values and the functions to the object that is created. Class can have a default method called constructor(), this is basically called whenever an object is created with a new keyword.

```javascript
const rajiv = {
     name: "Rajiv Das",
      employeeId: 00,
         printDetails: function(){
             console.log(this.name);
         }
 }

class Employee {
    constructor(enteredName, empId){
        this.name = Employee.capitalize(enteredName);
        this.employeeId = empId;
    }
    markAttendance(){
        console.log(`${this.name} with the employee id ${this.employeeId} has marked its attendance successfully`);
    }
    applyLeave(){
        console.log(`${this.name} with the employee id ${this.employeeId} has applied for leave successfully`);
    }
     fillDetails(enteredName, empId){
         this.name = enteredName;
         this.employeeId = empId;
     }
    static capitalize(name){
        return name.charAt(0).toUpperCase() + name.substr(,name.length);
    }
}

let rajiv = new Employee("rajiv Das",00);
let sanjiv = new Employee("sanjiv Kumar",002);
 let rajiv = new Employee();
 rajiv.fillDetails("Rajiv Das",00)
console.log(rajiv);
console.log(sanjiv);

rajiv.markAttendance();
rajiv.applyLeave();

 rajiv.capitalize();
 object rajiv cannot call the capitalize method, as it has the keyword static.

```

> **Static Methods**:\- Static methods are used to implement functions that belong to the class as a whole and not to any specific object.

#### Class Inheritance in JavaScript

> Class Inheritance is a way to inherit one class properties and methods to another class. this is done using the keyword extends.

```javascript
class Manager extends Employee {
    operations(){
        console.log("The manager is performing its operation");
    }
    markAttendance(){
         console.log("The manager is marking its attendance");
        super.markAttendance();
    }
}

let manish = new Manager("manish Jain", 003);
console.log(manish);

manish.applyLeave();
manish.markAttendance();
manish.operations();
 rajiv.operations();

```

> **Method Overriding** \- If we create an own function of markAttendance in Class Manager, then it wont use the inherited function from the Class Employee.

#### Scope and Scope Chaining <a name="scope"></a>

Types of scope . Local Scope. 2. Block Scope. 3. Function Scope. 4. Global Scope.

```javascript
var a  = ;global scope
{
     console.log(a);
    const a = 0;
    console.log(a);0
}
console.log(a);0
let and const are block scoped.

var b = 2;
{
    console.log(b);
    var b = 20;
    console.log(b);
}

function hello(){
    let a = "HI"
    console.log(a);
}
hello();
 console.log(a);
console.log(this);

scope chaining
let a = 0;
function one(){
    console.log(a);
    let b = 30;
     console.log(b);
    two();
    function two(){
        console.log(a);
        console.log(b);
    }
}
one();

```

#### Closures

>-  Closure makes a function remember all variables that existed at function's birth place initially.  
>- Any function always have access to variables environment of execution context in which the function was created.

```javascript
function nameOne(){
    let name = "Haresh";
    console.log(name);
    let anotherName = function(){
        console.log (`Hi I am ${name}`)
    }
    return anotherName;
}
let c = nameOne();
 console.log(c);
c();
console.dir(c);


let f ;
const g = function(){
    const a = 23;
    f = function(){
        console.log(a*2);
    }
};
const h = function(){
    const b = 25;
    f = function(){
        console.log(b*2);
    }
};
g();
h();
f();
console.dir(f);

```

> **Typed Coercion** : It is automatically converting the data type of the variable from one type to the another.

```javascript
let valueOne = "5";
let valueTwo = 3;
 let sum = valueOne + valueTwo;
let sum = Number(valueOne) + valueTwo;
console.log(sum, typeof(sum));

let named = "Raj";
let namedOne = "23";
let title = true;
console.log(named+title);

console.log(Number(named));
console.log(Number(namedOne));

let number = 5;
let bool = true;
let boole = false;0
console.log(number+bool);6
console.log(number+boole);5

let num = 23;
let str = "23";
console.log(num+str);

// call , apply , bind- allows us for function borrowing.

let showDetails = function(gender, age){
    console.log(`${this.fullName} is the name  of the employee with the employee ID as ${this.employeeId} 
    and working in the ${this.department} department having gender as ${gender} and age as ${age}`);
}

let employee1 = {
    fullName: "Harsh Bajaj",
    employeeId: 101,
    department: "Technical",
}

let employee2 = {
    fullName: "Ravi Prasad",
    employeeId: 102,
    department: "Sales",
}

let employee3 = {
    fullName: "Pinky Tambi",
    employeeId: 103,
    department: "Advertisement",
}

 employee1.showDetails();
 employee1.showDetails.call(employee2);

 console.log("Call Method");
 showDetails.call(employee1,"Male",24);
 showDetails.call(employee2,"Male",25);
 showDetails.call(employee3,"Female",24);

 console.log("Apply Method");
 showDetails.apply(employee1,["Male",24]);
 showDetails.apply(employee2,["Male",25]);
 showDetails.apply(employee3,["Female",24]);

 console.log("Bind Method");call the function anytime later u want it to call
 let value1 = showDetails.bind(employee1);
  console.log(value1);
 value1("Male",24);

 let value2 = showDetails.bind(employee2);
  console.log(value1);
 value2("Male",25);

 let value3 = showDetails.bind(employee3);
  console.log(value1);
 value3("Female",24);


 Introduction to Asynchronous JavaScript.

 setTimeout(() => {
      console.log("I am printing the result in 5 secs");

 }, 5000);

```

> **Callback Hell** - Callbacks are just the name/convention for using JavaScript. 
> - It instead of immediately returning results like other functions, takes time to produce the result. So, If we stuck in some particular call which prevents us from making further calls ends us into callback Hell.  
> - The structure of callback hell looks like pyramid/arrow shape. This makes our code look haphazard and makes it hard to understand.  
> - We should always try to avoid using multiple Callbacks to end up falling into callback hell. We use Promises to prevent using Callbacks and thereby avoiding Callback Hell.

#### Promises

> **Promises** - Promises are used to handle asynchronous operations in JavaScript. 
> - They are easy to manage when dealing with multiple asynchronous operations where callbacks can create callback hell leading to unmanageable code. 
> - It also allows us to make API calls or fetch data from Web Servers successfully. If not able to do so fetches us with an error message.

> It have three stages.
> 
> 1.  Pending
> 2.  Resolved(fulfilled)
> 3.  Rejected.

```javascript
// Promise producer
let promise = new Promise((resolve, reject)=>{

    setTimeout(() => {
        let id = 13; // this data has come from backend after making some asynchronous call by hitting an API
        if(id == 23){
            resolve(id);
        }
        reject("Didn't found data");
    }, 3000);
})
// Promise consumer
promise 
    .then((value)=>{
        console.log("This is the value",value);
    })
    .catch((err)=>{
        console.log("The error is",err);
    });
        .finally(()=>{
         console.log("End of promise");

        })

```

##### Promise Chaining

```javascript
let promise = new Promise((resolve, reject) => {
     resolve();
 })

 promise
     .then(()=>{
         console.log("first response");
     })
     .then(()=>{
         return new Promise((resolve, reject) => {
             setTimeout(() => {
                 console.log("second response");
                 resolve();
             }, 2000);
         })
     })
     .then(()=>{
         console.log("third response");
     })


const getId = new Promise((resolve, reject) => {
	setTimeout(() => {
		let id = [1, 2, 3, 4, 5];
		resolve(id);
		reject('Error in fetching the details'); //either of resolve or reject is executed on the basis of data received.If received then resolve is called otherwise reject is called. Resolve hits the .then() method and the reject hits the .catch method()
	}, 2000);
});

const getEmpDetails = (data) => {
	return new Promise((resolve, reject) => {
		setTimeout((data) => {
				let empDetails = {
					fName: 'Ravi',
					lName: 'Patel',
					age: 24,
				};
				resolve(`The id of employee is ${data} 
				and the name of the Employee is ${empDetails.fName} 
				${empDetails.lName} and the age is ${empDetails.age}`
				);
			},
			2000,
			data
		);
	});
};
```

#### Synchronous JavaScript: <a name="syncJS"></a>

```javascript
let a = 3;//3
let b = 6;//6
let result  = a + b;//3 + 6//9
console.log(result);//9
/*
 //parameters
function add(a,b){
    console.log(a+b);
}
 add(3,4);
//args
*/
```


#### Asynchronous JavaScript: It might execute then or after certain period of time.

```javascript
setTimeout((a,b) => {
     console.log("I want to print something after 2 secs",a,b);
 }, 5000,"apple","mango");
//callback function - setTimeout Function // 1000ms  = 1 sec

 setTimeout(function(a,b){
     console.log("I am also executing",a,b);
 }, 3000, "apple","mango");

// console.log("I can print anything right now");

setTimeout(() => {
    console.log("svhsvhs");
}, 2000);

// Timer functions in Async JS
// setTimeout, setInterval
//1st callback function, Timeout Period

setInterval(() => {
    console.log("I am printing after every 2 secs");
}, 2000);


 const mocktails = ["virgin Mojito","BlueLagoon","Mocktail"];
 const myTimer = setInterval(() => {
     console.log("I want to have a mocktail");
 }, 2000);

 if(mocktails.includes("virgin Mojito")){
     clearInterval(myTimer);
 }

// callback Functions - these are those kind of functions which can be called back after certain period of time
// or gets automatically called back after certain period of time.

const sayHi = (friend) => {
    console.log(`Hello my friend ${friend}`);
}
const greeting = (friend, callBackFn) => {

    callBackFn(friend);//function call//sayHi("Ravi")
}

greeting("Ravi",sayHi);
// sayHi("Ravi")


// Multiple callbacks/ Nested Callbacks - it brings certain disadvantages for us.

// 1. CallBack Hell;
// 2. Inversion Of Control

const items = ["Jeans","SHirt","Belts"];

// Task.addItemsToCart
// Task.MakeThePayment
// Task.OrderSummary
// Task.updateTheWallet

// task.addItemsToCart(function(){

//     task.MakeThePayment(function(){

//         task.OrderSummary(function(){

//             task.updateTheWallet();
//         })

//     })

// })

//callback Hell
//Pyramid Of Doom/ Arrow Shape.
// It is unmanageable code.
//It looks like code is arranged in a horizontal manner.

//Inversion of Control
// The control of the problem inverts from its natural path.

//Therefore we should always avoid using nested callback functions.

// Solutions for the problems faced by using nested Callback functions: Using Promises


// Promise - It is an object that represents eventual completion of an asynchronous task.
// a future value for the task.

// Three states:
// Pending , Fulfilled, Rejected


// resolve() -> .then()
// reject() -> .catch()

const promise = new Promise((resolve,reject)=>{//producer
   /* const api = 'https://jsonplaceholder.typicode.com/todos/';
    const result = fetch(api);
    console.log(result);*/
    if(result === true)
    {
    resolve(result);
    }else{
       reject(err);
       // reject is skipped if resolve is executed else part is optional.
    }
    
})

promise //consumer
    .then((data)=>{
        console.log(data.body);
    })
    .catch((err)=>{
        console.log("the error is",err);
    })
    .finally(()=>{
        console.log("End of Promise");
        
    });
```
#### CallBack Hell
>Callback Hell causing functions
```javascript
function addItemsToCart(list, callbackFn){
    setTimeout(() => {
        callbackFn(`The items to be ordered ${list}`);
    }, 1000);
}

function makeThePayment(paymentInfo, callbackFn) {
    setTimeout(() => {
        callbackFn(`The price to be paid is ${paymentInfo}`);
    }, 1000);
}

function orderSummary(orderDetails, callbackFn){
    setTimeout(() => {
        callbackFn(`The details of the order are ${orderDetails}`);
    }, 1000);
}

// nested callback functions : thereby leading to callback hell

const message = addItemsToCart("Jeans & Shirt", function (message) {
    console.log(message);
    makeThePayment("1050/-", function(payment){
        console.log(payment);
        orderSummary("Ordered Jeans & Shirt",function(order){
            console.log(order);
        })
    })
}); 


/* Promise Revision
const promise = new Promise((resolve,reject)=>{//Producer
    setTimeout(() => {
        const result = false;
        if(result === true){
            resolve("I am resolved");
        }
        else{
            reject("I am rejected");
        }
    }, 1000);
})

promise
    .then((res)=>{
        console.log(res);
    })
    .catch((err)=>{
        console.log(err)
    })
    .finally(()=>{
        console.log("End of Promise");
    })*/

```
>Solution 1 :
```

function addItemsToCart(list){
//callback executer functions resolve and reject
//Producers
    return new Promise((resolve,reject)=>{
        setTimeout(()=>{
            resolve(`$The items to be ordered ${list}`)
        },1000);
    })
}

function makeThePayment(payInfo){
    return new Promise((resolve,reject)=>{
        setTimeout(()=>{
            resolve(`$The price paid is ${payInfo}`)
        },1000);
    })
}
function orderSummary(orderDetails){
    return new Promise((resolve,reject)=>{
        setTimeout(()=>{
            resolve(`$The details of the order are$ {orderDetails}`)
        },1000);
    })
}
// Consumer 
addItemsToCart("Jeans And Shirt").then((res1)=>{
    console.log(res1);
    makeThePayment("1050/-").then((res2)=>{
        console.log(res2);
        orderSummary("Order Jeans And Shirt").then((res3)=>{
            console.log(res3);
        })
    })
});
```
#### <a name="pchain"></a> Promise Chaining - It Helps to Improve the ==pyramid of doom== from the ==*nested promises*==

```javascript
addItemsToCart("Jeans And Shirt")
.then((res1)=>{
    console.log(res1);
    return makeThePayment("1050/-")
})    
.then((res2)=>{
    console.log(res2);
    return orderSummery("Order Jeans And Shirt")
})
.then((res3)=>{
    console.log(res3);
})
.catch(err =>{
    console.log(err)
})
.finally(()=>{
    console.log("Promise Chain ended here")
})
```
##### Promise Combinators
>Starting functions
```javascript
function addItemsToCart(list){
    return new Promise((resolve,reject)=>{
        setTimeout(() => {
            // resolve(`The items to be ordered ${list}`);
            reject("I am rejecting the promise1")
        }, 1000);
    })
}

function makeThePayment(paymentInfo) {
    return new Promise((resolve,reject)=>{
        setTimeout(() => {
            // resolve(`The price to be paid is ${paymentInfo}`);
            reject("I am rejecting the promise2")
        }, 1000);
    })
}

function orderSummary(orderDetails){
    return new Promise((resolve,reject)=>{
        setTimeout(() => {
            // resolve(`The details of the order are ${orderDetails}`);
            reject("I am rejecting the promise3")
        }, 1000);
    })
}

addItemsToCart("Jeans & Shirt")
    .then((a)=>{
        console.log(a);
        makeThePayment("1050/-")
            .then((b)=>{
                console.log(b);
                orderSummary("Ordered Jeans & Shirt")
                    .then((c)=>{
                        console.log(c);
                    })
            })
    })
```
> **Promise.race()** : It returns the first promise which resolves or rejects.

```javascript
Promise.race([
    addItemsToCart("Jeans & Shirt"),
    makeThePayment("1050/-"),
    orderSummary("Ordered Jeans & Shirt")
])
.then((res)=>{
    console.log(res);
})
.catch((err)=>{
    console.log(err);
})
```


   > **Promise.all()** : It allows us to execute multiple promises at a time. It would run only if all the promises are resolved. Even if one of the promise doesn't resolve, then the entire promise is said to be rejected
   ```javascript
Promise.all([
    addItemsToCart("Jeans & Shirt"),
    makeThePayment("1050/-"),
    orderSummary("Ordered Jeans & Shirt")
])
.then((res)=>{
    console.log(res);
})
.catch((err)=>{
    console.log(err);
})
```

   
 >**Promise.allSettled()** : It returns all the promises including both the resolved and the rejected promises.
Unlike Promises.all() it wont resolve only if all the promises are resolved otherwise reject, instead will
give the status for all the promises


```javascript
Promise.allSettled([
addltemsToCart("Jeans & Shirt"),
makeThePayment("1050/-") ,
orderSummary( "Ordered Jeans & Shirt")
])
.then((res)=>{
console.log(res);
))
.catch((err)=>{
console.log(err);
})
```


>**Promise.any()** :
This returns the first resolved promise. What if all the promises are rejected?
In that case it shall return that the promises are rejected.

```javascript
Promise.any([
    addItemsToCart("Jeans & Shirt"),
    makeThePayment("1050/-"),
    orderSummary("Ordered Jeans & Shirt")
])
.then((res)=>{
    console.log(res);
})
.catch((err)=>{
    console.log(err);
})
```
#### Async Await

> Async : - Its a special method to work with promises in JS. 
> - A function can be made asynchronous by adding the
async keyword to it. An async function always returns a promise. So, async ensures that the function returns
 a promise and wraps the non promises in it. 

```javascript
async function add(a,b){
    console.log(a+b);
}

const add = async() => {
    let a = await anyFunction;
 }
```


 > **Await** : This is another keyword that works inside async "functions" only. 
 >- The await keyword makes javaScript wait until the promise is settled and returns a value. It makes
it easy to read and use promises efficiently.
 *Async and Await works together*
```javascript
async function weatherUpdate() {
  let bombayWeather = new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("The temp in Bombay is 33 degree Celsius");
    }, 2000);
  });

  let kolkataWeather = new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("The temp in Kolkata is 31 degree Celsius");
    }, 4000);
  });
/* by Promise method

   bombayWeather
   .then((res)=>{
       console.log(res);
   })
   .catch((err)=>{
       console.log(err);
   })
  kolkataWeather
   .then((res)=>{
       console.log(res);
   })
   .catch((err)=>{
       console.log(err);
   })
  */

  console.log("Getting weather detail of Bombay");
  let bombay = await bombayWeather;
  console.log("Got weather detail of Bombay");

  console.log("Getting weather detail of Kolkata");
  let Kolkata = await kolkataWeather;
  console.log("Got weather detail of Kolkata");
  return [bombay, Kolkata];
}

const printSomething = ()=> {
    console.log("Hey I am Printing any Casual things out here !!");
}
weatherUpdate()
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  });
  printSomething();
```
```javascript
async function mainFunction(){
    await weatherUpdate()
    .then((res)=>{
        console.log(res);
    })
    .catch((err)=>{
        console.log(err);
    })
    printSomething();
}

mainFunction();
console.log("i am a random message");

function addItemsToCart(list){
    return new Promise((resolve,reject)=>{
        setTimeout(() => {
            // resolve(`The items to be ordered ${list}`);
            reject("I am rejecting the promise1")
        }, 1000);
    })
}

function makeThePayment(paymentInfo) {
    return new Promise((resolve,reject)=>{
        setTimeout(() => {
            // resolve(`The price to be paid is ${paymentInfo}`);
            reject("I am rejecting the promise2")
        }, 1000);
    })
}

function orderSummary(orderDetails){
    return new Promise((resolve,reject)=>{
        setTimeout(() => {
            // resolve(`The details of the order are ${orderDetails}`);
            reject("I am rejecting the promise3")
        }, 1000);
    })
}

const shopping = async() => {
try{
    const taskl = await addltemsToCart( "Jeans & Shirt");
    console.log(taskl);
    const task2 =  await makeThePayment( "1050/-")
    console.log(task2) ;
    const task3 = await orderSummary( "Ordered Jeans & Shirt");
    console.log(task3) ;
}catch (err) {
    console.log(err) ;
}
}
shopping();
```

#### <a name="eventloop"></a> Event Loop and Task Queue

>JavaScript :
JS is such a code which doesn't wait for anything.
> 1. JS is single threaded language, non blocking, asynchronous language.
> 2. It has a call stack, event loop, callback queue and other API's
> 3. V8 engine has call stack and a Heap.
> 4. This heap is used for memory allocation and the stack holds the execution context.
DOM, set Timeout, XML, HTTRequests, don't exist in v8 source code.

>**Event Loop** : 
Its responsible for executing code, collecting and processing the events and executing the queued tasks.
>- Event loop pushes the waiting tasks from the task queue to the call stack in the order they are inserted
only if the call stack is found empty.
>- set Timeout (()=>{},0) still it will be queued in the task queue by the event loop.

>**Task Queue** :
JS can do only one task at a time.
Rest are queued to the task queue waiting for the current task executing to get finished.
>- When we run set Timeout, webAPI's run a timer and after the timer is finished, it pushes the set Timeout
in to the task queue.
>- These waiting tasks in the task queue are then pushed in to the call stack by the event loop where they
can be executed.