# Section 1. Basic

1. Data type -> Dynamic type
   - Number, String, Boolean, NaN, Undefine, Null , (BigInt, Symbol)  => __(typeof null = 'object' | typeof NaN = 'number' | typeof undefine = 'undefine')__
   - Object collections: Object, Array,  Map, Set, WeakMap, WeakSet, Date
   - Truthy, Falsy(false|0|''|null|undefine|NaN|-0|0n)
   - Ternary: a === b ? result_true | result_false;


2. Function
   - Reference parameter : There is __no "pass by reference"__ available in JavaScript. You can __pass an object__
   - Function trung ten
   - Ham trong ham
   - 3 Loai Function: 
     * Declaration function: function funcName(){} => __hoisting__
     * Expression Function: const funcName = function () {}    => __no hoisting__
     * Arrow function  : 
   - Polyfill: function trong es5 nhung khong duoc ho tro o tren cac trinh duyen cu

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
     - __forEach()__
     - __map()__
     - __reduce()__
     - every()
     - some()
     - find()
     - filter()

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
   [reference more](https://viblo.asia/p/use-strict-la-gi-va-cach-su-dung-trong-javascript-3P0lPz2mKox)
   
2. __Event loop__: 
  - Js is Single Thread (Thread # Process)
  - Thanh phan: __Heap__(Code), __Call Stack__, __WEB API__, __EVENT QUEUE__,**Event Loop**
  - Key word: Single Thread, Memory Heap, Call stack, Stack trace (Error exception), Stack overflow, Asynchronous, 
  - [demo](http://latentflip.com/loupe)
  - [more](https://www.youtube.com/watch?v=64ASqMjj9_o&t=57s)


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
   | __#__ | __Hoisting__ | __Example__ |
   | var | __YES__ | var name = 'Mr.Bean' |
   | const/let | NO | let name = 'Mr.Mean' |
   | function declaration | __YES__ | function sayHi(){} |
   | function expression | NO | const sayN = function sayHi(){} |
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
      `this` from outer normal function (ke thua tu ben ngoai)
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
            console.log(this); // same as this from outer normal function
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

6.  bind, call, apply
   NOTE:  Only works with regular function, **NOT arrow function**.
   | #                   | **bind**      | **call**            | **aplly**           |
   | bind `this` context |   yes         |    yes              |    yes              |
   | Return              | new function  | result of func call | result of func call |
   | Time of binding     | now           | now                 | now                 |
   | Time of exec        | future        | now                 | now                 |
   | Params              |      -        | arguments           | an array of params  |

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
   [more](https://javascript.plainenglish.io/quick-guide-to-call-apply-and-bind-methods-in-javascript-5c00cd856cfa?gi=a6a05d389196)

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

8. Closure


9. HOF

Debounce, Throttle,
Async, Promise

Generators : generator function, generator object
Destructuring Assignment

Catching, throwing errors
Currying 
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

