# comic-book-tools

## TODO

  * Pure Python script to iterate through comicbook archive (CBZ, CBR, CBT, CB7)
  * one image at a time and convert to a new archive.
  * Use threading where possible with Pillow/PIL for concurrent image/file conversion in memory without using temporary disk space.
  * Add option for image conversion, e.g. to WebP- https://www.reddit.com/r/comicrackusers/comments/ug8n4i/cb7_vs_cbz/

## Existing tools

  * https://pkg.go.dev/git.gryffyn.io/gryffyn/cbr2cbz#section-readme
      * git.gryffyn.io/gryffyn/cbr2cbz
  * https://github.com/Dapbler/cbr2cbz - Python but needs unrar-nonfree (does not work with unrar-free) and ImageMagick. Also requires temporary disk space, uses use mktemp so TEMP os env (TMP, etc.) can be used to avoid writting to SD cards etc and use alternative disk space
      * https://github.com/mikeymakesit/cbr2cbz/tree/valueerror-oldtimestamps - with bug-fix/enhancement for pre-1980 dates
  * https://github.com/clach04/kcc
  * https://github.com/clach04/image_ls
  * https://github.com/comictagger/comictagger
  * https://github.com/gen2brain/cbconvert Go based, requires mageMagick7 and libheif
  * https://github.com/davide-romanini/ComicStreamer
  * https://github.com/mcpierce/comixed - Java
    * https://github.com/comixed/comixed
  * https://github.com/gen2brain/comic-utils
  * https://github.com/davide-romanini/comicapi - uses unrar python wrapper
