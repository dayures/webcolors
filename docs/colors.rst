.. _colors:


An overview of colors on the Web
================================

Colors on the Web are specified in `the sRGB color space`_, where each
color is made up of a red component, a green component and a blue
component. This maps (fairly) cleanly to the red, green and blue
components of pixels on a computer display, and to the cone cells of a
human eye, which come in three sets roughly corresponding to the
wavelengths of light associated with red, green and blue.


HTML 4
------

HTML 4 defined `two ways to specify sRGB colors`_:

* A hash mark ('#') followed by three pairs of hexdecimal digits,
  specifying values for red, green and blue components in that order;
  for example, ``#0099cc``. Since each pair of hexadecimal digits can
  express 256 different values, this allows up to 256**3 or 16,777,216
  unique colors to be specified (though, due to differences in display
  technology, not all of these colors may be clearly distinguished on
  any given physical display).

* A set of predefined color names which correspond to specific
  hexadecimal values; for example, ``blue``. HTML 4 defines sixteen
  such colors.


CSS 1
-----

In `its description of color units`_, CSS 1 added
three new ways to specify sRGB colors:

* A hash mark followed by three hexadecimal digits, which is expanded
  into three hexadecimal pairs by repeating each digit; thus ``#09c``
  is equivalent to ``#0099cc``.

* The string "rgb", followed by parentheses, between which are three
  base-10 integers each between 0 and 255, inclusive, which are taken
  to be the values of the red, green and blue components in that
  order; for example, ``rgb(0, 153, 204)``.

* The same as above, except using percentages instead of numeric
  values; for example, ``rgb(0%, 60%, 80%)``.

CSS 1 also suggested a set of sixteen color names. These names were
identical to the set defined in HTML 4, but CSS 1 did not provide
definitions of their values and stated that they were taken from "the
Windows VGA palette".


CSS 2
-----

In its `section on colors`_, CSS 2 allowed the same methods of
specifying colors as CSS 1, and defined and provided values for
sixteen named colors, identical to the set found in HTML 4.

CSS 2 also specified `a list of names of system colors`_. These had no
fixed color values, but would take on values from the operating system
or other user interface, and allowed elements to be styled using the
same colors as the surrounding user interface. These names are
deprecated as of CSS 3.

The CSS 2.1 revision did not add any new methods of specifying sRGB
colors, but did define `one additional named color`_: ``orange``.


CSS 3
-----

`The CSS 3 color module`_ adds one new way to specify colors:

* A hue-saturation-lightness triplet (HSL), using the construct
  ``hsl()``.

CSS 3 also adds support for variable opacity of colors, by allowing
the specification of alpha-channel information through the ``rgba()``
and ``hsla()`` constructs. These are used similarly to the ``rgb()``
and ``hsl()`` constructs, except a fourth value is supplied indicating
the level of opacity from ``0.0`` (completely transparent) to ``1.0``
(completely opaque). Though not technically a color, the keyword
``transparent`` is also made available in lieu of a color value, and
corresponds to ``rgba(0,0,0,0)``.

CSS 3 also defines a new set of color names. This set is taken
directly from `the named colors defined for SVG (Scalable Vector
Graphics)`_ markup, and is a superset of the named colors defined in
CSS 2.1. This set also has significant overlap with traditional X11
color sets as defined by the ``rgb.txt`` file on many Unix and
Unix-like operating systems, though the correspondence is not exact:
the set of X11 colors is not standardized, and the set of CSS 3/SVG
colors contains some definitions which diverge significantly from
customary X11 definitions (for example, CSS 3/SVG's ``green`` is not
equivalent to X11's ``green``; the color which X11 designates
``green`` is designated ``lime`` in CSS 3/SVG).


HTML5
-----

As of the time of writing of this documentation, HTML5 is still under
development, and the latest drafts do not introduce any new methods of
specifying colors. Rather, those drafts deal only with defining
algorithms for parsing six-digit hexadecimal colors and color names.

.. _the sRGB color space: http://www.w3.org/Graphics/Color/sRGB
.. _two ways to specify sRGB colors: http://www.w3.org/TR/html401/types.html#h-6.5
.. _its description of color units: http://www.w3.org/TR/CSS1/#color-units
.. _section on colors: http://www.w3.org/TR/CSS2/syndata.html#color-units
.. _a list of names of system colors: http://www.w3.org/TR/CSS2/ui.html#system-colors
.. _one additional named color: http://www.w3.org/TR/CSS21/changes.html#q2
.. _The CSS 3 color module: http://www.w3.org/TR/css3-color/
.. _the named colors defined for SVG (Scalable Vector Graphics): http://www.w3.org/TR/SVG11/types.html#ColorKeywords


.. _support:

What this module supports
-------------------------

The ``webcolors`` module supports the following methods of specifying
sRGB colors, and conversions between them:

* Six-digit hexadecimal.

* Three-digit hexadecimal.

* Integer ``rgb()`` triplet.

* Percentage ``rgb()`` triplet.

* Varying selections of predefined color names.

The ``webcolors`` module **does not support**:

* The CSS 1 named colors, which did not have defined values.

* The CSS 2 system colors, which did not have fixed values.

* The ``transparent`` keyword, which denotes an effective lack of
  color.

* Opacity/alpha-channel information specified via ``rgba()`` triplets.

* Colors specified in the HSL color space, via ``hsl()`` or ``hsla()``
  triplets.

If you need to convert between sRGB-specified colors and HSL-specified
colors, or colors specified via other means, consult `the colorsys
module`_ in the Python standard library, which can perform conversions
amongst several common color systems.

.. _the colorsys module: http://docs.python.org/library/colorsys.html