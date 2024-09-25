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

