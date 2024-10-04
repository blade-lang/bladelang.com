# clib
The `clib` module exposes Blade capabilities to interact with C
shared libraries. The workflow follows a simple approach.
- Load the library
- Define the function schematics
- Call the function.
That simple!
For example, the following code `dirname()` and `cos()` function from the
standard C library on a Unix machine (Linux, OSX, FreeBSD etc).
```blade
# Import clib
import clib
# 1. Load 'libc' shared module available on Unix systems
var lib = clib.load('libc')
# 2. Declare the functions
var dirname = lib.define('dirname', clib.char_ptr, clib.char_ptr)
var cos = lib.define('cos', clib.double, clib.double)     # this may not work on linux
# 3. Call the functions
echo dirname('/path/to/my/file.ext')
echo cos(23)
# Close the library (this is a good practice, but not required)
lib.close()
```
The first argument to a definition is the name of the function.
The second is its return type. If the function takes parameters,
the parameter types follow immediately. (See below for a list of the
available types.)
> **NOT YET SUPPORTED:**
> - Variadic functions

## Properties

- **void** &#8674; _ptr_:

  C void type

- **bool** &#8674; _ptr_:

  C bool type

- **uint8\_t** &#8674; _ptr_:

  C uint8_t type

- **int8\_t** &#8674; _ptr_:

  C int8_t type

- **byte** &#8674; _ptr_:

  C byte type

- **ubyte** &#8674; _ptr_:

  C ubyte type

- **uint16\_t** &#8674; _ptr_:

  C uint16_t type

- **int16\_t** &#8674; _ptr_:

  C int16_t type

- **uint32\_t** &#8674; _ptr_:

  C uint32_t type

- **int32\_t** &#8674; _ptr_:

  C int32_t type

- **uint64\_t** &#8674; _ptr_:

  C uint64_t type

- **int64\_t** &#8674; _ptr_:

  C int64_t type

- **ssize\_t** &#8674; _ptr_:

  C ssize_t type

- **float** &#8674; _ptr_:

  C float type

- **double** &#8674; _ptr_:

  C double type

- **uchar** &#8674; _ptr_:

  C uchar type

- **char** &#8674; _ptr_:

  C char type

- **ushort** &#8674; _ptr_:

  C ushort type

- **short** &#8674; _ptr_:

  C short type

- **uint** &#8674; _ptr_:

  C uint type

- **int** &#8674; _ptr_:

  C int type

- **ulong** &#8674; _ptr_:

  C ulong type

- **long** &#8674; _ptr_:

  C long type

- **size\_t** &#8674; _ptr_:

  C size_t type

- **long\_double** &#8674; _ptr_:

  C long_double type

- **char\_ptr** &#8674; _ptr_:

  C char_ptr type

- **uchar\_ptr** &#8674; _ptr_:

  C uchar_ptr type

- **ptr** &#8674; _ptr_:

  C ptr type

- **function** &#8674; _ptr_:

  C closure/callback type


## Functions

#### load(name)

Loads a new C shared library pointed to by name. Name must be a 
relative path, absolute path or the name of a system library. 
If the system shared library extension is omitted in the name, 
it will be automatically added.

##### Parameters

- _string_ **name**

##### Returns

- CLib



#### new(type, ...)

Creates a new C value for the specified clib type with the given values.

##### Parameters

- _clib_type_ **type**
- _any..._ **values**

##### Returns

- bytes



#### get(type, data)

Returns the data contained in a C type _type_ encoded in the data.
The data should either be an output of `clib.new()` or a call to a 
function returning one of struct, union or array.

For structures created with `named_struct()`, a dictionary will 
automatically be returned with the values mapped to the names of the 
structure elements.

##### Parameters

- _clib_type_ **type**
- _string|bytes_ **data**

##### Returns

- list|dictionary



#### get\_ptr\_index(pointer, type, index)

get_ptr_index(pointer: ptr, type: clib_type, index: number)

Get the value at the given index of a pointer based 
on the given CLib type.

##### Parameters

- _ptr_ **pointer**
- _clib_type_ **type**
- _number_ **index**

##### Returns

- any



#### set\_ptr\_index(pointer, type, index, value)

Sets the value at the given index of a pointer based 
on the given CLib type to the given value.

##### Parameters

- _ptr_ **pointer**
- _clib_type_ **type**
- _number_ **index**
- _any_ **value**

##### Returns

- any



#### function\_handle(handle, return_type, ...)

Defines a new C function from an existing handle and return type.
-  When there are no more argument, it is declared that the function
   takes no argument.
-  `define()` expects a list of the argument/parameter types as expected
   by the function.

E.g.

```blade
function_handle(my_ptr, int, int, ptr)
```

Corresponds to the C declaration:

```c
int (*my_ptr)(int a, void *b);
```

##### Parameters

- _ptr_ **handle**
- _clib_type_ **return_type**
- _clib_type..._ **arg_types**

##### Returns

- function



#### create\_callback(closure, return_type, ...)

Creates a callback to be passed to C functions expecting a callback.

For example, imagine a C function defined as below:

```c
void ex_puts(const char *name, void (*fn)(char *req, char *res));
```

To pass the callback (second parameter) to this function, you'll need to 
wrap a blade function with `create_callback()` to properly define the 
callback return type and parameters.

The above function can be defined as:

```blade
var fn lib.define('ex_puts', clib.void, clib.char_ptr, clib.function)
```

To call this function and pass a Blade function that can be called when C 
triggers the callback, the second argument to the function will need to be 
wrapped in `create_callback()`. Thus, the above function can be called 
like this:

```blade
fn(
   'Blade Callbacks', 
   clib.create_callback(
     @(req, res) {
       echo 'Request is: ' + req
       echo 'Response is: ' + res
     }, 
     clib.void, # The return type of the callback
     clib.char_ptr, clib.char_ptr  # the parameters of the callback
   )
)
```

> **NOTE:** A callback can only be passed to a parameter previously defined 
> as function.

##### Parameters

- _function_ **closure**
- _clib_type_ **return_type**
- _clib_type..._ **types**

##### Returns

- clib_callback



#### struct(...)

Returns a type that can be used to declare structs. 
To create or read value for the struct you need to use the `new()` 
and `get()` functions respectively.
Alternatively, you may use the `pack()` and `unpack()` 
function in the `struct` module respectively.

##### Parameters

- _any..._ **type**

##### Returns

- type
##### Notes

- This function can also be used to define a C union or array.



#### named\_struct(types)

Returns a type that can be used to declare structs based on the named 
types. The function works well with the `get()` function because it 
automatically assigns the name of the struct elements when getting the 
value. 

To create or read value for the struct you need to use the `new()` 
and `get()` functions respectively.
Alternatively, you may use the `pack()` and `unpack()` 
function in the `struct` module respectively.

##### Parameters

- _dictionary_ **types**

##### Returns

- type
##### Notes

- This function can also be used to define a C union or array.



## Classes

### _class_ Clib

class CLib provides an interface for interacting with C shared modules.

#### Methods

#### Clib(name) &#8674; Constructor



##### Parameters

- _string?_ **name**

##### Notes

- The _name_ should follow the same practice outlined in `load()`.

#### load(name)

Loads a new C shared library pointed to by name. Name must be a 
relative path, absolute path or the name of a system library. 
If the system shared library extension is omitted in the name, 
it will be automatically added except on Linux machines.

##### Parameters

- _string_ **name**


#### close()

Closes the handle to the shared library.


#### function(name)

Retrieves the handle to a specific function in the shared library.

##### Parameters

- _string_ **name**

##### Returns

- ptr

#### define(name, return_type, ...)

Defines a new C function with the given name and return type.
-  When there are no more argument, it is declared that the function
   takes no argument.
-  `define()` expects a list of the argument/parameter types as expected
   by the function.

E.g.

```blade
define('myfunc', int, int, ptr)
```

Corresponds to the C declaration:

```c
int myfunc(int a, voidb);
 ```

##### Parameters

- _string_ **name**
- _clib_type_ **return_type**
- _clib_type..._ **types**

##### Returns

- function

#### get\_pointer()

Returns a pointer to the underlying module.

##### Returns

- ptr



