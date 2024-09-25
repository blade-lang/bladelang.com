# html

The html module provides interfaces for converting HTML to Blade and vice-versa.

## Nodes: Simplifying HTML Representation

Nodes are the building blocks that describe HTML tags, including their attributes, contents, and nested children. This representation closely resembles how web browsers organize an HTML document in the Document Object Model (DOM) using nodes. When the `html` module decodes HTML, it generates a nested list of nodes.

Within the `html` module, there are two main types of elements, just like in the HTML DOM: Text nodes and Element nodes.

### Element Node: Structuring HTML Elements

An element node is represented by a dictionary with the following properties:

- **type**: Indicates the node type. For element nodes, this value is always "element."
- **name**: Specifies the name of the HTML element.
- **attributes**: Contains a list of attributes associated with the HTML element, such as the `id` or `style` attribute. Each attribute consists of a `name` and `value` entry.
- **children**: Represents a list of nodes that are nested within the current element.

### Text Node: Handling Textual Content

A text node is represented by a dictionary with the following properties:

- **type**: Indicates the node type. For text nodes, this value is always "text."
- **content**: Stores the textual content of the element, equivalent to the `innerText` property in JavaScript.

To identify the type of node, you can check the value of the `type` property.

When calling the `decode()` function with the `with_position` option enabled, both node types will include an additional key called "position." The position dictionary provides the following information:

- **index**: Represents the ordinal index in the source string that corresponds to the start of the HTML element.
- **line**: Specifies the line number in the HTML source where the node is located.
- **column**: Indicates the offset, in terms of columns, from the start of the line in the source.

## Options: Configuring Decode and Encode

The default exported functions `decode()` and `encode()` offer an optional second argument that allows you to customize their behavior. You can pass a dictionary of options to these functions to modify their functionality. Below are the available options:

- `void_tags`: Specifies a list of HTML tags that are considered void elements.
- `closing_tags`: Defines whether or not closing tags should be included in the output.
- `childless_tags`: Indicates a list of HTML tags that do not have any children.
- `tag_ancestors`: Specifies whether to include the ancestors of an HTML tag in the output.
- `with_position`: Enables the inclusion of position information for nodes.

By default, all these options are set to their exported values, adhering to the HTML specification. You can selectively specify options based on your requirements. Remember that when providing options, they are merged with the default values to determine the final configuration. Omitting options will keep their default behavior.

> Note: This applies to any function within the module that accepts an `options` argument.

## Properties

- **name2codepoint** &#8674; _dict_: Dictionary of HTML entity name to the Unicode code point
- **html5** &#8674; _dict_: Dictionary of HTML5 named character references to the equivalent Unicode character(s).
- **codepoint2name** &#8674; _dict_: Dictionary of Unicode code point to the HTML entity name
- **entitydefs**: Dictionary of HTML entity name to the character
(or a character reference if the character is outside the Latin-1 range)
- **childless\_tags** &#8674; _readonly_ _list_: Tags which contain arbitary non-parsed content
For example: `<script>` JavaScript should not be parsed
- **closing\_tags** &#8674; _readonly_ _list_: Tags which auto-close because they cannot be nested
For example: `<p>Outer<p>Inner is <p>Outer</p><p>Inner</p>`
- **tag\_ancestors** &#8674; _readonly_ _list_: Closing tags which have ancestor tags which may exist within
them which prevent the closing tag from auto-closing.
For example: in `<li><ul><li></ul></li>`, the top-level `<li>`
should not auto-close.
- **void\_tags** &#8674; _readonly_ _list_: Tags which do not need the closing tag
For example: `<img>` does not need `</img>`.

## Functions

#### decode(str, options)

Decodes an HTML string into a list of nodes (described above) 
representing the structure of the HTML document.

The _options_ argument is an optional argument that allows the caller 
to modify how HTML is decoded using one or more of the HTML options 
described above. For example, one can pass the `void_tags` option to 
declare a custom tag as self-closing and thus avoid an error from not 
closing such tags.

Example,

```blade
import html
echo html.decode('<p>Hello World!</p>')
```

The code above should output the following:

```
[{type: element, name: p, attributes: [], children: [{type: text, content: Hello World!}]}]
```

You can include information about the position of the node in the source by setting the 
`with_position` option to `true`.

For example:

```blade
import html
echo html.decode('<img>', {with_position: true})
```

The code should output the nodes with the position information.

```
[{type: element, name: img, attributes: [], children: [], position: {start: {index: 0, line: 1, column: 1}, end: {index: 5, line: 1, column: 6}}}]
```
##### Parameters

- _string_ **str**
- _dict?_ **options**

##### Returns

- list



#### encode(nodes, options)

Encodes the list of `elements` into an HTML string.

The _options_ argument is an optional argument that allows the caller 
to modify how HTML is encoded using one or more of the HTML options 
described above. For example, one can pass the `void_tags` option to 
declare a custom tag as self-closing.
##### Parameters

- _list_ **nodes**
- _dict?_ **options**

##### Returns

- string



