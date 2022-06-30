# Section 1. Basic

1. ##Data type -> Dynamic type
- Number, String, Boolean, NaN, Undefine, Null , (BigInt, Symbol)  => __(typeof null = 'object' | typeof NaN = 'number' | typeof undefine = 'undefine')__
- Object collections: Object, Array,  Map, Set, WeakMap, WeakSet, Date
- Truthy, Falsy(false|0|''|null|undefine|NaN|-0|0n)
- Ternary: a === b ? result_true | result_false;


2. Function
- Reference parameter : There is __no "pass by reference"__ available in JavaScript. You can __pass an object__
- Function trung ten
- Ham trong ham
- 3 Loai Function: 
  + Declaration function: ` function funcName(){} ` => __hoisting__
  + Expression Function: `const funcName = function () {} `  => __no hoisting__
  + Arrow function  : `const sum = () => {}`   => __no hoisting__
- Polyfill: function trong es5 nhung khong duoc ho tro o tren cac trinh duyen cu
- Default param: auto convert null to 0
- Rest parameter: `arguments, sum(...listParams)`
- Spread parameter: `sum(...arrayParams)`

3. Object
- Constructor: __new__ User('name', 10);
- Prototype : Object.prototype.name = value | function
- Combine : Object.assign(object1, object2);
- Date:
- Object.keys(obj)
- Remove key of Object
- Check key exist
- Object.freeze(obj);
- Clone Object: clone deep

4. Array
- Mot so ham co ban
  + __forEach()__
  + __map()__
  + __reduce()__
  + every()
  + some()
  + find()
  + filter()

- Combine array: array3 = array1.concat(array2) => tao ra cung nho moi cho array3
- Insert to Array.
- Remove element of Array.


5. Import, Export
- Export: export {varName}, export default varNameDefault
- Import: import {varName} from '../../fileName', import varNameDefault from '../../fileName'

6. DOM : Document Object Model
- W3C: World Wide Web Consortium
- document: Element, Attribute, Text
- Element: id, class, tag, css selector, HTML collection : document.getElementBy...(ID|ClassName|TagName)
  + document.get**Element**ByID(): return html element
  + document.get**Elements**ByClassName(): return html collections
  + document.get**Elements**ByTagName(): return html collections
  + document.query**Selector**('.heading'): return html element
  + document.query**SelectorAll**('.heading'): return html collections
  + document.forms['form-ID']
- Attribute: element.getAttribute('attributeName'); element.setAttribute('attributeName', value);
- Text: innerText, textContent
---
# Section 2. Advanced

1. useStrict mode: Sử dụng sự nghiêm ngặt
- Gán giá trị cho biến chưa được khai báo.
```
   variable = "tranvanmy";
   console.log(variable);`
   // Ok
```
```
   "use strict"
   variable = "tranvanmy";
   console.log(variable);

   Uncaught ReferenceError: variable is not defined
```
- Báo lỗi khi sử dụng delete
```
   function getMyName (name)
   {
      console.log(name)
   }
   delete getMyName;
   //không có gì xảy ra mặc dù delete không xóa được hàm
```

```
   "use strict"
   function getMyName (name)
   {
      console.log(name)
   }
   delete getMyName;
   //Uncaught SyntaxError: Delete of an unqualified  identifier in strict mode.
```
- Tránh đặt nhầm trùng tên các tham số
- Báo lỗi trong một số được hợp không được phép
- Không sử dụng được một số từ khóa dễ gây nhầm lẫn hoặc được coi là có thể được thêm vào ngôn ngữ trong tương lai
[reference more >>](https://viblo.asia/p/use-strict-la-gi-va-cach-su-dung-trong-javascript-3P0lPz2mKox)
   
2. __Event loop__: 
- Js is Single Thread (Thread # Process)
- Thanh phan: __Heap__(Code), __Call Stack__, __WEB API__, __EVENT QUEUE__,**Event Loop**
- Key word: Single Thread, Memory Heap, Call stack, Stack trace (Error exception), Stack overflow, Asynchronous, 
- [demo >>](http://latentflip.com/loupe)
- [more >>](https://www.youtube.com/watch?v=64ASqMjj9_o&t=57s)


3. Scope
- Block scope
- Function scope
- Lexical scope:
```
   const name = 'Mr.Bean';
   function sayHello() {
      const language = 'en';
      console.log(name);
      // the lexical scope of name is global scope
      function printLanguage() {
         console.log(language); 
         // the lexical scope of language is a function scope (sayHello)
      }
   }
```
- Global scope
  - Browser: window
  - Nodejs : global
   -> globalThis : window, global
- Scope chain
```
   // First fullName variable defined in the global scope:
   const fullName = "Grandparent";
   // Nested functions containing two more fullName variables:
   function profile() {
      const fullName = "Parent";
      
      function sayName() {
         const fullName = "Boooom";
         
         function writeName() {
            return fullName; //Boooom
         }
         return writeName();
      }
      return sayName();
   }
```

4. Hoisting
- Hoisting là một cơ chế Javascript mà các __variable__ và __function__ khi khai báo sẽ được __đưa lên trên cùng (only khai báo)__ của scope trước khi code thực thi.
| __#__                | __Hoisting__ | __Example__                     |
| -------------------- | ------------ | ------------------------------- |
| var                  | __YES__      | var name = 'Mr.Bean'            |
| const/let            | NO           | let name = 'Mr.Mean'            |
| function declaration | __YES__      | function sayHi(){}              |
| function expression  | NO           | const sayN = function sayHi(){} |

```
   console.log(name);
   var name = 'Mr.Bean';
   // Out put: undefined
```
- Browser: var name = 'mr.Bean' -> window.name = 'mr.Bean' => *avoid use var*
- var : function scope
```
   function sayHi(){
      {
         const name = 'Mr.Bean';
         var city = 'London';
      }

      console.log(name);      //ReferenceError
      console.log(city);      //Out put: London
   }
```
- **const/let có bị hoisting ko?**
-> **CÓ**, nhưng kèm theo **Temporal Dead Zone** (ko dùng được trước dòng khai báo)

5. `this`
- `this` in **Global** context -> **this = global object (window, global)**
- `this` in **normal function**
  - non-strict mode: **this = global object**
  - strict mode: **this = undefined**
- `this` in **arrow function**: 
   `this` from outer (ke thua tu ben ngoai)
```
   const sayHello = () => {
      console.log(this); // this = window or global
   }
```
```
   'use strict';
   const sayHello = () => {
      console.log(this); // this = window or global
   }
```

```
   'use strict'
   function sayHello() {
      console.log(this); // undefined
      const getLanguage = () => {
         console.log(this); // same as this from outer normal function => undefined
      }
      getLanguage();
   }
```
- `this` in a **method** : `this` is owner object
```
const student = {
   name: 'Bob',
   // ES6 property methods
   sayHello() {
      console.log('My name is', this.name);
   }
}
student.sayHello(); // 'My name is Bob'
```

```
'use strict'
// avoid using arrow function in object methods
const student = {
   name: 'Bob',
   
   // __arrow function__
   sayHello: () => {
      console.log('My name is', this.name);
   }
}
student.sayHello(); // 'My name is **undefined**'
```

- `this` in an **event**: `this` = an element that received the even

1.  bind, call, apply
NOTE:  Only works with regular function, **NOT arrow function**.
| #                   | **bind**     | **call**            | **aplly**           |
| ------------------- | ------------ | ------------------- | ------------------- |
| bind `this` context | yes          | yes                 | yes                 |
| Return              | new function | result of func call | result of func call |
| Time of binding     | now          | now                 | now                 |
| Time of exec        | future       | now                 | now                 |
| Params              | -            | arguments           | an array of params  |

```
   function sayHi(a, b) {
   console.log(this.name, " say hi! ", a + b);
   }

   const obj = {
   name: "Mr.Bean"
   };

   const newFunc = sayHi.bind(obj);
   newFunc(2, 3);
   // out put: Mr.Bean say hi! 5

   sayHi.call(obj, 3, 3);
   //out put: Mr.Bean say hi! 6

   sayHi.apply(obj, [3, 4]);
   //out put: Mr.Bean say hi! 7
```
[read more >>](https://javascript.plainenglish.io/quick-guide-to-call-apply-and-bind-methods-in-javascript-5c00cd856cfa?gi=a6a05d389196)

7. IIFE - Immediately Invoked Function Expression
Hàm tạo ra chỉ để sử dụng duy nhất đúng 1 lần.
```
   // syntax
   (function (name) {
      console.log('IIFE', name);
   })('Mr.Cool');
   // out put: IIFE Mr.Cool

   // IIFE with arrow function
   (() => {})();
   
   (() => {
      console.log('IIFE');
   })();
```

8. HOF - Higher Order Function
- La Function co tham so truyen vao la function, hoac gia tri tra ve la 1 function
```
   function funcParent(){
      var x = 10;
      function children(){
         return ++x;
      }

      return children;
   }

   console.log(funcParent());    
   //Out put: 
   //   function children(){
   //      return ++x;
   //  }

   console.log(funcParent()());    // Out put: 11

   
```

9. Closure
- A closure is a function having access to the parent scope, even after the parent function has closed.
- Ung dung: Co the tao ra duoc cac bien **private** trong ham.
- Stateful Function la function co kha nang luu tru bien
```
   function makeFunc() {
      var num = 10;
      function plus(x) {
         return num + x;
      }
      return plus;
   }

   var myFunc = makeFunc();   // The parent function has closed
   console.log(myFunc(1));    // out put: 11
   // Access to the parent scope   
   console.log(myFunc(1)); // out put: 12

```

10. Currying
- **Currying** is the process of taking a function with **multiple arguments** and return a series of functions that take **one argument** and eventually resolve to a value
- 1 ham nhieu tham so -> nhieu ham co 1 tham so (preload data)
- Why should I use currying:
  - Currying is a checking method to make sure that you get everything you need before you proceed
  - It helps you to avoid passing the same variable again and again
  - It divides your function into multiple smaller functions that can handle one responsibility
```
   // Function with multiple arguments
   function fncMultipleArgs(x,y,z){
      return x + y + z;
   }
   console.log(fncMultipleArgs(1,2,3));   //out put: 6

   //Series of functions that take one argument
   function fncX(x){
      return function fncY(y){
         return function funcZ(z){
            return x + y + z; 
         }
      }
   }
   console.log(fncX(1)(2)(3));      // out put:6 

```

11. Callback
- Callback function is Function as arguments
- Truyen function vao 1 function khac duoi dang arguments.
```
   function myFunc(myCallBack){
      setTimeout(function() {
         console.log("My Function");
         myCallBack();
      }, 100)
   }

   function yourFunc(){
      console.log("Your Function is my Call back function");
   }

   myFunc(yourFunc);
   //out put:
   //    My Function
   //    Your Function is my Call back function
```

12. Promise
**Keep Going**


13.  Constructor Function & Factory Function
- Constructor Function
```
   function User(name, age){
      this.name = name;
      this.age = age;

      this.showName = function (){
         console.log(`Name ${this.name}`);
      }
   }

   const bean = new User('Mr.Bean', 54);     // Out put: "Name: Mr.Bean Age: 54"
   console.log(`Name: ${bean.name} Age: ${bean.age}`);   // Out put: "Name Mr.Bean"
   bean.showName();

   const jack = new User('Jack Sparrow', 60);
   jack.showName();     // Out put: "Name Jack Sparrow"

```

- Factory Function: Dua tren Closure, HOF
```
   function FactoryUser(name, age){

      function showName(){
         return `Name: ${name}`;
      }

      function showAge(){
         return `Age: ${age}`;
      }

      return {
         showName: showName,
         showAge: showAge
      }
   }

   const jim = FactoryUser('Jim', 32);
   console.log(jim.showName(), jim.showAge());        // Out put: "Name: Jim Age: 32"

   const jqk = FactoryUser('JQK', 102);
   console.log(jqk.showName(), jqk.showAge());     // Out put: "Name: JQK Age: 102"

```
14. IIFE -> Module Pattern
- Dua tren 3 co che: Closure, IIFE, HOF
```
   var Module =(function(){
      let private1 = [10];
      let private2 = 90;
      
      function privateFunc(){
         console.log('Data private1 : '+ private1[0]);
         console.log('Data private2 : '+ private2);
      }
      
      return {
         publicData1: private1,
         publicData2: private2,
         publicFunc: function() {
            privateFunc();
         }
      }
   })()

   console.log(Module.publicData1[0]);    // Output: 10
   console.log(Module.publicData2);       // Output: 90

   Module.publicData1[0] +=  5;        
   Module.publicData2 +=  5;

   console.log(Module.publicData1[0]);    // Output: 15
   console.log(Module.publicData2);       // Output: 95

   Module.publicFunc();
   // Output: 
   //    "Data private1 : 15"
   //    "Data private1 : 90"
```
15. 


Debounce, Throttle,
Generators : generator function, generator object
Destructuring Assignment

Catching, throwing errors
Template strings
[Map, Set](https://xdevclass.com/tat-ca-nhung-gi-ban-can-biet-ve-map-va-set-trong-javascript/)
[Symbol](https://xdevclass.com/kieu-symbol-trong-javascript-co-the-ban-chua-tung-nghe-thay/)
JavaScript Event Propagation
Regex

class, oop, iterable, iteration, observer, observable, micro queue, macro queue
Blob,  Buffer,  Stream
Prototype và _proto_ trong Object

---
# Section 3: Reference

https://github.com/yeungon/In-JavaScript-we-trust
https://github.com/yeungon/Javascript_Books

https://github.com/yeungon/30-Days-Of-JavaScript
https://javascript30.com/

https://github.com/yeungon/clean-code-javascript
https://github.com/hienvd/clean-code-javascript/

https://github.com/yeungon/js-quiz


https://oj.luyencode.net/

Q&A Quiz
Key Word: best practices

