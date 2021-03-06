tiffscan
========

tiffscan is an advanced SANE frontend. It has batch mode capabilities and
can generate compressed multi-page TIFF files. It handles from black and
white to 16 bit RBG+infrared scans.

tiffscan is Copyright (C) 2007-12 by Alessandro Zummo
and is released under the GPL, version 2.

Build
-----

tiffscan requires libpaper, libtiff and libpopt. Run make
to compile it.

If you want to build against a specific include and/or lib path, use

```
 INCDIR=/your/path/to/include LIBDIR=/your/path/to/libs make
```

Standard usage
--------------

To obtain help:
```
tiffscan --help
```

To list known devices:
```
tiffscan --list-devices
```

To list backend-specific options:
```
tiffscan --device .... --help
```

Simple scan:
```
tiffscan --device .... --scan
```

Batch scan:
```
tiffscan --device .... --scan --batch --paper a4
```

Batch scan to a single, compressed, multi-page TIFF file
```
tiffscan --device .... --scan --batch --compress --multi-page
```

Batch scan, prompt before each page
```
tiffscan --device .... --scan --batch --batch-prompt
```

Batch scan to an user-defined file series:
```
tiffscan --device .... --scan --batch --output-file my-scanned-page-%04d.tif
```

Advanced usage (coolscan2)
--------------------------
```
tiffscan --device ... --load
tiffscan --device ... --scan --autofocus --ae-wb
tiffscan --device ... --scan --autofocus --ae-wb --depth=12
tiffscan --device ... --eject
```

Infrared scanning 
-----------------

(requires experimental coolscan3 driver):

```
tiffscan --device ... --scan --autofocus --ae-wb --depth=12 --infrared=yes
```

Once the infrared image is obtained, you can use Ed Hamrick's Vuescan
to do cleaning and restoring (http://www.hamrick.com/) .

Automatic batch scanning from slide autoloader
(requires experimental coolscan3 driver) or SANE Evolution:

``` 
tiffscan --device ... --scan --batch --autofocus=yes --ae-wb=yes --autoload=yes
```

This should be enough to start using tiffscan. If you have any
question, please write me at a.zummo@towertech.it.

