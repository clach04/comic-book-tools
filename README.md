# comic-book-tools

## TODO

  * Pure Python script to iterate through comicbook archive (CBZ, CBR, CBT, CB7)
  * one image at a time and convert to a new archive.
  * Use threading where possible with Pillow/PIL for concurrent image/file conversion in memory without using temporary disk space.
  * Add option for image conversion, e.g.
      * to WebP - https://www.reddit.com/r/comicrackusers/comments/ug8n4i/cb7_vs_cbz/
      * https://github.com/wanadev/mozjpeg-lossless-optimization also see https://siipo.la/blog/is-webp-really-better-than-jpeg and https://siipo.la/blog/whats-the-best-lossless-image-format-comparing-png-webp-avif-and-jpeg-xl

## Existing tools

  * https://pkg.go.dev/git.gryffyn.io/gryffyn/cbr2cbz#section-readme
      * git.gryffyn.io/gryffyn/cbr2cbz
  * https://github.com/Dapbler/cbr2cbz - Python but needs unrar-nonfree (does not work with unrar-free) and ImageMagick. Also requires temporary disk space, uses use mktemp so TEMP os env (TMP, etc.) can be used to avoid writting to SD cards etc and use alternative disk space
      * https://github.com/mikeymakesit/cbr2cbz/tree/valueerror-oldtimestamps - with bug-fix/enhancement for pre-1980 dates
  * https://github.com/clach04/kcc
      * https://github.com/ciromattia/kcc/pull/393
      * https://github.com/ciromattia/kcc/pull/416
      * https://github.com/ciromattia/kcc/pull/393
  * https://github.com/clach04/image_ls
  * https://github.com/comictagger/comictagger
  * https://github.com/gen2brain/cbconvert Go based, requires mageMagick7 and libheif
  * https://github.com/davide-romanini/ComicStreamer
  * https://github.com/mcpierce/comixed - Java
    * https://github.com/comixed/comixed
  * https://github.com/gen2brain/comic-utils
  * https://github.com/davide-romanini/comicapi - uses unrar python wrapper
  * https://github.com/proDOOMman/Mangle/blob/master/mangle/rarfile.py pure python support for uncompressed rar (CBR) files with a Python Zip file API

### Viewers

#### Android

KoReader

  * https://play.google.com/store/apps/details?id=org.kill.geek.bdviewer
      * https://challengerviewer.wordpress.com/
  * https://play.google.com/store/apps/details?id=com.bobaman.aircomix&hl=en_US&gl=US

#### Windows and Linux

KoReader

  * https://quivi.sourceforge.net/features.en.html
  * https://github.com/YACReader/yacreader
  * WebP and CBR/CBZ - SumatraPdf - open source reader with WebP support (official since version 2.4): http://blog.kowalczyk.info/software/sumatrapdf/free-pdf-reader.html

#### Kobo

https://github.com/baskerville/plato

#### Web browser

  * https://github.com/luejerry/html-mangareader

## Conversion tips

From https://www.mobileread.com/forums/showpost.php?p=3728291&postcount=17

As usual, for best results, properly dithered PNGs are your friend .

If you have access to ImageMagick v7, my current rescale + letterbox + grayscale + dither pass of choice looks something like this:

    convert input.png -colorspace Lab -filter LanczosSharp -distort Resize 1080x1429 -colorspace sRGB -background black -gravity center -extent 1080x1429! -grayscale Rec709Luminance -colorspace sRGB -dither Riemersma -remap eink_cmap.gif -quality 75 png:out.png

1080x1429 being the effective resolution of an H2O .

With the cmap attached here.

EDIT:

An approximately 10 times faster alternative, if you *really* need on-device processing:

    convert input.png -filter LanczosSharp -resize 1080x1429 -background black -gravity center -extent '1080x1429!' -colorspace Gray -dither Riemersma -remap eink_cmap.gif -quality 75 png:out.png

Last edited by NiLuJe; 02-12-2019 at 08:57 PM. Reason: Create true Grayscale PNGs, instead of Indexed RGB (speedier rendering in FBInk ;)). 


Koreader handles CBZ better than mobi/epub for comics https://www.mobileread.com/forums/showthread.php?t=343221
