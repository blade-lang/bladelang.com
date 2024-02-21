# ast
Provides interface for parsing Blade code into Abstract Syntax Trees.

## Properties

- **NEWLINE**: newline token
- **LPAREN**: left parenthesis (`(`) token
- **RPAREN**: right parenthesis (`)`) token
- **LBRACKET**: left bracket (`[`) token
- **RBRACKET**: right bracket (`]`) token
- **LBRACE**: left brace (`{`) token
- **RBRACE**: right brace (`}`) token
- **SEMICOLON**: semicolon (`;`) token
- **COMMA**: comma (`,`) token
- **BACKSLASH**: backslash (`\`) token
- **BANG**: not (`!`) token
- **BANG\_EQ**: not equal (`!=`) token
- **COLON**: colon (`:`) token
- **AT**: at (`@`) token
- **DOT**: dot (`.`) token
- **RANGE**: range (`..`) token
- **TRI\_DOT**: tridot (`...`) token
- **PLUS**: plus (`+`) token
- **PLUS\_EQ**: plus equal (`+=`) token
- **INCREMENT**: increment (`++`) token
- **MINUS**: minus (`-`) token
- **MINUS\_EQ**: minus equal (`-=`) token
- **DECREMENT**: decrement (`--`) token
- **MULTIPLY**: multiply (`*`) token
- **MULTIPLY\_EQ**: multiply equal (`*=`) token
- **POW**: pow (`**`) token
- **POW\_EQ**: pow equal (`**=`) token
- **DIVIDE**: divide (`/`) token
- **DIVIDE\_EQ**: divide equal (`/=`) token
- **FLOOR**: floor division (`//`) token
- **FLOOR\_EQ**: floor divide equal (`//=`) token
- **EQUAL**: assignment (`=`) token
- **EQUAL\_EQ**: equality (`==`) token
- **LESS**: less than (`<`) token
- **LESS\_EQ**: less than or equal (`<=`) token
- **LSHIFT**: left shift (`<<`) token
- **LSHIFT\_EQ**: left shift equal (`<<=`) token
- **GREATER**: greater than (`>`) token
- **GREATER\_EQ**: greather than or equal (`>=`) token
- **RSHIFT**: right shift (`>>`) token
- **RSHIFT\_EQ**: right shift equal (`>>=`) token
- **PERCENT**: modulous (`%`) token
- **PERCENT\_EQ**: modulous equal (`%=`) token
- **AMP**: ampersand (`&`) token
- **AMP\_EQ**: and equal (`&=`) token
- **BAR**: bar (`|`) token
- **BAR\_EQ**: bar equal (`|=`) token
- **TILDE**: tilde/not (`~`) token
- **TILDE\_EQ**: tilde equal (`~=`) token
- **XOR**: exclusive or (`^`) token
- **XOR\_EQ**: exclusive or equal (`^=`) token
- **QUESTION**: question (`?`) token
- **AND**: and token
- **AS**: as token
- **ASSERT**: assert token
- **BREAK**: break token
- **CATCH**: catch token
- **CLASS**: class token
- **CONTINUE**: continue token
- **DEF**: def token
- **DEFAULT**: default token
- **DIE**: die token
- **DO**: do token
- **ECHO**: echo token
- **ELSE**: else token
- **FALSE**: false token
- **FINALLY**: finally token
- **FOR**: for token
- **IF**: if token
- **IMPORT**: import token
- **IN**: in token
- **ITER**: iter token
- **NIL**: nil token
- **OR**: or token
- **PARENT**: parent token
- **RETURN**: return token
- **SELF**: self token
- **STATIC**: static token
- **TRUE**: true token
- **TRY**: try token
- **USING**: using token
- **VAR**: var token
- **WHEN**: when token
- **WHILE**: while token
- **LITERAL**: string literal token
- **REG\_NUMBER**: regular number token
- **BIN\_NUMBER**: binary number token
- **OCT\_NUMBER**: octal number token
- **HEX\_NUMBER**: hexadecimal number token
- **IDENTIFIER**: identifier token
- **DECORATOR**: decorator token
- **INTERPOLATION**: interpolation token
- **COMMENT**: comment token
- **DOC**: doc block token
- **EOF**: eof token
- **ERROR**: error token
- **EMPTY**: empty token

## Functions

#### parse(source, path)

Parses a given source code and outputs Blade AST objects.
##### Parameters

- _string_ **source**
- _string?_ **path**

##### Returns

- ParseResult



#### json(source, path)

Parses the give source code and outputs a JSON representation of 
it's AST structure.
##### Parameters

- _string_ **source**
- _string?_ **path**

##### Returns

- string



## Classes

### _class_ ParseResult

Represents the result of an ast parse operation.



#### Properties

 - __@printable__
 - __@serializable__
 - __@iterable__

#### Methods

#### append(item)

Adds a new item to the parse result
##### Parameters

- _{Expr|Decl|Defn|Stmt}_ **item**


#### length()

Returns the length of items in the parsed result.
##### Returns

- number

#### get(index)

Returns the item at the given ParseResult index or throws exception if out of range.
##### Parameters

- _int_ **index**

##### Returns

- {Expr|Decl|Defn|Stmt}

#### to\_list()

Returns the items in the ParseResult as a list object.
##### Returns

- {list[Expr|Decl|Defn|Stmt]}



### _class_ Scanner

Blade source code scanner.



#### Properties

 - __@printable__

#### Fields

- **has\_error** &#8674; _readonly_ _bool_: Reports if an error was encountered in the scaner.
- **source** &#8674; _readonly_ _string_: The string to being scanned.

#### Methods

#### Scanner(source, file) &#8674; Constructor


##### Parameters

- _string_ **source**


#### scan()

Scans the source and returns a list of tokens.
##### Returns

- list[Token]



### _class_ Token

Blade source code token.



#### Properties

 - __@printable__
 - __@serializable__

#### Methods

#### Token(type, literal, line, file) &#8674; Constructor


##### Parameters

- _number_ **type**
- _string_ **literal**
- _number_ **line**



### _class_ ParseException < _Exception_

Exception raised for errors during parsing.

#### Methods

#### ParseException(token, message) &#8674; Constructor


##### Parameters

- _{Token}_ **token**
- _string_ **message**



### _class_ Stmt

base Stmt class



### _class_ EchoStmt < _Stmt_

Echo Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### EchoStmt(value) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **value**



### _class_ ExprStmt < _Stmt_

Expr Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### ExprStmt(expr) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **expr**



### _class_ IfStmt < _Stmt_

If Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### IfStmt(condition, truth, falsy) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **condition**
- _{Stmt|any|nil}_ **truth**
- _{Stmt|any|nil}_ **falsy**



### _class_ IterStmt < _Stmt_

Iter Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### IterStmt(declaration, condition, iterator, body) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **declaration**
- _{Stmt|any|nil}_ **condition**
- _{Stmt|any|nil}_ **iterator**
- _{Stmt|any|nil}_ **body**



### _class_ WhileStmt < _Stmt_

While Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### WhileStmt(condition, body) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **condition**
- _{Stmt|any|nil}_ **body**



### _class_ DoWhileStmt < _Stmt_

DoWhile Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### DoWhileStmt(body, condition) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **body**
- _{Stmt|any|nil}_ **condition**



### _class_ ForStmt < _Stmt_

For Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### ForStmt(vars, iterable, body) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **vars**
- _{Stmt|any|nil}_ **iterable**
- _{Stmt|any|nil}_ **body**



### _class_ ContinueStmt < _Stmt_

Continue Stmt representation.



#### Properties

 - __@serializable__



### _class_ BreakStmt < _Stmt_

Break Stmt representation.



#### Properties

 - __@serializable__



### _class_ DieStmt < _Stmt_

Die Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### DieStmt(exception) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **exception**



### _class_ ReturnStmt < _Stmt_

Return Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### ReturnStmt(value) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **value**



### _class_ AssertStmt < _Stmt_

Assert Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### AssertStmt(expr, message) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **expr**
- _{Stmt|any|nil}_ **message**



### _class_ UsingStmt < _Stmt_

Using Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### UsingStmt(expr, cases, default_case) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **expr**
- _{Stmt|any|nil}_ **cases**
- _{Stmt|any|nil}_ **default_case**



### _class_ ImportStmt < _Stmt_

Import Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### ImportStmt(path, elements) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **path**
- _{Stmt|any|nil}_ **elements**



### _class_ CatchStmt < _Stmt_

Catch Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### CatchStmt(type, var_name, body) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **type**
- _{Stmt|any|nil}_ **var_name**
- _{Stmt|any|nil}_ **body**



### _class_ FinallyStmt < _Stmt_

Finally Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### FinallyStmt(body) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **body**



### _class_ TryStmt < _Stmt_

Try Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### TryStmt(body, catch_stmt, finally_stmt) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **body**
- _{Stmt|any|nil}_ **catch_stmt**
- _{Stmt|any|nil}_ **finally_stmt**



### _class_ CommentStmt < _Stmt_

Comment Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### CommentStmt(data) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **data**



### _class_ BlockStmt < _Stmt_

Block Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### BlockStmt(body) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **body**



### _class_ AssignStmt < _Stmt_

Assign Stmt representation.



#### Properties

 - __@serializable__

#### Methods

#### AssignStmt(expr, type, value) &#8674; Constructor


##### Parameters

- _{Stmt|any|nil}_ **expr**
- _{Stmt|any|nil}_ **type**
- _{Stmt|any|nil}_ **value**



### _class_ Defn

base Defn class



### _class_ DocDefn < _Defn_

Doc Defn representation.



#### Properties

 - __@serializable__

#### Methods

#### DocDefn(data) &#8674; Constructor


##### Parameters

- _{Defn|any|nil}_ **data**



### _class_ Parser

Parses raw Blade tokens and produces an Abstract Syntax Tree.



#### Properties

 - __@printable__

#### Methods

#### Parser(tokens, path) &#8674; Constructor


##### Parameters

- _{list[Token]}_ **tokens**
- _string?_ **path**


#### parse()

Parses the raw source tokens passed into relevant class and
outputs a stream of AST objects that can be one of
Expr (expressions), Stmt (statements) or Decl (declarations).
##### Returns

- ParseResult



### _class_ Decl

base Decl class



### _class_ VarDecl < _Decl_

Var Decl representation.



#### Properties

 - __@serializable__

#### Methods

#### VarDecl(name, value) &#8674; Constructor


##### Parameters

- _{Decl|any|nil}_ **name**
- _{Decl|any|nil}_ **value**



### _class_ FunctionDecl < _Decl_

Function Decl representation.



#### Properties

 - __@serializable__

#### Methods

#### FunctionDecl(name, params, body) &#8674; Constructor


##### Parameters

- _{Decl|any|nil}_ **name**
- _{Decl|any|nil}_ **params**
- _{Decl|any|nil}_ **body**



### _class_ MethodDecl < _Decl_

Method Decl representation.



#### Properties

 - __@serializable__

#### Methods

#### MethodDecl(name, params, body, is_static) &#8674; Constructor


##### Parameters

- _{Decl|any|nil}_ **name**
- _{Decl|any|nil}_ **params**
- _{Decl|any|nil}_ **body**
- _{Decl|any|nil}_ **is_static**



### _class_ PropertyDecl < _Decl_

Property Decl representation.



#### Properties

 - __@serializable__

#### Methods

#### PropertyDecl(name, value, is_static) &#8674; Constructor


##### Parameters

- _{Decl|any|nil}_ **name**
- _{Decl|any|nil}_ **value**
- _{Decl|any|nil}_ **is_static**



### _class_ ClassDecl < _Decl_

Class Decl representation.



#### Properties

 - __@serializable__

#### Methods

#### ClassDecl(name, superclass, properties, methods) &#8674; Constructor


##### Parameters

- _{Decl|any|nil}_ **name**
- _{Decl|any|nil}_ **superclass**
- _{Decl|any|nil}_ **properties**
- _{Decl|any|nil}_ **methods**



### _class_ Expr

base Expr class



### _class_ BinaryExpr < _Expr_

Binary Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### BinaryExpr(left, op, right) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **left**
- _{Expr|any|nil}_ **op**
- _{Expr|any|nil}_ **right**



### _class_ GroupExpr < _Expr_

Group Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### GroupExpr(expression) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **expression**



### _class_ LiteralExpr < _Expr_

Literal Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### LiteralExpr(value) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **value**



### _class_ IdentifierExpr < _Expr_

Identifier Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### IdentifierExpr(value) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **value**



### _class_ UnaryExpr < _Expr_

Unary Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### UnaryExpr(op, right) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **op**
- _{Expr|any|nil}_ **right**



### _class_ ConditionExpr < _Expr_

Condition Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### ConditionExpr(expr, truth, falsy) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **expr**
- _{Expr|any|nil}_ **truth**
- _{Expr|any|nil}_ **falsy**



### _class_ CallExpr < _Expr_

Call Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### CallExpr(callee, args) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **callee**
- _{Expr|any|nil}_ **args**



### _class_ GetExpr < _Expr_

Get Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### GetExpr(expr, name) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **expr**
- _{Expr|any|nil}_ **name**



### _class_ SetExpr < _Expr_

Set Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### SetExpr(expr, name, value) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **expr**
- _{Expr|any|nil}_ **name**
- _{Expr|any|nil}_ **value**



### _class_ IndexExpr < _Expr_

Index Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### IndexExpr(args) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **args**



### _class_ ListExpr < _Expr_

List Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### ListExpr(items) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **items**



### _class_ DictExpr < _Expr_

Dict Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### DictExpr(keys, values) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **keys**
- _{Expr|any|nil}_ **values**



### _class_ InterpolationExpr < _Expr_

Interpolation Expr representation.



#### Properties

 - __@serializable__

#### Methods

#### InterpolationExpr(data) &#8674; Constructor


##### Parameters

- _{Expr|any|nil}_ **data**



