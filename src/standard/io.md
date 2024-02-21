# io

This module provides interfaces for working with to I/O stream and TTYs 
as well as expose the operating system standard I/O for easy access.

Some I/O operations that should belong to this module have been merged as 
core features and offered as built-in functions for Blade. Specifically 
file I/O features that can be accessed via the built-in `file()` function. 

The standard I/O streams are also files and you can call almost all file 
methods on them. Whenever a file method is not supported, you'll get an error 
message telling you that such operation is not supported for standard streams.

### Example

The following example shows how to use the `io` module for accepting user name 
and printing the result.

```blade
import io

var name = io.readline('What is your name?')
echo name
```

## Properties

- **SEEK\_SET** &#8674; _int_: Set I/O position from the beginning.
- **SEEK\_CUR** &#8674; _int_: Set I/O position from the current position.
- **SEEK\_END** &#8674; _int_: Set I/O position from the end.
- **stdin** &#8674; _file_: Stdin is a file handle to the standard input file of the system.
- **stdout** &#8674; _file_: Stdout is a file handle to the standard output file of the system.
- **stderr** &#8674; _file_: Stderr is a file handle to the standard error file of the system.

## Functions

#### flush(file)

Flushes the content of the given file handle



#### putc(c)

Writes character c to the screen.
##### Parameters

- _{char|number}_ **c**




#### getc()

Reads character(s) from standard input
When length is given, gets `length` number of characters
else, gets a single character
##### Returns

- {char|string}



#### getch()

Reads character(s) from standard input without printing to standard output
When length is given, gets `length` number of characters
else, gets a single character.
##### Returns

- {char|string}



#### readline(message, secure, obscure_text)

Reads an entire line from standard input. If a _messagge_ is given, the 
message will be printed before it begins to wait for a user input. If 
_secure_ is `true`, the user's input will not be printing and _obscure_text_ 
will be printed instead.
##### Parameters

- _string?_ **message**
- _bool?_ **secure**
- _string?_ **obscure_text**: : Default value is `*`.

##### Returns

- string
##### Notes

- Newlines will not be added automatically for messages.



## Classes

### _class_ TTY

class TTY is an interface to TTY terminals this class contains definitions 
to control TTY terminals

#### Fields

- **TTY\_IFLAG** &#8674; _static_ _int_: TTY attribute for input flags.
- **TTY\_OFLAG** &#8674; _static_ _int_: TTY attribute for output flags.
- **TTY\_CFLAG** &#8674; _static_ _int_: TTY attribute for control flags.
- **TTY\_LFLAG** &#8674; _static_ _int_: TTY attribute for local flags.
- **TTY\_ISPEED** &#8674; _static_ _int_: TTY attribute for input speed.
- **TTY\_OSPEED** &#8674; _static_ _int_: TTY attribute for output speed.
- **IGNBRK** &#8674; _static_ _int_: Ignore BREAK condition.
- **BRKINT** &#8674; _static_ _int_: Map BREAK to SIGINTR.
- **IGNPAR** &#8674; _static_ _int_: Ignore (discard) parity errors.
- **PARMRK** &#8674; _static_ _int_: Mark parity and framing errors.
- **INPCK** &#8674; _static_ _int_: Enable checking of parity errors.
- **ISTRIP** &#8674; _static_ _int_: Strip 8th bit off chars.
- **INLCR** &#8674; _static_ _int_: Map NL into CR.
- **IGNCR** &#8674; _static_ _int_: Ignore CR.
- **ICRNL** &#8674; _static_ _int_: Map CR to NL (ala CRMOD).
- **IXON** &#8674; _static_ _int_: Enable output flow control.
- **IXOFF** &#8674; _static_ _int_: Enable input flow control.
- **IXANY** &#8674; _static_ _int_: Any char will restart after stop.
- **IUTF8** &#8674; _static_ _int_: Maintain state for UTF-8 VERASE.
- **OPOST** &#8674; _static_ _int_: Enable following output processing.
- **ONLCR** &#8674; _static_ _int_: Map NL to CR-NL (ala CRMOD).
- **CSIZE** &#8674; _static_ _int_: Character size mask .
- **CS5** &#8674; _static_ _int_: 5 bits (pseudo).
- **CS6** &#8674; _static_ _int_: 6 bits.
- **CS7** &#8674; _static_ _int_: 7 bits.
- **CS8** &#8674; _static_ _int_: 8 bits.
- **CSTOPB** &#8674; _static_ _int_: Send 2 stop bits.
- **CREAD** &#8674; _static_ _int_: Enable receiver.
- **PARENB** &#8674; _static_ _int_: Parity enable.
- **PARODD** &#8674; _static_ _int_: Odd parity, else even.
- **HUPCL** &#8674; _static_ _int_: Hang up on last close.
- **CLOCAL** &#8674; _static_ _int_: Ignore modem status lines.
- **ECHOE** &#8674; _static_ _int_: Visually erase chars.
- **ECHOK** &#8674; _static_: Echo NL after line kill
- **ECHO** &#8674; _static_ _int_: Enable echoing.
- **ECHONL** &#8674; _static_ _int_: Echo NL even if ECHO is off.
- **ISIG** &#8674; _static_ _int_: Enable signals INTR, QUIT, [D]SUSP.
- **ICANON** &#8674; _static_ _int_: Canonicalize input lines.
- **IEXTEN** &#8674; _static_ _int_: Enable DISCARD and LNEXT.
- **TOSTOP** &#8674; _static_ _int_: Stop background jobs from output.
- **NOFLSH** &#8674; _static_ _int_: Don't flush after interrupt.
- **TCSANOW** &#8674; _static_ _int_: Make change immediate.
- **TCSADRAIN** &#8674; _static_ _int_: Drain output, then change.
- **TCSAFLUSH** &#8674; _static_ _int_: Drain output, flush input.
- **VEOF** &#8674; _static_ _int_: ICANON.
- **VEOL** &#8674; _static_ _int_: ICANON.
- **VERASE** &#8674; _static_ _int_: ICANON.
- **VKILL** &#8674; _static_ _int_: ICANON.
- **VINTR** &#8674; _static_ _int_: ISIG.
- **VQUIT** &#8674; _static_ _int_: ISIG.
- **VSUSP** &#8674; _static_ _int_: ISIG.
- **VSTART** &#8674; _static_ _int_: IXON, IXOFF.
- **VSTOP** &#8674; _static_ _int_: IXON, IXOFF.
- **VMIN** &#8674; _static_ _int_: !ICANON.
- **VTIME** &#8674; _static_ _int_: !ICANON.

#### Methods

#### TTY(std) &#8674; Constructor

TTY(std: file)
##### Parameters

- _file_ **std**

##### Notes

- _file_ must be one of stdout and stderr

#### get\_attr()

Returns the attribute of the current tty session
The returned attributes is a dict containing the TTY_ flags
##### Returns

- dict

#### set\_attr(option, attrs)

set_attr(option: number, attrs: dict)

sets the attributes of the current tty session

- option: one ot the TCSA options above (see their description above)
- attrs a dictionary of the TTY_ flags listed above
- one can safely omit any of the TTY_ flags listed above and Blade will fill in the default values as it exists.
##### Parameters

- _number_ **option**
- _dict_ **attr**

##### Returns

- bool
##### Notes

- This flags will be merged and not overwritten

#### set\_raw()

Sets the current tty to raw mode.
##### Returns

- bool

#### exit\_raw()

Disables the raw mode flags on the current tty.
##### Returns

- bool

#### flush()

Flushes the standard output and standard error interface



