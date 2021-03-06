qr-image
========

This is yet another QR Code generator.

Overview
--------

  * No dependecies;
  * generate image in `png`, `svg`, `eps` and `pdf` formats;
  * numeric and alphanumeric modes;
  * support UTF-8.

[Releases](https://github.com/alexeyten/qr-image/releases/)

Usage
-----

Example:
```javascript
var qr = require('qr-image');

var qr_svg = qr.image('I love QR!', { type: 'svg' });
qr_svg.pipe(require('fs').createWriteStream('i_love_qr.svg'));

var svg_string = qr.imageSync('I love QR!', { type: 'svg' });
```

[More examples](./examples)

`qr = require('qr-image')`

### Methods

  * `qr.image(text, [ec_level | options])` — Readable stream with image data;
  * `qr.imageSync(text, [ec_level | options])` — string with image data. (not implemented for `png`);
  * `qr.svgObject(text, [ec_level | options])` — object with SVG path and size;
  * `qr.matrix(text, [ec_level])` — 2D array.


### Options

  * `text` — text to encode;
  * `ec_level` — error correction level. One of `L`, `M`, `Q`, `H`. Default `M`.
  * `options` — image options object:
    * `ec_level` — default `M`.
    * `type` — image type. Possible values `png` (default), `svg`, `pdf` and `eps`.
    * `size` (png and svg only) — size of one module in pixels. Default `5` for png and `1` for others.
    * `margin` — white space around QR image in modules. Default `4` for `png` and `1` for others.
    * `customize` (only png) — function to customize qr bitmap before encoding to PNG.

Changes
-------

  * `svgpath` type is deprecated. Use `svgObject` method instead.
  * `margin` option is used for vector formats.


TODO
----

  * Tests;
  * `imageSync` for `png`.
  * mixing modes;
  * Kanji (???).
