# math
This module contains functions and constants to make trigonometric and 
non-trignonometric mathematics a breeze. The module also defines a couple 
of commonly used scientific and mathematical constants such as `PI`.

## Properties

- **PI**: represents the ratio of the circumference of a circle 
to its diameter
- **E**: represents Euler's number, the base of natural logarithms
- **LOG\_10**: represents the natural logarithm of 10
- **LOG\_10\_E**: represents the base 10 logarithm of e
- **LOG\_2**: represents the natural logarithm of 2
- **LOG\_2\_E**: represents the base 2 logarithm of e
- **ROOT\_2**: represents the square root of 2
- **ROOT\_3**: represents the square root of 3
- **ROOT\_HALF**: represents the square root of 1/2
- **Infinity**: Mathematical infinity
- **NaN**: Mathematical NaN

## Functions

#### factorial(n)

factorial(n: number)
calculates the product of all positive 
numbers less than or equal to a given positive number n


Example:

```blade-repl
%> import math
%> math.factorial(60)
8.320987112741392e+81
```
##### Returns

- number



#### sin(n)

Returns a numeric value between -1 and 1, which 
represents the sine of the angle given in radians.

Example:

```blade-repl
%> math.sin(46)
0.9017883476488092
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### cos(n)

Returns a numeric value between -1 and 1, which 
represents the cosine of the angle.

Example:

```blade-repl
%> math.cos(93)
0.3174287015197017
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### tan(n)

Returns a numeric value that represents the tangent 
of the angle given.

Example:

```blade-repl
%> math.tan(11.43)
-2.155225644164932
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### sinh(n)

Returns the hyperbolic sine (in radians) of number n.

Example:

```blade-repl
%> math.sinh(1.4)
1.904301501451534
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### cosh(n)

Returns the hyperbolic cosine (in radians) of number n.

Example:

```blade-repl
%> math.cosh(1.91)
3.450584592563374
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### tanh(n)

Returns the hyperbolic tangent (in radians) of number n.

Example:

```blade-repl
%> math.tanh(2.19)
0.975



```
##### Parameters

- _number_ **n**

##### Returns

- number2591705196751



#### asin(n)

Returns a numeric value between -(π/2) and π/2 radians 
for x between -1 and 1. 
If the value of x is outside this range, it returns NaN.

Example:

```blade-repl
%> math.asin(0.123)
0.123312275191872
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### acos(n)

Returns a numeric value between 0 and π radians for x 
between -1 and 1. If the value of x is outside this range, it 
returns NaN.

Example:

```blade-repl
%> math.acos(0.471)
1.080372275769021
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### atan(n)

Returns a numeric value between -(π/2) and π/2 radians.

Example:

```blade-repl
%> math.atan(math.Infinity)
1.570796326794897
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### atan2(x, y)

Returns a numeric value between -π and π representing the 
angle theta of an (x, y) point. This is the counterclockwise angle, 
measured in radians, between the positive X axis, and the point (x, y). 

Example:

```blade-repl
%> math.atan2(math.Infinity, -math.Infinity)
2.356194490192345
%> math.atan2(1, 2)
0.4636476090008061
%> math.atan2(-1.5, 2.4)
-0.5585993153435624
```
##### Parameters

- _number_ **n**

##### Returns

- number
##### Notes

- the arguments to this function pass the y-coordinate first and the x-coordinate second.



#### asinh(n)

Returns the hyperbolic arcsine (in radians) of number n.

Example:

```blade-repl
%> math.asinh(3.42)
1.943507380182802
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### acosh(n)

Returns the hyperbolic arccosine (in radians) of number n.

Example:

```blade-repl
%> math.acosh(1.21)
0.637237379754108
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### atanh(n)

Returns the hyperbolic arctangent (in radians) of number n.

Example:

```blade-repl
%> math.atanh(0.11)
0.1104469157900971
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### exp(n)

Returns e ** x, where x is the argument, and e is Euler's 
number (also known as Napier's constant), the base of the 
natural logarithms.

Example:

```blade-repl
%> math.exp(4)
54.59815003314424
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### expm1(n)

Returns (e ** x) - 1, where x is the argument, and e the base of 
the natural logarithms.

Example:

```blade-repl
%> math.expm1(1)
1.718281828459045
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### ceil(n)

Returns number n rounded up to the next largest integer.

Example:

```blade-repl
%> math.ceil(1.65)
2
%> math.ceil(1.01)
2
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### round(n)

Returns the value of a number rounded to the nearest integer.

Example:

```blade-repl
%> math.round(103.51)
104
%> math.round(103.49)
103
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### log(n)

Returns the natural logarithm (base e) of a number (mathematical ln(x)).

Example:

```blade-repl
%> math.log(45)
3.80666248977032
```
##### Parameters

- _number_ **n**

##### Returns

- number
##### Notes

- If the value of x is 0, the return value is always -inf.
- If the value of x is negative, the return value is always NaN.



#### log2(n)

Returns the base 2 logarithm of the given number. 
If the number is negative, NaN is returned

Example:

```blade-repl
%> math.log2(45)
5.491853096329675
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### log10(n)

Returns the base 10 logarithm of the given number. 
If the number is negative, NaN is returned.

Example:

```blade-repl
%> math.log10(45)
1.653212513775344
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### log1p(n)

For very small values of x, adding 1 can reduce or eliminate precision.  
The double floats used in JS give you about 15 digits of precision.  
1 + 1e-15 = 1.000000000000001, but 1 + 1e-16 = 1.000000000000000 and therefore 
exactly 1.0 in that arithmetic, because digits past 15 are rounded off.  

When you calculate log(1 + x), you should get an answer very close to x, 
if x is small (that's why these are called 'natural' logarithms).  
If you calculate log(1 + 1.1111111111e-15) you should get an answer 
close to 1.1111111111e-15.  
Instead, you will end up taking the logarithm of 1.00000000000000111022 
(the roundoff is in binary so sometimes it gets ugly), so you get the answer 
1.11022...e-15, with only  3 correct digits.  
If, instead, you calculate log1p(1.1111111111e-15) you will get a much 
more accurate answer 1.1111111110999995e-15 with 15 correct digits of precision 
(actually 16 in this case).

returns the natural logarithm (base e) of 1 + a number
If the value of x is less than -1, the return value is always NaN.

Example:

```blade-repl
%> math.log1p(45)
3.828641396489095
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### cbrt(n)

Returns the cube root of a number n.

Example:

```blade-repl
%> math.cbrt(64)
4
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### sign(n)

Returns either a positive or negative +/- 1, indicating the sign of 
a number passed into the argument. 
If the number passed into sign() is 0, it will return a 0.

Example:

```blade-repl
%> math.sign(10)
1
%> math.sign(-20)
-1
%> math.sign(-0)
-0
%> math.sign(0)
0
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### floor(n)

A number representing the largest integer less than or 
equal to the specified number

Example:

```blade-repl
%> math.floor(1.92)
1
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### is\_nan(n)

is_nan(n: number)

returns true if the given number is equal to NaN or false otherwise.
##### Parameters

- _number_ **n**

##### Returns

- bool



#### is\_inf(n)

Returns `true` if the given number is equal to Infinity or -Infinity 
or `false` otherwise.

Example:

```blade-repl
%> math.is_inf(math.Infinity)
true
%> math.is_inf(-math.Infinity)
true
%> math.is_inf(0)
false
```
##### Parameters

- _number_ **n**

##### Returns

- bool



#### is\_finite(n)

Return `true` if x is neither an Infinity nor a NaN, and `false` otherwise.

Example:

```blade-repl
%> math.is_finite(0)
true
%> math.is_finite(math.NaN)
true
%> math.is_finite(-math.Infinity)
false
```
##### Parameters

- _number_ **n**

##### Returns

- bool



#### trunc(n)

Returns the integer part of a number by removing any fractional.

Example:

```blade-repl
%> math.trunc(1.92)
1
%> math.trunc(1.0)
1
%> math.trunc(1.01)
1
%> math.trunc(-1.01)
-1
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### sqrt(n)

Returns the square root of a nunmber.

Example:

```blade-repl
%> math.sqrt(100)
10
```
##### Parameters

- _number_ **n**

##### Returns

- number



#### sum(arg)

Calculates the sum of all the elements in the input iterable
the default start value for the product is 1.
when the iterable is empty, it returns 1

Example:

```blade-repl
%> math.sum([1, 2, [3, 4, [5, 6]]])
21
```
##### Parameters

- _iterable_ **arg**

##### Returns

- number



#### product(arg)

Calculates the product of all the elements in the input iterable
the default start value for the product is 1.
when the iterable is empty, it returns 1

Example:

```blade-repl
%> math.product([1, 2, [3, 4, [5, 6]]])
720
```
##### Parameters

- _iterable_ **arg**

##### Returns

- number



#### fraction(n)

Returns the fractional part of a number as a whole number 
by removing any integer

Example:

```blade-repl
%> math.fraction(1.92)
92
```
##### Parameters

- _number_ **n**

##### Returns

- number



