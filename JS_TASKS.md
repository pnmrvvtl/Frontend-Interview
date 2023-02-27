### 1. Polyfill Function.prototype.bind

```javascript
Function.prototype.myBind = function (obj, ...args) {
  let func = this;
  return function (...newArgs) {
    func.apply(obj, [...args, ...newArgs]);
  };
};


Function.prototype.myBind = function (obj, ...args) {
  return (...newArgs) => {
    this.apply(obj, [...args, ...newArgs]);
  };
};
```

### 2. Polyfill Object.create

```javascript
Object.myCreate = function (proto, properties) {
  function MyClass() {}
  MyClass.prototype = proto;
  let obj = new MyClass();
  if (properties) {
    Object.defineProperties(obj, properties);
  }
  return obj;
};
```

### 3. Array.flat polyfill

```javascript
Array.prototype.myFlat = function (deep = 1) {
  let result = [];
  for (let i = 0; i < this.length; i++) {
    if (Array.isArray(this[i]) && deep > 0) {
      result = [...result, ...this[i].myFlat(deep - 1)];
    } else {
      result = [...result, this[i]];
    }
  }
  return result;
};
```

### 4. Array.reduce

```javascript
Array.prototype.myReduce = function (reducer, initial) {
  let result = initial;
  for (let i = 0; i < this.length; i++) {
    result = reducer(result, this[i], i, this);
  }
  return result;
};
```

### 5. 'hello world'.repeating(3) -> 'hello world hello world hello world'.

```javascript
String.prototype.repeating = function (counter) {
  let result = [];
  for (let i = 0; i < counter; i++) {
    result = [...result, this];
  }
  return result.join(" ");
};
```

### 6. myFunc('!', 4, -10, 34, 0) -> '4!-10!34!0`. How to implement?

```javascript
function myFunc (spliter, ...args){
  return args.join(spliter);
} 
```

### 7. five(plus(seven(minus(three())))) -> 9. How to implement?

```javascript
function three(arg){
	if (typeof arg === 'function') {
		return arg(3);
	} else {
		return 3;
	}
}

function seven(arg) {
	if (typeof arg === 'function') {
		return arg(7);
	} else {
		return 7;
	}
}

function five(arg) {
    if (typeof arg === 'function') {
        return arg(5);
    } else {
        return 5;
    }
}

function plus(arg) {
	return function (a) {
		return a + arg;
	}
}

function minus(arg) {
    return function (a) {
        return a - arg;
    }
}
```

### 8. add(5)(9)(-4)(1) -> 11. How to implement?

```javascript
function add(a) {
  return (b) => {
    return (c) => {
      return (d) => {
        return a + b + c + d;
      };
    };
  };
}
```

### 9. periodOutput(period) method should output in the console once per every period how mach time has passed since the first function call. Example: periodOutput(100) -> 100(after 100 ms), 200(after 100 ms), 300(after 100 ms), ...

```javascript
function periodOutput(time) {
  let counter = time;
  setInterval(() => {
    console.log(`${counter}(after ${time} ms),`);
    counter += time;
  }, time);
}

periodOutput(100);
```


### 10. extendedPeriodOutput(period) method should output in the console once per period how mach time has passed since the first function call and then increase the period. Example: // extendedPeriodOutput(100) -> 100(after 100 ms), 200(after 200 ms), 300(after 300 ms)

```javascript
function periodOutput(time) {
  function inInterval(inTime) {
    let start = inTime;
    interval = setInterval(() => {
      console.log(`${start} after (${start})`);
      start += time;
      clearInterval(interval);
      inInterval(start);
    }, start);
  }
  inInterval(time);
}
```



