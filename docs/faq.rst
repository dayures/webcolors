.. _faq:

Frequently asked questions
==========================

The following notes answer common questions, and may be useful to you
when using ``webcolors``.


How closely does this module follow the standards?
--------------------------------------------------

As closely as is practical (see below regarding floating-point
values), within :ref:`the supported formats <support>`; the
``webcolors`` module was written with the relevant standards documents
close at hand. See :ref:`the conformance documentation <conformance>`
for details.


Why aren't ``rgb_to_rgb_percent()`` and ``rgb_percent_to_rgb()`` precise?
-------------------------------------------------------------------------

This is due to limitations in the representation of floating-point
numbers in programming languages. Python, like many programming
languages, uses `IEEE floating-point
<http://en.wikipedia.org/wiki/IEEE_floating_point>`_, which is
inherently imprecise for some values.

This imprecision only appears when converting between integer and
percentage ``rgb()`` triplets, and only when an integer value converts
to a non-integer percentage.

To work around this, some common values (255, 128, 64, 32, 16 and 0)
are handled as special cases, with hard-coded precise results. For all
other values, conversion to percentage ``rgb()`` triplet uses a
standard Python ``float``, rounding the result to two decimal places.

See :ref:`the conformance documentation <conformance>` for details on
how this affects testing.


Why aren't HSL values supported?
--------------------------------

In the author's experience, actual use of HSL values on the Web is
extremely rare; the overwhelming majority of all colors used on the
Web are specified using sRGB, through hexadecimal color values or
through integer or percentage ``rgb()`` triplets. This decreases the
importance of supporting the ``hsl()`` construct.

Additionally, Python already has `the colorsys module`_ in the
standard library, which offers functions for converting between RGB,
HSL, HSV and YIQ color systems. If you need conversion to/from HSL or
another color system, use ``colorsys``.

.. _the colorsys module: http://docs.python.org/library/colorsys.html


How am I allowed to use this module?
------------------------------------

The ``webcolors`` module is distributed under a `three-clause BSD
license <http://opensource.org/licenses/BSD-3-Clause>`_. This is an
open-source license which grants you broad freedom to use,
redistribute, modify and distribute modified versions of
``webcolors``. For details, see the file ``LICENSE`` in the source
distribution of ``webcolors``.

.. _three-clause BSD license: http://opensource.org/licenses/BSD-3-Clause


I found a bug or want to make an improvement!
---------------------------------------------

The canonical development repository for ``webcolors`` is online at
<https://github.com/ubernostrum/webcolors>. Issues and pull requests
can both be filed there.
