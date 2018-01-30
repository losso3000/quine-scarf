# quine-scarf

A kind-of quine in perl, i.e. a program that outputs its own source code—in this case, as an image (as opposed to source code like [traditional quines](https://en.wikipedia.org/wiki/Quine_(computing)) do). Created for the quine scarf competition held by [@fbz on Twitter](https://twitter.com/fbz/status/936117740560990209).

I call it "kind-of-quine" because reading the source code's own file (via `$0` in Perl) might be considered cheating by some. However, since I aimed to include my own hand-pixelled font and wanted to avoid external libraries for the graphics output, there simply was no space for the traditional self-quoting approach used by text-only quines, since that would have at least doubled the size of the source code.

## Usage

```
$ perl quine.pl > quine.pbm
```

Voilà! You should be able to open the resulting file in GIMP or Photoshop, or convert it with ImageMagick (`convert quine.pbm quine.png`). The result should look like this:

![The rendered quine](/quine.png)

## Technical stuff

As mentioned, the program starts by reading its own source. Then it creates a string with an empty PBM image like this:

```
P1
100 1200
0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 ...
```
(`P1` is the file format, in this case a bitmap. `100` and `1200` denote width and height, respectively, and each `0` is a pixel.)

Then, each character of the source code is plotted into this string, turning a `0` into a `1` wherever a pixel is to be set (5×8 pixels per glyph), and printed to STDOUT.

## Not-so technical

Much to my delight, my entry was co-selected as a winner, and the result [looks awesome](https://twitter.com/fbz/status/958410528543588352)! Thanks again, @fbz, and congratz to your entry, too, @kenshirriff!
