Tags: plugin
Bundle: 2
Edition: creative
Tagline: Blur, sharpen, remove noise, and perform automatic histogram adjustment. Plus several other cool effects. 

# AdvancedFilters plugin

Apply advanced effects to your images. Requires Full Trust.

The plugin currently applies effects to the image along with any background color, padding, or drop shadow that may be present. Future versions may simply apply the effect to the image, not the surrounding area. Note: does not affect borders or watermarks.

## Installation

Either run `Install-Package ImageResizer.Plugins.AdvancedFilters` in the NuGet package manager, or:

1. Add ImageResizer.Plugins.AdvancedFilters.dll to your project. Make sure AForge.dll, AForge.Math.dll, and AForge.Imaging.dll are copied also, although they do not need to be referenced directly.
2. Add `<add name="AdvancedFilters" />` inside `<plugins></plugins>` in Web.config.

## Usage

If you want more effects, [post your idea and vote for it](http://resizer.uservoice.com).

* Gaussian blur with adjustable radius: &blur=radius
* Gaussian sharpen with adjustable radius: &sharpen=radius

## Alpha effects (may change or disappear without notice)

**Please note the following effects are only preset for evaluation. If you like one and find a practical use for it, please let me know! Otherwise it might disappear to reduce the code surface area.**

**Also, note the order in which effects are applied *WILL CHANGE* in future releases** Don't combine them if you want repeatable results.

**The names for these will probably also change in future releases**

### Contrast, saturation, and brightness adjustment

Hint: Start with values between -0.1 and 0.1. Values have a big effect. 

* &a.contrast=-1..1
* &a.saturation=-1..1
* &a.brightness=-1..1

### Automatic white balance (alpha feature of 3.3.0)

Automatically corrects the white balance of the photo with 1 of 3 algorithms.

* `area` - Threshold is applied based on cumulative area at the lower and upper ends of the histogram. Much larger thresholds are required for this than SimpleThreshold.
* `simple` - Simple upper and lower usage thresholds are applied to the values in each channel's histogram to determine the input start/stop points for each individual channel. The start/stop points are used to calculate the scale factor and offset for the channel.
* `gimp` - Threshold is applied based on strangely skewed cumulative area, identical to the process used by GIMP.

The default (and reccommended) algorithm is 'area'.

*  &a.balancewhite=true|area|simple|gimp
*  &a.balancethreshold=0.6|0.06 (simple white balance requires a smaller threshold.)

For the `area` and `gimp` algorithms, the default threshold is 0.6. For `simple`, 0.06 is used (as it is not compared against cumulative area, but an individual value's usage)



### Automatic histogram adjustment (Good for daylight photos)

Adjusts contrast, saturation, and brightness with curves based on the histogram. Good for adjusting slightly foggy or dark daytime photos. 

* &a.equalize=true

### Sepia

Sepia effect, slightly different from the one in SimpleFilters... going to evaluate which is best.

* &a.sepia=true

### Oil Painting effect

Try `1` for impressionist, `100` for modern art ;)

* &a.oilpainting=1..100

### Noise removal

Not a blur effect - designed to remove color noise, 'pepper noise'. Very conservative, doesn't affect edges.

* &a.removenoise=1-100 


### Sobel energy filter

Useful only for debugging why [WhitespaceTrimmer](/plugins/whitespacetrimmer) isn't working on an image.

* &a.sobel=true

Note - you can also threshold the sobel filter into black and white with &a.threshold=0-255

### Canny Edge Detector

Displays edges as lines. Aggressive.

* &a.canny=true

