# Working with Binary data

Working with binary data in Blade is a simple as working with _lists_ and this can be 
done using `bytes`. A `bytes` (meaning Byte stream) is an iterable in-memory contiguous 
list of numbers. Blade allows easily creating _bytes_ from strings and vice-versa and 
they are the primary medium of reading and writing binary data into and from the OS.

## Reference

- [Working with Binary data](#working-with-binary-data)
  - [Reference](#reference)
  - [Creating a Byte stream](#creating-a-byte-stream)
  - [Byte stream indexing](#byte-stream-indexing)
  - [`bytes()` methods](#bytes-methods)
      - [bytes(value: _number_ | _list_)](#bytesvalue-number--list)
      - [length()](#length)
      - [append(item: _any_)](#appenditem-any)
      - [clone()](#clone)
      - [extend(item: _bytes2_)](#extenditem-bytes2)
      - [index\_of(byte: _number_ \[, start\_index: _number_\])](#index_ofbyte-number--start_index-number)
      - [pop()](#pop)
      - [remove(index: _number_)](#removeindex-number)
      - [reverse()](#reverse)
      - [first()](#first)
      - [last()](#last)
      - [get(index: _number_)](#getindex-number)
      - [split(delimiter: _bytes_)](#splitdelimiter-bytes)
      - [is\_alpha()](#is_alpha)
      - [is\_alnum()](#is_alnum)
      - [is\_number()](#is_number)
      - [is\_lower()](#is_lower)
      - [is\_upper()](#is_upper)
      - [is\_space()](#is_space)
      - [dispose()](#dispose)
      - [to\_list()](#to_list)
      - [to\_string()](#to_string)



## Creating a Byte stream

The built-in `bytes()` function can be used to create a byte stream. For example,

```blade-repl
%> bytes(5)
(0 0 0 0 0)
```

The above code creates a byte stream containing five bytes all initialized to zero (0).
You can also create byte stream from a list of numbers as well. For example,

```blade-repl
%> bytes([72, 69, 76, 76, 79])
(48 45 4c 4c 4f)
```

The above code creates a byte stream sequence corresponding to `HELLO` in memory.

Byte streams are like lists and they can be extended, conncatenated and more. They allow
us operate on binary data. 

One very important use-case for bytes are to create a file containing binary data, 
the `file.write()` API expects to write byte streams to file when the file is opened in 
the binary mode and the most basic way of providing it with such data is by using `bytes`.

For example,

```blade-repl
%> file('dummy.txt', 'wb').write(bytes([72, 69, 76, 76, 79]))
true
%> file('dummy.txt').read()
'HELLO'
```

In the above sample, we wrote the bytes we created ealier into a file and read its contents.

> When a byte stream is created using a list of numbers, the maximum number 
> that will be interpreted as is is 255. All numbers exceeding that amount 
> will be equal to `(number % 255) - 1`.
> 
> E.g.
> ```blade-repl
> %> bytes([256])
> (0)
> %> bytes([386])
> (82)
> %> 0x82
> 130
> %> (386 % 255) - 1
> 130
> ```


## Byte stream indexing

Like _Lists_, _Strings_ and _Dictionaries_, Byte streams can also be indexed in Blade. We can retrieve an index in a byte stream using the same operators as others (`[]`) and we can use this to access or modify the contents of a byte stream.

For example,

```blade-repl
%> var g = bytes([31, 47, 83, 105, 72])
%> g
(1f 2f 53 69 48)
%> g[3]
105
%> g[1,3]
(2f 53)
%> g[2] = 96
%> g
(1f 2f 60 69 48)
```


## `bytes()` methods 

The byte stram object contains the following methods:

> **NOTE:** Byte streams are printed as hexadecimal lists.

#### bytes(value: _number_ | _list_)

Creates a new byte stream
  - if a number is given, creates an array of size number
  - if a list is given, converts the bytes list into an array of bytes.<br>

  For example,

  ```blade-repl
  %> bytes(5)
  (0 0 0 0 0)
  %> bytes([65, 66, 67, 68, 69])
  (41 42 43 44 45)
  ```
 
#### length()

Returns the length of a byte stream.<br>

  For example,

  ```blade-repl
  %> bytes([25, 57]).length()
  2
  ```
 
#### append(item: _any_)

Adds an item to the top of a byte stream.<br>

  For example,

  ```blade-repl
  %> var a = bytes([0x40, 0x75])
  %> a.append(0x16)
  %> echo a
  (40 75 16)
  ```
 
#### clone()

Returns a deep clone of the byte stream.<br>

  For example,

  ```blade-repl
  %> bytes([19, 11]).clone()
  (13 b)
  ```
 
#### extend(item: _bytes2_)

Adds the content of byte stream 2 into byte stream.<br>

  For example,

  ```blade-repl
  %> var a = bytes([33, 91, 126])
  %> var b = bytes([119, 42])
  %> a
  (21 5b 7e)
  %> b
  (77 2a)
  %> a.extend(b)
  (21 5b 7e 77 2a)
  %> a
  (21 5b 7e 77 2a)
  ```

  > **@note:** `extend()` is an in-place action so the original 
  > byte stream will be modified.

#### index_of(byte: _number_ [, start_index: _number_])

Returns the index position of the first occurrence of the byte _`byte`_ in the binary data (bytes). 

If the _byte_ cannot be found anywhere in _byte array_, it returns -1. If the `start_index` parameter is argument is given, it will start scanning from the given index.

  For example:

  ```blade-repl
  %> bytes([5, 10, 21, 22]).index_of(10)
  1
  %> bytes([1, 2, 3, 1, 2, 3]).index_of(1, 2)
  3
  %> bytes([1, 2, 3]).index_of(5)
  -1
  ```

#### pop()

Removes the last item in a byte stream and returns it.<br>

  For example,

  ```blade-repl
  %> var a = bytes([79, 43, 9])
  %> a.pop()
  9
  %> a
  (4f 2b)
  ```
 
#### remove(index: _number_)

Removes the item at the specified index in the byte stream.<br>

  For example,

  ```blade-repl
  %> var a = bytes([79, 43, 9, 139])
  %> a.remove(1)
  43
  %> a
  (4f 9 8b)
  ```
 
#### reverse()

Reverses the items in a byte stream.<br>

  For example,

  ```blade-repl
  %> bytes([1, 2, 3, 4, 5]).reverse()
  (5 4 3 2 1)
  ```
 
#### first()

Returns the first item in a byte stream or nil if the byte stream is empty.<br>

  For example,

  ```blade-repl
  %> bytes([14, 93, 37]).first()
  14
  ```
 
#### last()

Returns the last item in a byte stream or nil if the byte stream is empty.<br>

  For example,

  ```blade-repl
  %> bytes([14, 93, 37]).last()
  37
  ```
 
#### get(index: _number_)

Returns the value at index in the byte stream.<br>

  For example,

  ```blade-repl
  %> bytes([1, 2, 3, 4, 5]).get(3)
  4
  ```
 
#### split(delimiter: _bytes_)

Splits the content of a byte stream based on the specified delimiter.<br>

  For example,

  ```blade-repl
  %> bytes(0).split(bytes(0))
  []
  %> echo 'test'.to_bytes().split(bytes(0))
  [(74), (65), (73), (74)]
  ```
 
#### is_alpha()

Returns true if the byte stream contains only alphabets.<br>

  For example,

  ```blade-repl
  %> bytes([25, 57]).is_alpha()
  false
  %> bytes([65, 66]).is_alpha()
  true
  ```
 
#### is_alnum()

Returns true if the byte stream contains only number and alphabets.<br>

  For example,

  ```blade-repl
  %> bytes([25, 57]).is_alnum()
  false
  %> bytes([65, 66]).is_alnum()
  true
  %> bytes([97, 66]).is_alnum()
  true
  ```
 
#### is_number()

Returns true if the byte stream contains only number.<br>

  For example,

  ```blade-repl
  %> bytes([60, 61]).is_number()
  false
  %> bytes([49, 51]).is_number()
  true
  ```
 
#### is_lower()

Returns true if all the text in the byte stream are lower case.<br>

  For example,

  ```blade-repl
  %> bytes([97]).is_lower()
  true
  %> bytes([77]).is_lower()
  false
  ```
 
#### is_upper()

Returns true if all the text in the byte stream are capital case.<br>

  For example,

  ```blade-repl
  %> bytes([97]).is_upper()
  false
  %> bytes([67]).is_upper()
  true
  ```
 
#### is_space()

Returns true is the byte stream contains only white space.<br>

  For example,

  ```blade-repl
  %> bytes([13]).is_space() # 13 is the character number for ENTER
  true
  %> bytes([33]).is_space()
  false
  ```
 
#### dispose()

Due to the nature of byte stream and their use-case (especially streaming data),
  it is easy for the system memory to get filled up with data in the byte stream.
  The method allows users to reset a byte stream and empty it.

  > This allows manual memory management of byte stream.<br>

  For example,

  ```blade-repl
  %> var a = bytes([13, 36])
  %> a.dispose()
  %> a
  ()
  ```
 
#### to_list()

Returns a list of every byte in the byte stream.<br>

  For example,

  ```blade-repl
  %> bytes([0x31, 0x55, 0x149, 0x215]).to_list()
  [49, 85, 73, 21]
  ```
 
#### to_string()

Returns a string representation of the byte stream.<br>

  For example,

  ```blade-repl
  %> bytes([65, 66, 67, 68, 69]).to_string()
  'ABCDE'
  ```
 

<br><br><br>
<hr>

**_If you've come this far then you are already a Blade master! What you've learnt so far coupled with the standard library 
opens the door to endless possiblities. Remember that Blade is a growing language and stuffs are bound to change so we 
plead with you to keep up to date with this documentation to follow the development of the language of Ninjas._**


[Previous Topic](./modules)