# Javascript Scoping

<ul>
  <li><a href="javascript" title="Global Scope">Global Scope</a></li>
  <li><a href="javascript" title="Local Scope">Local Scope</a></li>
  <li><a href="javascript" title="Block Scope">Block Scope</a></li>
  <li><a href="javascript" title="Lexical Scope">Lexical Scope</a></li>
  <li><a href="javascript" title="Closures">Closures</a></li>
  <li><a href="javascript" title="Public and Private Scope">Public and Private Scope</a></li>
</ul>

#### Global Scope

```javascript
var name = 'Suryansh';

console.log(name); // logs 'Suryansh'

function logName() {
    console.log(name); // 'name' is accessible here and everywhere else
}

logName(); // logs 'Suryansh'
```

#### Local Scope

```javascript
// Global Scope
function someFunction() {
    // Local Scope #1
    function someOtherFunction() {
        // Local Scope #2
    }
}

// Global Scope
function anotherFunction() {
    // Local Scope #3
}
// Global Scope
```

#### Block Statements

```javascript
if (true) {
    // this 'if' conditional block doesn't create a scope

    // name is in the global scope because of the 'var' keyword
    var name = 'Suryansh';
    // likes is in the local scope because of the 'let' keyword
    let likes = 'Coding';
    // skills is in the local scope because of the 'const' keyword
    const skills = 'JavaScript and PHP';
}

console.log(name); // logs 'Suryansh'
console.log(likes); // Uncaught ReferenceError: likes is not defined
console.log(skills); // Uncaught ReferenceError: skills is not defined
```

#### Lexical Scope
Lexical Scope means that in a nested group of functions, the inner functions have access to the variables and other resources of their parent scope. This means that the child functions are lexically bound to the execution context of their parents. Lexical scope is sometimes also referred to as Static Scope.

```javascript
function grandfather() {
    var name = 'Suryansh';
    // likes is not accessible here
    function parent() {
        // name is accessible here
        // likes is not accessible here
        function child() {
            // Innermost level of the scope chain
            // name is also accessible here
            var likes = 'Coding';
        }
    }
}
```

#### Closures
// Example 1
A closure can not only access the variables defined in its outer function but also the arguments of the outer function.
```javascript
function greet() {
    name = 'Suryansh';
    return function () {
        console.log('Hi ' + name);
    }
}

greet(); // nothing happens, no errors

// the returned function from greet() gets saved in greetLetter
greetLetter = greet();

 // calling greetLetter calls the returned function from the greet() function
greetLetter(); // logs 'Hi Suryansh'


// Example 2
function greet() {
    name = 'Suryansh';
    return function () {
        console.log('Hi ' + name);
    }
}

greet()(); // logs 'Hi Suryansh'

More about <a href="https://github.com/suryansh54/javascript-closure">Closures</a>
```

#### Public and Private Scope

##### PHP
```php
// Public Scope
public $property;
public function method() {
  // ...
}

// Private Sccpe
private $property;
private function method() {
  // ...
}

// Protected Scope
protected $property;
protected function method() {
  // ...
}
```

##### javascript

```javascript
(function () {
  // private scope
})();
```
