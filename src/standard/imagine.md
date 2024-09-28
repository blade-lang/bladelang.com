# imagine

## Properties

- **QUANT\_DEFAULT**: QUANT_LIQ if libimagequant is available, QUANT_JQUANT otherwise.
- **QUANT\_JQUANT**: libjpeg's old median cut. Fast, but only uses 16-bit color.
- **QUANT\_NEUQUANT**: NeuQuant - approximation using Kohonen neural network.
- **QUANT\_LIQ**: A combination of algorithms used in libimagequant aiming for the highest quality at cost of speed.
- **ARC\_ARC**: Produces a rounded edge.
- **ARC\_PIE**: Same as ARC_ARC.
- **ARC\_CHORD**: Connects the starting and ending angles with a straight line.
- **ARC\_NO\_FILL**: Indicates that the arc or chord should be outlined, not filled.
- **ARC\_NO\_EDGE**: Used together with ARC_NO_FILL, indicates that the beginning and 
ending angles should be connected to the center; this is a good 
way to outline (rather than fill) a 'pie slice'.
- **CROP\_DEFAULT**: Same as CROP_TRANSPARENT
- **CROP\_TRANSPARENT**: Crop using the transparent color
- **CROP\_BLACK**: Crop black borders
- **CROP\_WHITE**: Crop white borders
- **CROP\_SIDES**: Crop using colors of the 4 corners
- **CMP\_IMAGE**: Actual image IS different
- **CMP\_NUM\_COLORS**: Number of colors in pallette differ
- **CMP\_COLOR**: Image colors differ
- **CMP\_SIZE\_X**: Image width differs
- **CMP\_SIZE\_Y**: Image heights differ
- **CMP\_TRANSPARENT**: Transparent color differs
- **CMP\_BACKGROUND**: Background color differs
- **CMP\_INTERLACE**: Interlaced setting differs
- **CMP\_TRUECOLOR**: Truecolor vs palette differs
- **BLUR\_SELECTIVE**: Blurs the image using the Gaussian method.
- **BLUR\_GAUSSIAN**: Blurs the image.
- **FLIP\_BOTH**: Flip an image vertically and horizontally
- **FLIP\_HORIZONTAL**: Flip an image horizontally
- **FLIP\_VERTICAL**: Flip an image vertically
- **FONT\_SMALL**: A small ISO-8859-2 raster font (5x8 pixels).
- **FONT\_REGULAR**: The regular ISO-8859-2 raster font (6x13 pixels)
- **FONT\_MEDIUM**: A medium bold ISO-8859-2 raster font (7x13 pixels).
- **FONT\_LARGE**: A large ISO-8859-2 raster font (8x16 pixels).
- **FONT\_EXTRALARGE**: An extra-large ISO-8859-2 raster font (9x15 pixels).
- **COLOR\_STYLED**: Use the current style, see `set_style()`
- **COLOR\_BRUSHED**: Use the current brush, see `set_brush()`
- **COLOR\_STYLED\_BRUSHED**: Use the current style and brush
- **COLOR\_TILED**: Use the current tile, see `set_tile()`
- **COLOR\_TRANSPARENT**: Indicate transparency, what is not the same as the transparent 
color index; used for lines only
- **COLOR\_ANTI\_ALISED**: Draw anti aliased
- **INTERP\_DEFAULT**: Bell
- **INTERP\_BELL**: Bell
- **INTERP\_BESSEL**: Bessel
- **INTERP\_BILINEAR\_FIXED**: fixed point bilinear
- **INTERP\_BICUBIC**: Bicubic
- **INTERP\_BICUBIC\_FIXED**: fixed point bicubic integer
- **INTERP\_BLACKMAN**: Blackman
- **INTERP\_BOX**: Box
- **INTERP\_BSPLINE**: BSpline
- **INTERP\_CATMULLROM**: Catmullrom
- **INTERP\_GAUSSIAN**: Gaussian
- **INTERP\_GENERALIZED\_CUBIC**: Generalized cubic
- **INTERP\_HERMITE**: Hermite
- **INTERP\_HAMMING**: Hamming
- **INTERP\_HANNING**: Hannig
- **INTERP\_MITCHELL**: Mitchell
- **INTERP\_NEAREST\_NEIGHBOUR**: Nearest neighbour interpolation
- **INTERP\_POWER**: Power
- **INTERP\_QUADRATIC**: Quadratic
- **INTERP\_SINC**: Sinc
- **INTERP\_TRIANGLE**: Triangle
- **INTERP\_WEIGHTED4**: 4 pixels weighted bilinear interpolation
- **INTERP\_LINEAR**: bilinear interpolation
- **LANCZOS3**: Lanczos 3
- **LANCZOS8**: Lanczos 8
- **BLACKMAN\_BESSEL**: Blackman Bessel
- **BLACKMAN\_SINC**: Blackman Sinc
- **QUADRATIC\_BSPLINE**: Quadratic BSpline
- **CUBIC\_SPLINE**: Cubic Spline
- **COSINE**: Cosine
- **WELSH**: Welsh

## Functions

#### true\_color(r, g, b, a)

Compose a truecolor value from its components.

 @param {number?} r - The red channel (0-255) - Default: 0
 @param {number?} g - The green channel (0-255) - Default: 0
 @param {number?} b - The blue channel (0-255) - Default: 0
 @param {number?} a - The alpha channel (0-127, where 127 is 
     fully transparent, and 0 is completely opaque) 
     - Default: 0.
##### Returns

- {number}



#### decompose(color)

Decomposes an Image true color number into it's respective 
RGBA components.

The function returns a dictionary that contains the following 
decomposed items:

- `r` - The red channel value
- `g` - The green channel value
- `b` - The blue channel value
- `a` - The alpha channel value
##### Parameters

- _{number}_ **color**

##### Returns

- {dict}



## Classes

### _class_ ImageResource

The ImageResource class represents a loaded image and exposes all 
the image processing, metadata and manipulation functions.

#### Methods

#### use(callback)

Invokes the given callback with the image as a parameter and 
automatically closes the image once the callback returns. 
Leaving images in open can quickly lead to resource exhaustion 
especially when working with multiple images. The `use()` 
method is recommended over manually closing images as it 
ensures that an image is always closed and not forgotten in 
memory.
##### Parameters

- _{function(1)}_ **callback**


#### close()

Closes an image and frees all associated resources.
##### Notes

- an image can no longer be used once it is closed.

#### meta()

Returns metadata information about the image.

Metadata contains:
- `width`: The width of the image (in pixels).
- `height`: The height of the image (in pixels).
- `colors`: The number of colors in the image.
- `res_x`: The horizontal resolution in DPI.
- `res_y`: The vertical resolution in DPI.
- `interpolation`: The method of interpolation used on the image.
- `true_color`: True if the image uses true colors, false otherwise.
- `interlaced`: True if the image is interlaced, false otherwise.
##### Returns

- {dict}

#### set\_pixel(x, y, color)

Sets the pixel indicated by _x_ and _y_ coordinate in the image to 
the given _color_.
##### Parameters

- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **color**


#### get\_pixel(x, y)

Returns the color at the give pixel indicated by _x_ and _y_ 
coordinate in the image.
##### Parameters

- _{number}_ **x**
- _{number}_ **y**

##### Returns

- {number}

#### line(x1, y1, x2, y2, color)

Draws a line between x1,y1 and x2, y2.The line is drawn using 
the color index specified. Note that color index can be a color 
returned by `allocate_color()` or one of `set_style()`, or
`set_brush()`.
##### Parameters

- _{number}_ **x1**
- _{number}_ **y1**
- _{number}_ **x2**
- _{number}_ **y2**
- _{number}_ **color**


#### dashed\_line(x1, y1, x2, y2, color)

Draws a dashed line between x1,y1 and x2, y2.The line is drawn using 
the color specified. Note that color index can be a color returned 
by `allocate_color()` or one of `set_style()`, or `set_brush()`.
##### Parameters

- _{number}_ **x1**
- _{number}_ **y1**
- _{number}_ **x2**
- _{number}_ **y2**
- _{number}_ **color**


#### rectangle(x1, y1, x2, y2, color)

Draws a rectangle with the upper left (x1, y1) then lower right (y1,y2) 
corners specified, using the color specified.
##### Parameters

- _{number}_ **x1**
- _{number}_ **y1**
- _{number}_ **x2**
- _{number}_ **y2**
- _{number}_ **color**


#### filled\_rectangle(x1, y1, x2, y2, color)

Draws a solid rectangle with the upper left (x1, y1) then lower 
right (y1,y2) corners specified, using the color specified.
##### Parameters

- _{number}_ **x1**
- _{number}_ **y1**
- _{number}_ **x2**
- _{number}_ **y2**
- _{number}_ **color**


#### safe\_bound(x, y)

Returns true if the coordinate represented by _x_ and _y_ 
is within the bounds of the image.
##### Parameters

- _{number}_ **x**
- _{number}_ **y**


#### char(x, y, char, font, color)

Draws a single character.
##### Parameters

- _{number}_ **x**: - The x coordinate of the upper left pixel.
- _{number}_ **y**: - The y coordinate of the upper left pixel.
- _{char}_ **text**: - The character.
- _{font}_ **font**: - The raster font.
- _{number}_ **color**: - The color.


#### char\_vert(x, y, char, font, color)

Draws a single character vertically.
##### Parameters

- _{number}_ **x**: - The x coordinate of the upper left pixel.
- _{number}_ **y**: - The y coordinate of the upper left pixel.
- _{char}_ **text**: - The character.
- _{font}_ **font**: - The raster font.
- _{number}_ **color**: - The color.


#### string(x, y, text, font, color)

Draws a character string.
##### Parameters

- _{number}_ **x**: - The x coordinate of the upper left pixel.
- _{number}_ **y**: - The y coordinate of the upper left pixel.
- _{string}_ **text**: - The character string.
- _{font}_ **font**: - The raster font.
- _{number}_ **color**: - The color.


#### string\_vert(x, y, text, font, color)

Draws a character string vertically.
##### Parameters

- _{number}_ **x**: - The x coordinate of the upper left pixel.
- _{number}_ **y**: - The y coordinate of the upper left pixel.
- _{string}_ **text**: - The character string.
- _{font}_ **font**: - The raster font.
- _{number}_ **color**: - The color.


#### polygon(points, color)

Draws a polygon with the vertices specified by _points_, in the 
specified by _color_. There must be at least three points.

Point must be a list of lists where each list contains two numbers 
for the x and y coordinates. It is required that there must be at 
least three points.
##### Parameters

- _{list[list]}_ **points**
- _{number}_ **color**


#### open\_polygon(points, color)

Draws an open polygon with the vertices specified by _points_, in 
the specified by _color_. There must be at least three points.

Point must be a list of lists where each list contains two numbers 
for the x and y coordinates. It is required that there must be at 
least three points.
##### Parameters

- _{list[list]}_ **points**
- _{number}_ **color**


#### filled\_polygon(points, color)

Fills a polygon with the vertices specified by _points_, in the 
specified by _color_. There must be at least three points.

Point must be a list of lists where each list contains two numbers 
for the x and y coordinates. It is required that there must be at 
least three points.
##### Parameters

- _{list[list]}_ **points**
- _{number}_ **color**


#### arc(x, y, width, height, start, end, color)

Draws a partial ellipse centered at the given point, with the 
specified width and height in pixels. The arc begins at the 
position in degrees specified by _start_ and ends at the 
position specified by _end_. The arc is drawn in the color 
specified by the last argument. A circle can be drawn by 
beginning from 0 degrees and ending at 360 degrees, with width 
and height being equal. `end` must be greater than `start`. 
Values greater than 360 are interpreted modulo 360.
##### Parameters

- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **width**
- _{number}_ **height**
- _{number}_ **start**
- _{number}_ **end**
- _{number}_ **color**


#### filled\_arc(x, y, width, height, start, end, color, style)

Fills a partial ellipse centered at the given point, with the 
specified width and height in pixels using the specified style. 
The arc begins at the position in degrees specified by _start_ 
and ends at the position specified by _end_. The arc is drawn 
in the color specified by the last argument. A circle can be 
drawn by beginning from 0 degrees and ending at 360 degrees, 
with width and height being equal. `end` must be greater than 
`start`. Values greater than 360 are interpreted modulo 360. 

Style must be one or more of ARC_ constants or'ed together.
 E.g. `ARC_NO_FILL | ARC_NO_EDGE`.

When style is not given, it defaults to `ARC_PIE`.
##### Parameters

- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **width**
- _{number}_ **height**
- _{number}_ **start**
- _{number}_ **end**
- _{number}_ **color**
- _{number}_ **style**


#### ellipse(x, y, width, height, color)

Draws a full ellipse centered at the given point, with the 
specified width, height, and color.
##### Parameters

- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **width**
- _{number}_ **height**
- _{number}_ **color**


#### filled\_ellipse(x, y, width, height, color)

Fills a full ellipse centered at the given point, with the 
specified width, height, and color.
##### Parameters

- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **width**
- _{number}_ **height**
- _{number}_ **color**


#### allocate\_color(r, g, b, a)

Returns the given color allocated from the image palette. 
Any of R, G, B, or A can be omitted or set to nil in which case 
they'll default to zero.
##### Parameters

- _{number?}_ **r**
- _{number?}_ **g**
- _{number?}_ **b**
- _{number?}_ **a**

##### Returns

- {number}

#### closest\_color(r, g, b, a)

Returns the closes color based on the image to the color specified by 
`r`, `g`, `b`, and `a`. A slightly different color with the same 
transparency beats the exact same color with radically different 
transparency.
##### Parameters

- _{number}_ **r**
- _{number}_ **g**
- _{number}_ **b**
- _{number}_ **a**

##### Returns

- {number}

#### closest\_color\_hwb(r, g, b)

Same as `closes_color()` but uses an alternative algorithm and does 
not account for transparency.
##### Parameters

- _{number}_ **r**
- _{number}_ **g**
- _{number}_ **b**

##### Returns

- {number}

#### exact\_color(r, g, b, a)

Returns an exact match only, including alpha when specified.
##### Parameters

- _{number}_ **r**
- _{number}_ **g**
- _{number}_ **b**
- _{number}_ **a**

##### Returns

- {number}

#### resolve\_color(r, g, b, a)

Resolves color in the image based on `exact_color()` and `closest_color()` 
and return the one that matches the image best.
##### Parameters

- _{number}_ **r**
- _{number}_ **g**
- _{number}_ **b**
- _{number}_ **a**

##### Returns

- {number}

#### deallocate\_color(color)

Deallocates a color previously allocated from the image.
##### Parameters

- _{number}_ **color**


#### color\_transparent(color)

Specifies a color index (if a palette image) or an RGB color (if a 
truecolor image) which should be considered 100% transparent. FOR 
TRUECOLOR IMAGES, THIS IS IGNORED IF AN ALPHA CHANNEL IS BEING SAVED. 
Use `save_apha(false)` to turn off the saving of a full alpha 
channel in a truecolor image. Note that this function is usually 
compatible with older browsers that do not understand full alpha 
channels well.
##### Parameters

- _{number}_ **color**


#### palette\_copy(image)

Copies the palatte from a paletted image to this image.
##### Parameters

- _{ImageResource}_ **image**


#### color\_replace(src, dest)

Replaces every occurrence of color _src_ in the image with the 
color _dest_.
##### Parameters

- _{number}_ **src**
- _{number}_ **dest**

##### Returns

- {bool}

#### fill(x, y, color)

Flood fills the image with the given _color_ starting are 
the coordinates given by _x_ and _y_.
##### Parameters

- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **color**


#### fill\_to\_border(x, y, border, color)

Flood fills the image with the given _color_ starting are 
the coordinates given by _x_ and _y_ and using the color 
specified by border to fill its borders.
##### Parameters

- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **color**


#### copy(src, dst_x, dst_y, src_x, src_y, width, height)

Copy a part of image _src_ onto this image starting at the x,y c
oordinates src_x, src_y with the source width and height. The 
portion defined will be copied onto the x,y coordinates, dst_x 
and dst_y.
##### Parameters

- _{ImageResource}_ **src**
- _{number}_ **dst_x**
- _{number}_ **dst_y**
- _{number}_ **src_x**
- _{number}_ **src_y**
- _{number}_ **width**
- _{number}_ **height**


#### copy\_merge(src, dst_x, dst_y, src_x, src_y, width, height, pct)

Copy and merge a part of image _src_ onto this image starting 
at the x,y coordinates src_x, src_y with the source width and 
height. The portion defined will be copied onto the x,y 
coordinates, dst_x and dst_y.

The two images will be merged according to pct which can range 
from 0 to 100. When pct = 0, no action is taken, when 100 this 
function behaves identically to `copy()` for pallete images, 
except for ignoring alpha components, while it implements 
alpha transparency for true colour images.
##### Parameters

- _{ImageResource}_ **src**
- _{number}_ **dst_x**
- _{number}_ **dst_y**
- _{number}_ **src_x**
- _{number}_ **src_y**
- _{number}_ **width**
- _{number}_ **height**
- _{number}_ **pct**


#### copy\_merge\_gray(src, dst_x, dst_y, src_x, src_y, width, height, pct)

Same as `copy_merge()` except that when merging it preserves the 
hue of the source by converting the destination pixels to gray scale 
before the copy operation.
##### Parameters

- _{ImageResource}_ **src**
- _{number}_ **dst_x**
- _{number}_ **dst_y**
- _{number}_ **src_x**
- _{number}_ **src_y**
- _{number}_ **width**
- _{number}_ **height**
- _{number}_ **pct**


#### copy\_resized(src, x, y, src_x, src_y, width, height, src_width, src_height)

Copy a resized area defined by src_x, src_y, src_width, and 
src_height from the image _src_ to the area defined by x, y, 
width, height on this image.

If the source and destination coordinates and width and heights 
differ, appropriate stretching or shrinking of the image fragment
will be performed. 

The coordinates refer to the upper left corner. 

This function can be used to copy regions within the same image 
(if this image is the same as _src_) but if the regions overlap 
the results will be unpredictable.
##### Parameters

- _{ImageResource}_ **src**
- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **src_x**
- _{number}_ **src_y**
- _{number}_ **width**
- _{number}_ **height**
- _{number}_ **src_width**
- _{number}_ **src_height**


#### copy\_resampled(src, x, y, src_x, src_y, width, height, src_width, src_height)

Copy a resized area defined by src_x, src_y, src_width, and 
src_height from the image _src_ to the area defined by x, y, 
width, height on this image. Unlike `copy_resized()`, it 
smoothly interpolates pixel values so that, in particular, 
reducing the size of an image still retains a great deal of 
clarity.

If the source and destination coordinates and width and heights 
differ, appropriate stretching or shrinking of the image fragment
will be performed. 

The coordinates refer to the upper left corner. 

This function can be used to copy regions within the same image 
(if this image is the same as _src_) but if the regions overlap 
the results will be unpredictable.
##### Parameters

- _{ImageResource}_ **src**
- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **src_x**
- _{number}_ **src_y**
- _{number}_ **width**
- _{number}_ **height**
- _{number}_ **src_width**
- _{number}_ **src_height**


#### copy\_rotated(src, x, y, src_x, src_y, src_width, src_height, angle)

Similar to `copy_resized()` with an added rotation to the copied image. 
Destination is the _center_ of the rotated copy. Angle is in degrees, 
same as `arc()`. 

Floating point destination center coordinates allow accurate rotation of 
objects of odd-numbered width or height.

The rotation angle is interpreted as the number of degrees to rotate the 
image anticlockwise.
##### Parameters

- _{ImageResource}_ **src**
- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **src_x**
- _{number}_ **src_y**
- _{number}_ **src_width**
- _{number}_ **src_height**
- _{number}_ **angle**


#### clone()

Clones this image resource.
##### Returns

- {ImageResource}

#### set\_brush(brush)

Sets the brush image to be used by all line drawing functions for 
this image.

A "brush" is an image used to draw wide, shaped strokes in another image. 
Just as a paintbrush is not a single point, a brush image need not be a 
single pixel. Any image resource can be used as a brush, and by setting 
the transparent color index of the brush image with `color_transparent()`, 
a brush of any shape can be created. 

All line-drawing functions, such as gdImageLine and `polygon()`, will use 
the current brush if the special "color" `COLOR_BRUSHED` or 
`COLOR_STYLED_BRUSHED` is used when calling them.

>*NOTE:** 
 > 
> You need not take special action when you are finished with a 
> brush, but if you close the brush image (or let the GC close it), 
> you must not use the `COLOR_BRUSHED` or `COLOR_STYLED_BRUSHED` colors 
> until you have set a new brush image.
##### Parameters

- _{ImageResource}_ **brush**


#### set\_tile(tile)

Sets the tile image to be used by all region filling functions.

A tile is an image used to fill an area with a repeated pattern. Any image 
resource can be used as a tile, and by setting the transparent color index 
of the tile image with `color_transparent()`, a tile that allows certain 
parts of the underlying area to shine through can be created. All 
region-filling functions, such as `fill()` and `filled_polygon()`, will use 
the current tile if the special "color" `COLOR_TILED` is used when calling 
them.

You can set any image resource to be the tile. If the tile image does not have 
the same color map as the first image, any colors missing from the first image 
will be allocated. If not enough colors can be allocated, the closest colors 
already available will be used. This allows arbitrary GIFs to be used as tile 
images. It also means, however, that you should not set a tile unless you will 
actually use it; if you set a rapid succession of different tile images, you can 
quickly fill your color map, and the results will not be optimal.

You need not take any special action when you are finished with a tile. As for 
any other image, if you will not be using the tile image for any further purpose, 
you should call `close()`. You must not use the color `COLOR_TILED` if the current 
tile has been closed; you can of course set a new tile to replace it.
##### Parameters

- _{ImageResource}_ **tile**


#### set\_antialiased(color, dont_blend)

Set the color for subsequent anti-aliased drawing and whether to blend the 
color or not.
##### Parameters

- _{number}_ **color**
- _{bool}_ **dont_blend**


#### set\_thickness(thickness)

Sets the thickness in pixels for following lines drawn when drawing lines, 
ellipses, rectangles, polygons and so forth.
##### Parameters

- _{number}_ **thickness**


#### interlace(enable)

Sets whether an image is interlaced. If the `enabled` parameter is not 
given, it defaults to true.
##### Parameters

- _{bool?}_ **enable**


#### alpha\_blending(enable)

Toggles between two different blending modes of drawing on truecolor images. 

In blending mode, the alpha channel component of the color supplied to all 
drawing function, such as `set_pixel()` determines how much of the underlying 
color should be allowed to shine through. As a result, the module 
automatically blends the existing color at that point with the drawing color, 
and stores the result in the image. The resulting pixel is opaque. 

In non-blending mode, the drawing color is copied literally with its alpha 
channel information, replacing the destination pixel. Blending mode is not 
available when drawing on palette images.

If the `enabled` parameter is not given, it defaults to true.
##### Parameters

- _{bool}_ **enable**


#### flip(mode)

Flips the image horizontally, vertically, or in both direction as specified 
in mode. `mode` must be one of the `FLIP_` constants. When no mode is set, 
 mode defaults to `FLIP_BOTH`.
##### Parameters

- _{number?}_ **mode**


#### crop(x, y, width, height)

Returns a new imaged cropped from the rectangular area specified by x, y, 
width, and height in this image.
##### Parameters

- _{number}_ **x**
- _{number}_ **y**
- _{number}_ **width**
- _{number}_ **height**

##### Returns

- {ImageResource}

#### auto\_crop(mode)

Crop an image automatically using one of the `CROP_` modes. If `mode` 
 is not give, it defaults to `CROP_DEFAULT`.
##### Parameters

- _{number?}_ **mode**

##### Returns

- {ImageResource}

#### scale(width, height, method)

Scale an image using the given new width and height with the 
interpolation algorithm. If height is not given, the height 
will be automatcially calculated from the new width to maitain 
aspect ratio. 

If the interpolation method is not given, it defaults to 
`INTERP_BILINEAR_FIXED`.

This method returns a new image rather than modify this image.
##### Parameters

- _{number}_ **width**
- _{number?}_ **height**
- _{number?}_ **method**

##### Returns

- {ImageResource}

#### rotate(angle, bg_color, method)

Creates a new image rotated counter-clockwise by the requested angle using 
the given interpolation method.  Non-square angles will add a border with 
bgcolor.
##### Parameters

- _{number}_ **angle**
- _{number}_ **bg_color**
- _{number?}_ **method**

##### Returns

- {ImageResource}

#### save\_alpha(save)

Sets the save alpha flag

The save alpha flag specifies whether the alpha channel of the pixels should
be saved. This is supported only for image formats that support full alpha
transparency, e.g. PNG.
##### Parameters

- _{bool}_ **save**


#### pixelate(block_size, mode)

Applies pixelation effect to the image based on the block 
size and given effect mode.
##### Parameters

- _{number}_ **block_size**
- _{number}_ **mode**


#### scatter(sub, plus, colors)

Applies scatter effect to an image using the _sub_ and _plus_ to 
control the strength of the scatter and colors to indicate the 
colors it should be restricted to.
##### Parameters

- _{number}_ **sub**
- _{number}_ **plus**
- _{list<number>}_ **colors**


#### smooth(weight)

Makes an image smooter based on the specified weight. If 
weight is not given, it defaults to `1`.
##### Parameters

- _{number}_ **weight**


#### mean\_removal()

Uses mean removal to achieve a "sketchy" effect.

#### emboss()

Embosses the image.

#### blur(type)

Applies a blur to the image. If the type is not given, a 
Guassian blur will be applied.
##### Parameters

- _{number}_ **type**


#### detect\_edge()

Uses edge detection to highlight the edges in the image.

#### grayscale()

Converts the image into grayscale by changing the red, green 
and blue components to their weighted sum using the same 
coefficients as the REC.601 luma (Y') calculation. The alpha 
components are retained. For palette images the result may 
differ due to palette limitations.

#### negate()

Reverses all colors of the image to create a negative image.

#### color(r, g, b, a)

Same as `grayscale()` except this allows you to specify the 
output color.
##### Parameters

- _{number}_ **r**
- _{number}_ **g**
- _{number}_ **b**
- _{number}_ **a**


#### contrast(contrast)

Changes the contrast of the image based on the level set 
in _contrast_.
##### Parameters

- _{number}_ **contrast**


#### brightness(brightness)

Changes the brightness of the image based on the level set 
in _brightness_.
##### Parameters

- _{number}_ **brightness**


#### set\_clip(x1, y1, x2, y2)

Sets the rectangular clipping region beyond which no pixels 
will be drawn in the image.
##### Parameters

- _{number}_ **x1**
- _{number}_ **y1**
- _{number}_ **x2**
- _{number}_ **y2**


#### get\_clip()

Returns the clipping region in the image. See `set_clip()`.

The function returns a list containing four numbers that 
indicates the x1, y1, x2, and y2 of the clipping region in 
the image.
##### Returns

- {list<number>}

#### set\_resolution(res_x, res_y)

Sets the resolution of the the image across both axis.
##### Parameters

- _{number}_ **res_x**
- _{number}_ **res_y**


#### true\_color\_to\_palette(dither, colors_wanted)

Convert a true color image to a palette image. 

The first parameter `dither` controls whether the image 
should be dithered which results in a more speckled image but 
with better color approximation. 

The second argument `colors_wanted` controls the number of 
colors that should be kept in the palette.
##### Parameters

- _{bool}_ **dither**
- _{number}_ **colors_wanted**

##### Returns

- {bool} - `true` if successful, otherwise `false`.

#### palette\_to\_true\_color()

Converts a palette based image to true color.
##### Returns

- {bool} - `true` if successful, otherwise `false`.

#### match\_color(image)

Makes the colors of the palette version of an image more closely 
match the true color version. This function should be given a 
true color image as the function will attempt to make the color 
of the image given if the current image is a paletted image.
##### Parameters

- _{ImageResource}_ **image**

##### Returns

- {bool} - `true` if successful, otherwise `false`.

#### compare(image)

Check whether two images are idential.

This check includes a size, transparency, interlace, color profile, 
and a pixel by pixel check.

If the images are completely identical, the method returns a zero 
(`0`). Otherwise, it returns a number greater than 0. The number 
returned can be tested againt the various `CMP_` constants to test 
 for any of the conditions.

For example,

```blade
var result = image1.compare(image2)

var both_transparent = !(result & CMP_TRANSPARENT)
var same_width = !(result & CMP_SIZE_X)
```
##### Parameters

- _{ImageResource}_ **image**

##### Returns

- {number}

#### export\_png(dest, quality)

Saves the image to file with the PNG format.

Quality level: 0-10, where 9 is NO COMPRESSION at all,
9 is FASTEST but produces larger files, 0 provides the best
compression (smallest files) but takes a long time to compress, and
10 selects the default compiled into the zlib library.
##### Parameters

- _{string|file}_ **dest**
- _{number}_ **quality**


#### export\_jpeg(dest, quality)

Saves the image to file with the JPEG format.

Quality level: 100 is highest quality (there is always 
a little loss with JPEG). 0 is lowest. 10 is about the 
lowest useful setting.
##### Parameters

- _{string|file}_ **dest**
- _{number}_ **quality**


#### export\_bmp(dest, quality)

Saves the image to file with the BMP format.

Quality level: 100 is highest quality (there is always 
a little loss with BMP). 0 is lowest. 10 is about the 
lowest useful setting.
##### Parameters

- _{string|file}_ **dest**
- _{number}_ **quality**


#### export\_wbmp(dest, foreground)

Saves the image to file with the WBMP format using the 
given foreground color.
##### Parameters

- _{string|file}_ **dest**
- _{number}_ **foreground**


#### export\_webp(dest, quantization)

Saves the image to file with the WEBP format using the 
given quantization.
##### Parameters

- _{string|file}_ **dest**
- _{number}_ **quantization**


#### export\_tiff(dest)

Saves the image to file with the TIFF format.
##### Parameters

- _{string|file}_ **dest**


#### export\_avif(dest, quality, speed)

Saves the image to file with the JPEG format.

Quality level: 100 is highest quality (there is always 
a little loss with JPEG). 0 is lowest. 10 is about the 
lowest useful setting.
##### Parameters

- _{string|file}_ **dest**
- _{number}_ **quality**
- _{number}_ **speed**: - Default = 1


#### get\_pointer()

Returns the raw image resource pointer.
##### Returns

- {ptr}



### _class_ Image

The Image class is allows creating and opening of imnages in 
any of the supported formats which includes `JPEG`, `PNG`, 
`GIF`, `TIFF`, `BMP`, `WBMP`, `TGA`, `WEBP`, `AVIF`.

#### Methods

#### new(width, height, use_true_colors)

Creates a palette-based image (up to 256 colors) or a truecolor 
image (millions of colors) when `use_true_colors` is set to true.
##### Parameters

- _{number}_ **width**
- _{number}_ **height**
- _{bool?}_ **use_true_colors**

##### Returns

- {ImageResource}

#### from\_png(src)

Creates an image from a PNG file. Truecolor PNG stays truecolor; 
palette PNG stays palette-based.
##### Parameters

- _{string|file}_ **src**

##### Returns

- {ImageResource}

#### from\_jpeg(src)

Creates an image from a JPEG file.
JPEG is always truecolor.
##### Parameters

- _{string|file}_ **src**

##### Returns

- {ImageResource}

#### from\_gif(src)

Creates an image from a GIF file.
##### Parameters

- _{string|file}_ **src**

##### Returns

- {ImageResource}

#### from\_bmp(src)

Creates an image from a BMP file.
##### Parameters

- _{string|file}_ **src**

##### Returns

- {ImageResource}

#### from\_wbmp(src)

Creates an image from a WBMP file.
##### Parameters

- _{string|file}_ **src**

##### Returns

- {ImageResource}

#### from\_tga(src)

Creates an image from a TGA file.
##### Parameters

- _{string|file}_ **src**

##### Returns

- {ImageResource}

#### from\_tiff(src)

Creates an image from a TIFF file.
##### Parameters

- _{string|file}_ **src**

##### Returns

- {ImageResource}

#### from\_webp(src)

Creates an image from a WEBP file.
##### Parameters

- _{string|file}_ **src**

##### Returns

- {ImageResource}

#### from\_avif(src)

Creates an image from a AVIF file.
##### Parameters

- _{string|file}_ **src**

##### Returns

- {ImageResource}

#### from\_file(src)

Creates an image from any supported image file.
As long as the file type is supported by Imagine,
the file type will automatically be detected.
##### Parameters

- _{string|file}_ **src**

##### Returns

- {ImageResource}



