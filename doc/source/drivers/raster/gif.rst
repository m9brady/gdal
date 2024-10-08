.. _raster.gif:

================================================================================
GIF -- Graphics Interchange Format
================================================================================

.. shortname:: GIF

.. build_dependencies:: (internal GIF library provided)

GDAL supports reading and writing of normal, and interlaced GIF files.
Gif files always appear as having one colormapped eight bit band. GIF
files have no support for georeferencing.

A GIF image with transparency will have that entry marked as having an
alpha value of 0.0 (transparent). Also, the transparent value will be
returned as the NoData value for the band.

If an ESRI :ref:`world file <raster.wld>` exists with the .gfw, .gifw
or .wld extension, it will be read and used to establish the geotransform
for the image.

XMP metadata can be extracted from the file,
and will be stored as XML raw content in the xml:XMP metadata domain.

Driver capabilities
-------------------

.. supports_createcopy::

.. supports_virtualio::

Creation Issues
---------------

GIF files can only be created as 1 8bit band using the "CreateCopy"
mechanism. If written from a file that is not colormapped, a default
greyscale colormap is generated. Transparent GIFs are not currently
supported on creation.

|about-creation-options|
The following creation options are supported:

- .. co:: WORLDFILE
     :choices: ON, OFF
     :default: OFF

     Force the generation of an associated ESRI world file (.wld).
     See :ref:`World Files <raster.wld>` section for details.

- .. co:: INTERLACING
     :choices: ON, OFF
     :default: OFF

     Generate an interlaced (progressive) GIF file.

GDAL's internal GIF support is implemented
based on source from the giflib 4.1.6 library (written by Gershon Elbor,
Eric Raymond and Toshio Kuratomi), hence generating LZW compressed GIF.

The driver was written with the financial support of the `DM Solutions
Group <http://www.dmsolutions.ca/>`__, and `CIET
International <http://www.ciet.org/>`__.

See Also
--------

-  `giflib Home Page <http://sourceforge.net/projects/giflib/>`__
