# section 1. Basic

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

6. DOM : Document Object Mark
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
# section 2. Advanced

useStrict mode, Closer, Event loop, Async,...
regex


---
# section 3: Reference

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

