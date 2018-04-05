# Svgize

A command line tool to make transparent JPEG images with the help of SVG. Use it to dramatically reduce filesize of transparent PNG images.

## Installation

1. Install ImageMagick.

```
brew install imagemagick
```

Alternatively, install ImageMagick from [binary distributions](https://www.imagemagick.org/script/download.php#macosx).

2. Download and install `svgize` preferably to `/usr/local/bin`.

```
curl -L https://raw.githubusercontent.com/vmdanilov/svgize/master/svgize >/usr/local/bin/svgize && chmod +x /usr/local/bin/svgize
```

## Usage

Run `svgize` on transparent images in Terminal:

```
Usage: svgize [options] image-file
Options:
  -h, --help                   Show this help message and exit
  -q, --quality value[:value]  Set compression quality for layer and mask respectively (75:100)
  -l, --link                   Save layer and mask separately, otherwise inline using base64 encoding
  -o, --output name            Specify name for output file
```

Output SVG image is a composition of YUV 4:2:0 JPEG image and grayscale PNG/JPEG image used as a mask.

```
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="width" height="height" viewBox="0 0 width height">
    <defs>
        <mask id="m">
            <image width="100%" height="100%" xlink:href="data:image/png;base64,..."/>
        </mask>
    </defs>
    <image mask="url(#m)" width="100%" height="100%" xlink:href="data:image/jpeg;base64,..."/>
</svg>
```

## License
The MIT License.
