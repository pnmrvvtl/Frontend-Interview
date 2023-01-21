# JS-Interview

## Questions

#### 1. Типы данных в JS. Приведение типов
Все типы данных в JavaScript, кроме объектов, являются иммутабельными (значения не могут быть модифицированы, а только перезаписаны новым полным значением). Например, в отличии от C, где строку можно посимвольно корректировать, в JavaScript строки пересоздаются только полностью. Значения таких типов называются «примитивными значениями».

- _Булевый тип данных_

Булевый тип представляет собой результат логического выражения и принимает одно из двух значений: true (истина) или false (ложь).
```javascript
let checked = true;
checked = false;    
```
- _Null_

Этот тип данных имеет всего одно значение: null. Смотрите null и Null для получения подробностей.
```javascript
let age = null;
```
- _Undefined_

Переменная, значение которой не было присвоено, имеет значение undefined. Смотрите undefined и undefined для получения подробностей.
```javascript
let x = 123;
x = undefined;
alert( x ); // "undefined"
```
- _Числа_

В соответствии со стандартом ECMAScript, существует только один числовой тип, который представляет собой 64-битное число двойной точности согласно стандарту IEEE 754. 
Другими словами, специального типа для целых чисел в JavaScript нет. 
Это означает, что при числовых операциях вы можете получить неточное (округлённое) значение. 
В дополнение к возможности представлять числа с плавающей запятой, есть несколько символических значений: +Infinity (положительная бесконечность), -Infinity (отрицательная бесконечность), и NaN (не число).
Для получения самого большого или самого меньшего доступного значения в пределах +/-Infinity, можно использовать константы Number.MAX_VALUE или Number.MIN_VALUE. 
А начиная с ECMAScript 2015, вы также можете проверить, находится ли число в безопасном для целых чисел диапазоне, используя метод Number.isSafeInteger(), либо константы Number.MAX_SAFE_INTEGER и Number.MIN_SAFE_INTEGER. 
За пределами этого диапазона операции с целыми числами будут небезопасными, и возвращать приближённые значения.
Ноль в JavaScript имеет два представления: -0 и +0. («0» это синоним +0). На практике это имеет малозаметный эффект. Например, выражение +0 === -0 является истинным. Однако, это может проявиться при делении на ноль:
> 42 / +0
Infinity
> 42 / -0
-Infinity
```javascript
  let n = 123;
  n = 12.345;
```

Подробнее: https://learn.javascript.ru/number

- _Текстовые строки_

В JavaScript для представления текстовых данных служит тип String. 
Он представляет собой цепочку «элементов» 16-битных беззнаковых целочисленных значений. 
Каждый такой элемент занимает свою позицию в строке. Первый элемент имеет индекс 0, следующий — 1, и так далее. 
Длина строки — это количество элементов в ней.
В отличие от языков подобных C, строки в JavaScript являются иммутабельными. 
Это означает, что после того, как строковое значение создано, его нельзя модифицировать.
 Остаётся лишь создать новую строку путём совершения некой операции над исходной строкой. 
```javascript
let str = "Мама мыла раму";
str = 'Одинарные кавычки тоже подойдут';
```

Подробнее: https://learn.javascript.ru/es-string

- _Тип данных Символ (Symbol)_

Символы являются нововведением JavaScript начиная с ECMAScript 2015. 
Символ — это уникальное и иммутабельное примитивное значение, которое может быть использовано как ключ для свойства объекта. 
В некоторых языках программирования символы называются атомами. Их также можно сравнить с именованными значениями перечисления (enum) в языке C. 

Подробнее: https://learn.javascript.ru/symbol#obyavlenie

- _Объекты_

В JavaScript объект может расцениваться как набор свойств. 
Литеральная инициализация объекта задаёт определённое количество начальных свойств, и в процессе работы приложения поля могут добавляться и удаляться. 
Значения свойств могут иметь любой тип, включая другие объекты, что позволяет строить сложные, разветвлённые иерархии данных. 
Каждое свойство объекта идентифицируется ключом, в качестве которого может выступать значение с типом Строка или Символ.
Создание объекта:
```javascript
1. let a = new Object();
2. let b = {}; // пустые фигурные скобки
```

Подробнее: https://learn.javascript.ru/object

Приведение типов:

##### Строковое преобразование.
Строковое преобразование происходит, когда требуется представление чего-либо в виде строки. Например, его производит функция alert.
```javascript
 let a = true;
 alert( a ); // "true"
 ```
Можно также осуществить преобразование явным вызовом String(val):
```javascript
 alert( String(null) === "null" ); // true
 ```
Как видно из примеров выше, преобразование происходит наиболее очевидным способом, «как есть»: false становится "false", null – "null", undefined – "undefined" и т.п.
Также для явного преобразования применяется оператор "+", у которого один из аргументов строка. В этом случае он приводит к строке и другой аргумент, например:
```javascript
 alert( true + "test" ); // "truetest"
 alert( "123" + undefined ); // "123undefined"
 ```
##### Численное преобразование.
Численное преобразование происходит в математических функциях и выражениях, а также при сравнении данных различных типов (кроме сравнений ===, !==).
Для преобразования к числу в явном виде можно вызвать Number(val), либо, что короче, поставить перед выражением унарный плюс "+":
```javascript
let a = +"123"; // 123
let a = Number("123"); // 123, тот же эффект
```
##### Логическое преобразование.
Преобразование к true/false происходит в логическом контексте, таком как if(value), и при применении логических операторов.
Все значения, которые интуитивно «пусты», становятся false. Их несколько: 0, пустая строка, null, undefined и NaN.
Остальное, в том числе и любые объекты – true.

Подробнее: https://learn.javascript.ru/types-conversion

#### 2. Что такое hoisting?
Hoisting (поднятие) - это механизм в JavaScript в котором переменные и объявления функций передвигаются вверх своей области видимости перед тем, как код будет выполнен. Это происходит, т.к. компиляция кода происходит в два прохода. При первом проходе компилятор получает все объявления переменных, все идентификаторы. При этом никакой код не выполняется, методы не вызываются. При втором проходе собственно происходит выполнение.
- _var_
```javascript
console.log(foo); //ReferenceError: foo is not defined
```
```javascript
console.log(foo); //undefined
var foo = "Tom";
```
```javascript
var c = a * b;
var a = 7;
var b = 3;
console.log(c); //NaN
```
Область видимости var заканчивается внутри функции:
```javascript
function hoist() {
  console.log(message);
  var message = 'Hoisting is all the rage!'
}
hoist(); //undefined
```
Вот как интерпретатор видит код выше:
```javascript
function hoist() {
  var message;
  console.log(message);
  message = 'Hoisting is all the rage!'
}
hoist(); // Вывод: undefined
```
- _let_
```javascript
console.log(hoist); //ReferenceError: hoist is not defined
let hoist = 'The variable has been hoisted.';
```
```javascript
let hoist;
console.log(hoist); //undefined
hoist = 'Hoisted'
```
Переменные объявленные как let заключены в область видимости блока, а не функции.
- _const_
```javascript
console.log(hoist); //ReferenceError: hoist is not defined
const hoist = 'The variable has been hoisted.';
```
```javascript
const PI;
console.log(PI); //SyntaxError: Missing initializer in const declaration
PI=3.142;
```
Переменные объявленные с let и const остаются неинициализированными в начале выполнения, в то время как переменные объявленные с var инициализируются со значением undefined.
- _function declaration_
```javascript
display(); //"Hello Hoisting"
 
function display(){
    console.log("Hello Hoisting"); 
}
```
- _function expression_
```javascript
display(); //TypeError: display is not a function.
 
var display = function (){
    console.log("Hello Hoisting"); 
}
```
- _class declaration_ (не всплывает)
```javascript
var Frodo = new Hobbit();
Frodo.height = 100;
Frodo.weight = 300;
console.log(Frodo); //ReferenceError: Hobbit is not defined
class Hobbit {
  constructor(height, weight) {
    this.height = height;
    this.weight = weight;
  }
}
```
- _class expression_ (не всплывает)
```javascript
var Square = new Polygon();
Square.height = 10;
Square.width = 10;
console.log(Square); //TypeError: Polygon is not a constructor
var Polygon = class Polygon {
constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
```

[read more ...](https://medium.com/@stasonmars/%D1%80%D0%B0%D0%B7%D0%B1%D0%B8%D1%80%D0%B0%D0%B5%D0%BC%D1%81%D1%8F-%D1%81-%D0%BF%D0%BE%D0%B4%D0%BD%D1%8F%D1%82%D0%B8%D0%B5%D0%BC-hoisting-%D0%B2-javascript-7d2d27bc51f1)
#### 3. Let vs var. Const
- _var_

Область видимости переменной, объявленной через var, это её текущий контекст выполнения. Который может ограничиваться функцией или быть глобальным, для переменных, объявленных за пределами функции.

Подробнее: https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/var

- _let_

Директива let позволяет объявить локальную переменную с областью видимости, ограниченной текущим блоком кода . В отличие от ключевого слова var, которое объявляет переменную глобально или локально во всей функции, независимо от области блока.

Подробнее: https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/let

- _const_

Значение констант не может быть изменено новым присваиванием, а также не может быть переопределено. Константы (const) подчиняются области видимости уровня блока, так же как переменные объявленные с использованием ключевого слова let.

Подробнее: https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/const

#### 4. Передача данных по ссылке и по значению. Примеры
- _Передача по значению_
```javascript
function change(x){
  x = 2 * x;
  console.log("x in change:", x);
}
 
let n = 10;
console.log("n before change:", n); // n before change: 10
change(n);                          // x in change: 20
console.log("n after change:", n);  // n after change: 10
```
Строки, числа, логические значения передаются в функцию по значению (передается их копия).
- _Передача по ссылке_
```javascript
function change(user){
  user.name = "Tom";
}
 
var bob ={ 
  name: "Bob"
};
console.log("before change:", bob.name);    // Bob
change(bob);
console.log("after change:", bob.name);     // Tom
```
Объекты и массивы передаются по ссылке. То есть функция получает сам объект или массив, а не их копию.
```javascript
function change(array){
  array[0] = 8;
}
function changeFull(array){
  array = [9, 8, 7];
}
 
var numbers = [1, 2, 3];
 
console.log("before change:", numbers);     // [1, 2, 3]
change(numbers);
console.log("after change:", numbers);      // [8, 2, 3]
changeFull(numbers);
console.log("after changeFull:", numbers);  // [8, 2, 3]
```
#### 5. {a: 10} == {a: 10}. Что вернет код?
```javascript
{a: 10} == {a: 10} //false
```
т.к. сравнивается не содержимое объектов, а их ссылки.
Дя того, чтобы сравнить 2 объекта, существует несколько способов, наиболее простой из которых:
```javascript
function deepEqual (obj1, obj2){
   return JSON.stringify(obj1)===JSON.stringify(obj2);
}
```
#### 6. Что такое this?
Для доступа к текущему объекту из метода используется ключевое слово this.
Значением this является объект перед «точкой», в контексте которого вызван метод, например:
```javascript
let user = {
  name: 'Василий',
  sayHi: function() {
    alert( this.name );
  }
};

user.sayHi(); // sayHi в контексте user
```
Здесь при выполнении функции user.sayHi() в this будет храниться ссылка на текущий объект user.
Вместо this внутри sayHi можно было бы обратиться к объекту, используя переменную user:
```javascript
  sayHi: function() {
    alert( user.name );
  }
```
…Однако, такое решение нестабильно. Если мы решим скопировать объект в другую переменную, например admin = user, а в переменную user записать что-то другое – обращение будет совсем не по адресу:
```javascript
let user = {
  name: 'Василий',
  sayHi: function() {
    alert( user.name ); // приведёт к ошибке
  }
};

let admin = user;
user = null;

admin.sayHi(); // упс! внутри sayHi обращение по старому имени, ошибка!
```
Использование this гарантирует, что функция работает именно с тем объектом, в контексте которого вызвана.
Через this метод может не только обратиться к любому свойству объекта, но и передать куда-то ссылку на сам объект целиком:
```javascript
let user = {
  name: 'Василий',
  sayHi: function() {
    showName(this); // передать текущий объект в showName
  }
};

function showName(namedObj) {
  alert( namedObj.name );
}
user.sayHi(); // Василий
```
Если одну и ту же функцию запускать в контексте разных объектов, она будет получать разный this:
```javascript
let user = { firstName: "Вася" };
let admin = { firstName: "Админ" };

function func() {
  alert( this.firstName );
}

user.f = func;
admin.g = func;

// this равен объекту перед точкой:
user.f(); // Вася
admin.g(); // Админ
admin['g'](); // Админ (не важно, доступ к объекту через точку или квадратные скобки)
```
Значение this, при вызове без контекста, получает значение глобального объекта window:

```javascript
 function func() {
  alert( this ); // выведет [object Window] или [object global]
}

func();
```
Таково поведение в старом стандарте.
А в режиме use strict вместо глобального объекта this будет undefined:
```javascript
 function func() {
  "use strict";
  alert( this ); // выведет undefined (кроме IE9-)
}

func();
```
Обычно если в функции используется this, то она, всё же, служит для вызова в контексте объекта, так что такая ситуация – скорее исключение.

Подробнее:
http://learn.javascript.ru/object-methods
https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/this
https://github.com/azat-io/you-dont-know-js-ru/tree/master/this%20%26%20object%20prototypes
#### 7. Apply, call, bind. Для чего используются? В чем отличия?
- _call_

Метод call() вызывает функцию с указанным значением this и индивидуально предоставленными аргументами. Вы можете присваивать различные объекты this при вызове существующей функции. this ссылается на текущий объект, вызвавший объект. С помощью call вы можете написать метод один раз, а затем наследовать его в других объектах, без необходимости переписывать метод для каждого нового объекта.

```javascript
function showFullName() {
  alert( this.firstName + " " + this.lastName );
}

const user = {
  firstName: "Василий",
  lastName: "Петров"
};

// функция вызовется с this=user
showFullName.call(user) // "Василий Петров"
```
- _apply_

Метод apply() вызывает функцию с указанным значением this и аргументами, предоставленными в виде массива (либо массивоподобного объекта). Вы можете присваивать различные объекты this при вызове существующей функции. this ссылается на текущий объект, вызывающий объект. С помощью apply() вы можете написать метод один раз, а затем наследовать его в других объектах без необходимости переписывать метод для каждого нового объекта.

```javascript
//эти две строчки сработают одинаково:
showFullName.call(user, 'firstName', 'surname');
showFullName.apply(user, ['firstName', 'surname']);
```
```javascript
var arr = [];
arr.push(1);
arr.push(5);
arr.push(2);

// получить максимум из элементов arr
alert( Math.max.apply(null, arr) ); // 5
```
Преимущество apply() перед call() отчётливо видно, когда мы формируем массив аргументов динамически.
- _bind_

Метод bind() создаёт новую функцию, которая при вызове устанавливает в качестве контекста выполнения this предоставленное значение. В метод также передаётся набор аргументов, которые будут установлены перед переданными в привязанную функцию аргументами при её вызове.

```javascript
// Пример потери контекста
var user = {
  firstName: "Вася",
  sayHi: function() {
    alert( this.firstName );
  }
};

setTimeout(user.sayHi, 1000); // undefined (не Вася!)
```
```javascript
// привязка контекста
var user = {
  firstName: "Вася",
  sayHi: function() {
    alert( this.firstName );
  }
};

setTimeout(user.sayHi.bind(user), 1000); // Вася
```
Вызов bind часто используют для привязки функции к контексту, чтобы затем присвоить её в обычную переменную и вызывать уже без явного указания объекта.
- фундаментальное различие между этими методами заключается в том, что функция call() принимает список аргументов, в то время, как функция apply() - одиночный массив аргументов. Методы call/apply вызывают функцию с заданным контекстом и аргументами. А bind не вызывает функцию. Он только возвращает «обёртку», которую мы можем вызвать позже, и которая передаст вызов в исходную функцию, с привязанным контекстом.

Подробнее:

https://learn.javascript.ru/call-apply

https://learn.javascript.ru/bind
#### 8. Замыкание. Приведите пример.
Замыкание — это комбинация функции и лексического окружения, в котором эта функция была определена.
```javascript
function makeFunc() {
  let name = "Mozilla";
  function displayName() {
    alert(name);
  }
  return displayName;
};

let myFunc = makeFunc();
myFunc(); //Mozilla
```
Подробнее:

https://developer.mozilla.org/ru/docs/Web/JavaScript/Closures

http://learn.javascript.ru/closures

https://github.com/azat-io/you-dont-know-js-ru/tree/master/scope%20%26%20closures
#### 9. Sum(1)(2)

1 способ

```javascript
function sum (a) {
  return function (b) {
    return a + b;
  }
};

sum(2)(3) //5

// раблотаеет только с 2 скобками
```

2 способ

```javascript
function sum(a) {

  var currentSum = a;

  function f(b) {
    currentSum += b;
    return f;
  }

  f.toString = function() {
    return currentSum;
  };

  return f;
}

sum(1)(2); // 3
sum(5)(-1)(2); // 6
```

Подробнее:

https://learn.javascript.ru/task/sum-many-brackets

#### 10. Prototype. Отличия proto от prototype. Пример наследования
Объекты в JavaScript можно организовать в цепочки так, чтобы свойство, не найденное в одном объекте, автоматически искалось бы в другом.
Связующим звеном выступает специальное свойство __proto__.
Если один объект имеет специальную ссылку __proto__ на другой объект, то при чтении свойства из него, если свойство отсутствует в самом объекте, оно ищется в объекте __proto__.
```javascript
var animal = {
  eats: true
};
var rabbit = {
  jumps: true
};

rabbit.__proto__ = animal;

// в rabbit можно найти оба свойства
alert( rabbit.jumps ); // true
alert( rabbit.eats ); // true
```
Объект, на который указывает ссылка __proto__, называется «прототипом». В данном случае получилось, что animal является прототипом для rabbit.
У объекта, который является __proto__, может быть свой __proto__, у того – свой, и так далее. При этом свойства будут искаться по цепочке.
__proto__ не работает в IE10.
К счастью, в JavaScript с древнейших времён существует альтернативный, встроенный в язык и полностью кросс-браузерный способ.
Чтобы новым объектам автоматически ставить прототип, конструктору ставится свойство prototype.
При создании объекта через new, в его прототип __proto__ записывается ссылка из prototype функции-конструктора.

Например, код ниже полностью аналогичен предыдущему, но работает всегда и везде:
```javascript
let animal = {
  eats: true
};

function Rabbit(name) {
  this.name = name;
}

Rabbit.prototype = animal;

let rabbit = new Rabbit("Кроль"); //  rabbit.__proto__ == animal

alert( rabbit.eats ); // true
```
Установка Rabbit.prototype = animal буквально говорит интерпретатору следующее: "При создании объекта через new Rabbit запиши ему __proto__ = animal".
Свойство prototype имеет смысл только у конструктора
Свойство с именем prototype можно указать на любом объекте, но особый смысл оно имеет, лишь если назначено функции-конструктору.
Само по себе, без вызова оператора new, оно вообще ничего не делает, его единственное назначение – указывать __proto__ для новых объектов.

Пример наследования:
```javascript
// 1. Конструктор Animal
function Animal(name) {
  this.name = name;
  this.speed = 0;
}

// 1.1. Методы -- в прототип

Animal.prototype.stop = function() {
  this.speed = 0;
  alert( this.name + ' стоит' );
}

Animal.prototype.run = function(speed) {
  this.speed += speed;
  alert( this.name + ' бежит, скорость ' + this.speed );
};

// 2. Конструктор Rabbit
function Rabbit(name) {
  this.name = name;
  this.speed = 0;1
}

// 2.1. Наследование
Rabbit.prototype = Object.create(Animal.prototype);
Rabbit.prototype.constructor = Rabbit;

// 2.2. Методы Rabbit
Rabbit.prototype.jump = function() {
  this.speed++;
  alert( this.name + ' прыгает, скорость ' + this.speed );
}
```

Подробнее:

http://learn.javascript.ru/class-inheritance

http://learn.javascript.ru/prototype

http://learn.javascript.ru/new-prototype
#### 11. Как создать объект без прототипа?

```javascript
const data = Object.create(null);
data.text = "Привет";

alert(data.text); // Привет
alert(data.toString); // undefined
```

Объект, создаваемый при помощи Object.create(null) не имеет прототипа, а значит в нём нет лишних свойств. 

Подробнее: 

https://learn.javascript.ru/prototype#object-create-null

#### 12. Методы массива, перебирающие элементы массива
- _forEach_
Метод «Array.prototype.forEach(callback[, thisArg])» используется для перебора массива.
Он для каждого элемента массива вызывает функцию callback.
Этой функции он передаёт три параметра callback(item, i, arr):

item – очередной элемент массива.

i – его номер.

arr – массив, который перебирается.

Например:
```javascript
let arr = ["Яблоко", "Апельсин", "Груша"];

arr.forEach(function(item, i, arr) {
  alert( i + ": " + item + " (массив:" + arr + ")" );
});
```
Второй, необязательный аргумент forEach позволяет указать контекст this для callback.
Метод forEach ничего не возвращает, его используют только для перебора, как более «элегантный» вариант, чем обычный цикл for.

- _filter_
Метод «Array.prototype.filter(callback[, thisArg])» используется для фильтрации массива через функцию.
Он создаёт новый массив, в который войдут только те элементы arr, для которых вызов callback(item, i, arr) возвратит true.

Например:
```javascript
let arr = [1, -1, 2, -2, 3];

let positiveArr = arr.filter(function(number) {
  return number > 0;
});

alert( positiveArr ); // 1,2,3
```

- _map_
Метод «Array.prototype.map(callback[, thisArg])» используется для трансформации массива.
Он создаёт новый массив, который будет состоять из результатов вызова callback(item, i, arr) для каждого элемента arr.

Например:
```javascript
let names = ['HTML', 'CSS', 'JavaScript'];

let nameLengths = names.map(function(name) {
  return name.length;
});

// получили массив с длинами
alert( nameLengths ); // 4,3,10
```

- _every/some_

Эти методы используются для проверки массива.

Метод «Array.prototype.every(callback[, thisArg])» возвращает true, если вызов callback вернёт true для каждого элемента arr.
Метод «Array.prototype.some(callback[, thisArg])» возвращает true, если вызов callback вернёт true для какого-нибудь элемента arr.
```javascript
let arr = [1, -1, 2, -2, 3];

function isPositive(number) {
  return number > 0;
}

alert( arr.every(isPositive) ); // false, не все положительные
alert( arr.some(isPositive) ); // true, есть хоть одно положительное
```

- _reduce/reduceRight_

Метод «Array.prototype.reduce(callback[, initialValue])» используется для последовательной обработки каждого элемента массива с сохранением промежуточного результата.
Метод reduce используется для вычисления на основе массива какого-либо единого значения, иначе говорят «для свёртки массива». Чуть далее мы разберём пример для вычисления суммы.
Он применяет функцию callback по очереди к каждому элементу массива слева направо, сохраняя при этом промежуточный результат.

Аргументы функции callback(previousValue, currentItem, index, arr):

previousValue – последний результат вызова функции, он же «промежуточный результат».
currentItem – текущий элемент массива, элементы перебираются по очереди слева-направо.

index – номер текущего элемента.

arr – обрабатываемый массив.

Кроме callback, методу можно передать «начальное значение» – аргумент initialValue. Если он есть, то на первом вызове значение previousValue будет равно initialValue, а если у reduce нет второго аргумента, то оно равно первому элементу массива, а перебор начинается со второго.

Пример:

```javascript
let arr = [1, 2, 3, 4, 5]

// для каждого элемента массива запустить функцию,
// промежуточный результат передавать первым аргументом далее
let result = arr.reduce(function(sum, current) {
  return sum + current;
}, 0);

alert( result ); // 15
```
При первом запуске sum – исходное значение, с которого начинаются вычисления, равно нулю (второй аргумент reduce).
Сначала анонимная функция вызывается с этим начальным значением и первым элементом массива, результат запоминается и передаётся в следующий вызов, уже со вторым аргументом массива, затем новое значение участвует в вычислениях с третьим аргументом и так далее.

Подробнее: 

https://learn.javascript.ru/array-iteration

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/filter

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/map

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/every

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/some

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce
#### 13. “hello world”.repeating(3) -> hello world hello world hello world. Как реализовать?

1 способ

```javascript
// cheat =)
String.prototype.repeating = String.prototype.repeat;
'hello world'.repeating(3);
```

2 способ

```javascript
String.prototype.repeating = function (count) {
  var str = '' + this;
  count = +count;
  var rpt = '';
  for (var i = 0; i < count; i++) {
    rpt = rpt + ' ' + str;
  }
  return rpt;
}
```
#### 14. Браузерные события элементов. Отмена дефолтных событий браузера
Событие – это сигнал от браузера о том, что что-то произошло.
Список самых часто используемых событий:

##### События мыши:
* click – происходит, когда кликнули на элемент левой кнопкой мыши
* contextmenu – происходит, когда кликнули на элемент правой кнопкой мыши
* mouseover – возникает, когда на элемент наводится мышь
* mousedown и mouseup – когда кнопку мыши нажали или отжали
* mousemove – при движении мыши

##### События на элементах управления:
* submit – посетитель отправил форму <form>
* focus – посетитель фокусируется на элементе, например нажимает на <input>

##### Клавиатурные события:
* keydown – когда посетитель нажимает клавишу
* keyup – когда посетитель отпускает клавишу

##### События документа:
* DOMContentLoaded – когда HTML загружен и обработан, DOM документа полностью построен и доступен.

##### События CSS:
* transitionend – когда CSS-анимация завершена.

Назначение обработчиков событий:
Использование атрибута HTML
```html
<input value="Нажми меня" onclick="alert('Клик!')" type="button">
```
Использование свойства DOM-объекта
```html
<input id="elem" type="button" value="Нажми меня" />
<script>
  elem.onclick = function() {
    alert( 'Спасибо' );
  };
</script>
```

##### addEventListener и removeEventListener
Методы addEventListener и removeEventListener являются современным способом назначить или удалить обработчик, и при этом позволяют использовать сколько угодно любых обработчиков.
Назначение обработчика осуществляется вызовом addEventListener с тремя аргументами:

element.addEventListener(event, handler[, phase]);

event - Имя события, например click

handler - Ссылка на функцию, которую надо поставить обработчиком.

phase - Необязательный аргумент, «фаза», на которой обработчик должен сработать.

Удаление обработчика осуществляется вызовом removeEventListener:
```javascript
// передать те же аргументы, что были у addEventListener
element.removeEventListener(event, handler[, phase]);
```

Удаление требует именно ту же функцию
Многие события автоматически влекут за собой действие браузера.
Например:

- Клик по ссылке инициирует переход на новый URL.
- Нажатие на кнопку «отправить» в форме – отсылку ее на сервер.
- Двойной клик на тексте – инициирует его выделение.

Есть два способа отменить действие браузера:

* Основной способ – это воспользоваться объектом события. Для отмены действия браузера существует стандартный метод event.preventDefault().

* Если же обработчик назначен через onсобытие (не через addEventListener), то можно просто вернуть false из обработчика.

Подробнее: 

https://learn.javascript.ru/introduction-browser-events#addeventlistener-i-removeeventlistener

https://learn.javascript.ru/default-browser-action
#### 15. Всплытие и перехват событий

Основной принцип всплытия:

При наступлении события обработчики сначала срабатывают на самом вложенном элементе, затем на его родителе, затем выше и так далее, вверх по цепочке вложенности.

![](https://learn.javascript.ru/article/event-bubbling/event-order-bubbling.png)

Самый глубокий элемент, который вызывает событие, называется «целевым» или «исходным» элементом и доступен как `event.target`.

Для остановки всплытия нужно вызвать метод `event.stopPropagation()`.

`stopPropagation` препятствует продвижению события дальше, но на текущем элементе все обработчики отработают.

Для того, чтобы не только предотвратить всплытие, но и останавить обработку событий на текущем элементе используется метод `event.stopImmediatePropagation()`

В современном стандарте, кроме "всплытия" событий, предусмотрено ещё и "погружение" (или "захват").

![](https://mdn.mozillademos.org/files/14075/bubbling-capturing.png)

Откройте данный пример: 

[исходный код](https://github.com/mdn/learning-area/blob/master/javascript/building-blocks/events/show-video-box.html)

[пример](http://mdn.github.io/learning-area/javascript/building-blocks/events/show-video-box.html)

```javascript
video.onclick = function(e) {
  e.stopPropagation();
  video.play();
};
```
Подробнее:

[developer.mozilla.org](https://developer.mozilla.org/ru/docs/Learn/JavaScript/Building_blocks/%D0%A1%D0%BE%D0%B1%D1%8B%D1%82%D0%B8%D1%8F#%D0%92%D1%81%D0%BF%D0%BB%D1%8B%D1%82%D0%B8%D0%B5_%D0%B8_%D0%BF%D0%B5%D1%80%D0%B5%D1%85%D0%B2%D0%B0%D1%82_%D1%81%D0%BE%D0%B1%D1%8B%D1%82%D0%B8%D0%B9)

https://learn.javascript.ru/event-bubbling

#### 16. Делегирование. Пример
Всплытие событий позволяет реализовать один из самых важных приёмов разработки – делегирование.

Он заключается в том, что если у нас есть много элементов, события на которых нужно обрабатывать похожим образом, то вместо того, чтобы назначать обработчик каждому – мы ставим один обработчик на их общего предка.
Из него можно получить целевой элемент event.target, понять на каком именно потомке произошло событие и обработать его.
```javascript
<div id="menu">
  <button data-action="save">Сохранить</button>
  <button data-action="load">Загрузить</button>
  <button data-action="search">Поиск</button>
</div>

<script>
  function Menu(elem) {
    this.save = function() {
      alert( 'сохраняю' );
    };
    this.load = function() {
      alert( 'загружаю' );
    };
    this.search = function() {
      alert( 'ищу' );
    };

    let self = this;

    elem.onclick = function(e) {
      let target = e.target;
      let action = target.getAttribute('data-action');
      if (action) {
        self[action]();
      }
    };
  }

  new Menu(menu);
</script>
```

Подробнее:

https://learn.javascript.ru/event-delegation
#### 17. Напишите функцию F, так чтобы new F === F
```javascript
function F() { return F; }
```

В данном случае чтобы обеспечить равенство, мы явно задаем `return`, поэтому объект не создается, а `new` отрабатывает просто как функция.

_О `this` and `return`:_

Как правило, конструкторы ничего не возвращают. Их задача – записать всё, что нужно, в `this`, который автоматически станет результатом.

Но если явный вызов return всё же есть, то применяется простое правило:

- При вызове `return` с объектом, будет возвращён он, а не `this`.
- При вызове `return` с примитивным значением, оно будет отброшено.

Иными словами, вызов `return` с объектом вернёт объект, а с чем угодно, кроме объекта – возвратит, как обычно, `this`.

```javascript
function Animal(name) {
  // this = {}; это делает интерпритатор

  // в this пишем свойства, методы
  this.name = name;
  this.canWalk = true;

  // return this; это делает интерпритатор
}
```
Подробнее:

https://learn.javascript.ru/constructor-new
#### 18. Function.prototype.bind polyfill
```javascript
if (!Function.prototype.bind) {
  Function.prototype.bind = function (context /* ...args */) {
    var fn = this;
    var args = Array.prototype.slice.call(arguments, 1);

    if (typeof(fn) !== 'function') {
      throw new TypeError('Function.prototype.bind - context must be a valid function');
    }

    return function () {
      return fn.apply(context, args.concat(Array.prototype.slice.call(arguments)));
    };
  };
}
```

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/bind
#### 19. Object.create polyfill

See here: [developer.mozilla.org](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/create#Polyfill)

#### 20. Event loop
https://developer.mozilla.org/ru/docs/Web/JavaScript/EventLoop
#### 21. Promises

Для того чтобы поиграться с запросами, можно использовать открытый API http://jsonplaceholder.typicode.com/

Объект Promise (обещание) используется для отложенных и асинхронных вычислений. Promise может находиться в трёх состояниях:

- ожидание (pending): начальное состояние, не выполнено и не отклонено.
- выполнено (fulfilled): операция завершена успешно.
- отклонено (rejected): операция завершена с ошибкой.

```javascript
new Promise(executor);
new Promise(function(resolve, reject) { ... });
```

https://learn.javascript.ru/promise
https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Promise

## Additional Questions
#### 22. Денормализация в ES6

http://learn.javascript.ru/destructuring

#### 23. Spread оператор (...)

### 24. cookies, localStorage, sessionStorage
Куки – это небольшие строки данных, которые хранятся непосредственно в браузере.
Значение document.cookie состоит из пар ключ=значение, разделённых ;. Каждая пара представляет собой отдельное куки.
Мы можем писать в document.cookie. Но это не просто свойство данных, а акcессор (геттер/сеттер). Присваивание к нему обрабатывается особым образом.
Запись в document.cookie обновит только упомянутые в ней куки, но при этом не затронет все остальные.

У куки есть ряд настроек, многие из которых важны и должны быть установлены.
Эти настройки указываются после пары ключ=значение и отделены друг от друга разделителем ;, вот так:
```javascript
document.cookie = "user=John; path=/; expires=Tue, 19 Jan 2038 03:14:07 GMT"
```
Настройки path, domain, expires, max-age, secure, samesite

sessionStorage, localStorage
* В отличие от куки, объекты веб-хранилища не отправляются на сервер при каждом запросе. Именно поэтому мы можем хранить гораздо больше данных. Большинство современных браузеров могут выделить как минимум 5 мегабайтов данных (или больше), и этот размер можно поменять в настройках.
* Ещё одно отличие от куки – сервер не может манипулировать объектами хранилища через HTTP-заголовки. Всё делается при помощи JavaScript.
* Хранилище привязано к источнику (домен/протокол/порт). Это значит, что разные протоколы или поддомены определяют разные объекты хранилища, и они не могут получить доступ к данным друг друга.

Объекты хранилища localStorage и sessionStorage предоставляют одинаковые методы и свойства:
* setItem(key, value) – сохранить пару ключ/значение.
* getItem(key) – получить данные по ключу key.
* removeItem(key) – удалить данные с ключом key.
* clear() – удалить всё.
* key(index) – получить ключ на заданной позиции.
* length – количество элементов в хранилище.

Когда обновляются данные в localStorage или sessionStorage, генерируется событие storage со следующими свойствами:
* key – ключ, который обновился (null, если вызван .clear()).
* oldValue – старое значение (null, если ключ добавлен впервые).
* newValue – новое значение (null, если ключ был удалён).
* url – url документа, где произошло обновление.
* storageArea – объект localStorage или sessionStorage, где произошло обновление. 
Важно: событие срабатывает на всех остальных объектах window, где доступно хранилище, кроме того окна, которое его вызвало.

localStorage	
* Совместно используется между всеми вкладками и окнами с одинаковым источником	
* «Переживает» перезапуск браузера	

sessionStorage
* Разделяется в рамках вкладки браузера, среди ифреймов из того же источника
* «Переживает» перезагрузку страницы (но не закрытие вкладки)