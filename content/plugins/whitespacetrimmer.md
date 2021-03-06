Bundle: 2
Edition: creative
Tagline: Automatically trims whitespace off an image using smart edge detection

# WhitespaceTrimmer plugin

Trims whitespace (even smooth gradients) from around images automatically using edge detection filters. Requires Full Trust, uses unmanaged code.

## Usage

Add `&trim.threshold=80` to an image URL. You'll probably also want to restore a bit of padding with `&trim.percentpadding=0.5`, since it's ugly to trim completely to the edge of the object. 

The threshold value can usually go all the way up to 255 without cutting off any part of the image. The percentpadding value can be anywhere between 0 and 50, but 0.5-2 is usually the best.

## Installation

Either run `Install-Package ImageResizer.Plugins.WhitespaceTrimmer` in the NuGet package manager, or:

* Add ImageResizer.Plugins.WhitespaceTrimmer.dll to your project. Make sure AForge.dll, AForge.Math.dll, and AForge.Imaging.dll are copied also, although they do not need to be referenced directly.
* Add `<add name="WhitespaceTrimmer" />` inside `<plugins></plugins>` in Web.config.
