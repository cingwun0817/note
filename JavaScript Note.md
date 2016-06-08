# JavaScript Note

[MDN] (https://developer.mozilla.org/en-US/docs/Web/JavaScript)

## Object

```javascript
var car = function(o) {
  var self = o
  
  var init = function() {
    return self
  }
  
  self.a = function() {
    console.log('hello')
  }
  
  return init()
}({item1: '#aaa', item2: '#bbb'})
```

## Prototype

```javascript
var car = function() {}
car.prototype = {
	a: function() {

	},
	b: function() {
		
	},
	c: function() {
	}
}
```

## Variable

* var 
* const
* let

### Default

```javascript
a = a || "AAA";
b = b || "BBB";
c = c || "CCC";
```
