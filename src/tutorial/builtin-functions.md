# Built-in Functions

Blade comes with an array of optimized built-in functions for simple tasks. Below is a list of the 
built-in functions followed by their respective documentations.

## Reference

- [Built-in Functions](#built-in-functions)
  - [Reference](#reference)
      - [abs(_x_: number | instance)](#absx-number--instance)
      - [bin(_x_: number | instance)](#binx-number--instance)
      - [bytes(_x_: number | list)](#bytesx-number--list)
      - [chr(_x_: number)](#chrx-number)
      - [delprop(_object_: instance, _name_: string)](#delpropobject-instance-name-string)
      - [file(_path_: string \[, _mode_: string\])](#filepath-string--mode-string)
      - [getprop(_object_: instance, _name_: string)](#getpropobject-instance-name-string)
      - [hasprop(_object_: instance, _name_: string)](#haspropobject-instance-name-string)
      - [hex(_x_: number | instance)](#hexx-number--instance)
      - [id(_x_: any)](#idx-any)
      - [instance\_of(_x_: any, _y_: class)](#instance_ofx-any-y-class)
      - [int(\[_x_: number | instance\])](#intx-number--instance)
      - [is\_bool(_x_: any)](#is_boolx-any)
      - [is\_callable(_x_: any)](#is_callablex-any)
      - [is\_class(_x_: any)](#is_classx-any)
      - [is\_dict(_x_: any)](#is_dictx-any)
      - [is\_function(_x_: any)](#is_functionx-any)
      - [is\_instance(_x_: any)](#is_instancex-any)
      - [is\_int(_x_: any)](#is_intx-any)
      - [is\_list(_x_: any)](#is_listx-any)
      - [is\_number(_x_: any)](#is_numberx-any)
      - [is\_object(_x_: any)](#is_objectx-any)
      - [is\_string(_x_: any)](#is_stringx-any)
      - [is\_bytes(_x_: any)](#is_bytesx-any)
      - [is\_file(_x_: any)](#is_filex-any)
      - [is\_iterable(_x_: any)](#is_iterablex-any)
      - [max(_numbers_...)](#maxnumbers)
      - [microtime()](#microtime)
      - [min(_numbers_...)](#minnumbers)
      - [oct(_x_: number)](#octx-number)
      - [ord(_x_: char)](#ordx-char)
      - [print(_values_...)](#printvalues)
      - [rand(\[_x_: number \[, _y_: number\]\])](#randx-number--y-number)
      - [setprop(_object_: instance, _name_: string, _value_: any)](#setpropobject-instance-name-string-value-any)
      - [sum(_numbers_...)](#sumnumbers)
      - [time()](#time)
      - [to\_bool(_x_: any)](#to_boolx-any)
      - [to\_dict(_x_: any)](#to_dictx-any)
      - [to\_int(_x_: number | instance)](#to_intx-number--instance)
      - [to\_list(_x_: any)](#to_listx-any)
      - [to\_number(_x_: any)](#to_numberx-any)
      - [to\_string(_x_: any)](#to_stringx-any)
      - [typeof(_x_: any)](#typeofx-any)


#### abs(_x_: number | instance)

If _x_ is a number, this function returns the absolute value of the number _x_. 
This is equivalent to `x >= 0 ? x : -x`. However, if _x_ is an instance of a class 
_y_ and _y_ defines `@abs()`, then this functions returns `x.@abs()`. 

#### bin(_x_: number | instance)

If _x_ is a number, this function converts number _x_ to it's binary string and 
returns the value. However, if _x_ is an instance of a class _y_ and _y_ defines `@bin()`, 
then this functions returns `x.@bin()`. 

#### bytes(_x_: number | list)

If _x_ is a number, this function returns a new `bytes` object with length _x_ having all 
its bytes set to `0x0`. 

If _x_ is a list, it returns a new `bytes` object whose contents are the bytes specified in the list.

> **_@note:_** If _x_ is a list, then the list must only contain valid bytes which can be any 
> number between 0 and 255.

#### chr(_x_: number)

Returns the Unicode character whose code point is equal to the number _x_.

#### delprop(_object_: instance, _name_: string)

Deletes the property _name_ from the given instance of _object_.

#### file(_path_: string [, _mode_: string])

Returns an open file handle to the file specified in the path in the specified mode. If the mode is not specified, 
  the file will be opened in the _read only_ mode.

#### getprop(_object_: instance, _name_: string)

Returns the value of the property _name_ from the given instance of _object_. If the _object_ 
  has no such property, `nil` is returned.

#### hasprop(_object_: instance, _name_: string)

Returns `true` if the _object_ has a property _name_. Returns `false` otherwise.

#### hex(_x_: number | instance)

If _x_ is a number, this function converts number _x_ to its hexadecimal string and returns the 
  value. However, if _x_ is an instance of a class _y_ and _y_ defines `@hex()`, then this 
  functions returns `x.@hex()`. 

#### id(_x_: any)

Returns the unique identifier of value _x_ within the system. This value is also equivalent to the current 
  address of object _x_ in memory.

#### instance_of(_x_: any, _y_: class)

Returns `true` if _x_ is an instance of the given class _y_ or `false` otherwise.

#### int([_x_: number | instance])

If _x_ is not given, returns `0`. If _x_ is a number, converts the number to an integer and 
  returns the integer. However, if _x_ is an instance of a class _y_ and _y_ defines `@int()`, 
  then this functions returns `x.@int()`.

#### is_bool(_x_: any)

Returns `true` if _x_ is a boolean or `false` otherwise.

#### is_callable(_x_: any)

Returns `true` if _x_ is a callable or `false` otherwise. Callables includes classes, functions 
  and closures.

#### is_class(_x_: any)

Returns `true` if _x_ is a class or `false` otherwise.

#### is_dict(_x_: any)

Returns `true` if _x_ is a dictionary or `false` otherwise.

#### is_function(_x_: any)

Returns `true` if _x_ is a function or closure or `false` otherwise.

#### is_instance(_x_: any)

Returns `true` if _x_ is an instance of any class or `false` otherwise.

#### is_int(_x_: any)

Returns `true` if _x_ is an integer or `false` otherwise.

#### is_list(_x_: any)

Returns `true` if _x_ is a list or `false` otherwise.

#### is_number(_x_: any)

Returns `true` if _x_ is a number or `false` otherwise.

#### is_object(_x_: any)

Returns `true` if _x_ is an object or `false` otherwise.

#### is_string(_x_: any)

Returns `true` if _x_ is a string or `false` otherwise.

#### is_bytes(_x_: any)

Returns `true` if _x_ is a bytes object or `false` otherwise.

#### is_file(_x_: any)

Returns `true` if _x_ is a file object or `false` otherwise.

#### is_iterable(_x_: any)

Returns `true` if _x_ is an iterable object or `false` otherwise. Iterables includes lists, 
  dictionaries, strings, bytes, and instances of any class that defines both `@iter()` and 
  `@itern()` decorator functions.

#### max(_numbers_...)

Returns the greatest of the given numbers. _This method requires at least two numbers._

#### microtime()

Returns the current epoch time to the microseconds resolution.

#### min(_numbers_...)

Returns the least of the given numbers. _This method requires at least two numbers._


#### oct(_x_: number)

If _x_ is a number, this function converts number _x_ to it's octal string and returns the 
  value. However, if _x_ is an instance of a class _y_ and _y_ defines `@oct()`, then this 
  functions returns `x.@oct()`. 


#### ord(_x_: char)

Returns the code point value of a unicode character _x_.

#### print(_values_...)

Prints the given values joined by spaces to standard output.

#### rand([_x_: number [, _y_: number]])

If no argument is given, returns a random number between 0 and 1. If _x_ is given, returns a 
  random number between 0 and _x_. If _y_ is given, returns a random number between _x_ and _y_.

#### setprop(_object_: instance, _name_: string, _value_: any)

Sets the value of the _object_'s property with the matching _name_ to the given _value_. If the property already 
  exists, it overwrites it and returns `true`, otherwise it returns `false`.

#### sum(_numbers_...)

Returns the sum of all the given numbers. _This method expects at least two arguments._

#### time()

Returns the current epoch time in seconds.

#### to_bool(_x_: any)

Converts the given value into a boolean. If _x_ is an instance of class _y_ and _y_ defines 
  `@bool()` decorator, returns `x.@bool()`.

#### to_dict(_x_: any)

Converts the given value into a dictionary. If _x_ is an instance of class _y_ and _y_ defines 
  `@dict())` decorator, returns `x.@dict()`.

#### to_int(_x_: number | instance)

If _x_ is a number, converts the given value into an integer and returns the integer. If _x_ is 
  an instance of a class and the class defines `@int()` decorator, returns `x.@int()`.

#### to_list(_x_: any)

Converts the given value into a list. If _x_ is an instance of class _y_ and _y_ defines 
  `@list()` decorator, returns `x.@list()`.

#### to_number(_x_: any)

Converts the given value into a number. If _x_ is an instance of class _y_ and _y_ defines 
  `@number()` decorator, returns `x.@number()`.

#### to_string(_x_: any)

Converts the given value into a string. If _x_ is an instance of class _y_ and _y_ defines 
  `@string()` decorator, returns `x.@string()`.

#### typeof(_x_: any)

Returns the name of the type of _x_ as a string.




<br><br>

[Previous Topic](./functions) | [Next Topic](./class)