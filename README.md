QPack JavaScript
================

Library for encoding and decoding QPack data using pure JavaScript.

Usage example:
```javascript
var iris = {
  name: 'Iris',
  age: 3
};

// Encode iris to a binary string.
// The second argument is true which tells the function to return a string.
// When false or undefined an Uint8Array is returned.
var qp = qpack.encode(iris, true);

// Decode qp binary string to JavaScript object.
var data = qpack.decode(qp);

console.log(data);  // {name: 'Iris', age: 3}
```

Float problem
-------------

JavaScript has no integer type and therefore the values 1.0 and 1 are equal. QPack therefore cannot known if such value should be packed as integer of as float. By default a value like 1.0 will be packed as integer 1. If you have a use case where you really want to pack a value as float it can be wrapped with the function `qpack.double(f)`.

For example:
```javascript
// This will pack 1.0 as a double (float) value.
var qp = qpack.encode(qpack.double(1.0), true);
```
