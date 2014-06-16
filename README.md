Font scale tool
================

A series of mixins and functions to set font-size, line-height and font-family values from a typographic scale. For more information check the [original post](http://erskinedesign.com/blog/setting-typographic-scale-with-sass-maps/) on the subject.

```scss
//scss
h1 {
	@include font-scale(large, helvetica);
}

//css output
h1 {
	font-size: 35px;
	line-height: 40px;
}
```

### Installation

This module can be installed as a bower package like so:

```
bower install ult-font-scale
```

In your main `.scss` file you’ll need to add the default base font size and the set the `supports` map to convert all of the units to rems: 

```
$supports: (rem: true);
$font-base-size: 16;
```

Then import the `rem-calc` and the `font-scale` tool that’s a dependency:

```
@import "bower_components/ult-font-scale/font-scale";
@import "bower_components/ult-rem-calc/rem-calc";
```

Once that’s done we’ll need to set our typographic scale map. Usually I’d do this in another Sass partial like `font-scale.scss`:

```scss
$fonts: (
	helvetica: (
		base: (
            font-size: 16,
            line-height: 20
        ),

        large: (
        	font-size: 35,
        	line-height: 40
        )
    ),
	georgia: (
		small: (
			font-size: 13,
			line-height: 16
		),
		base: (
			font-size: 15,
			line-height: 19
		)
	)
);
```

Finally we can use the mixins like so:

```scss
h1 {
	@include font-scale(large, helvetica);
}
```

And that should export to something like this in CSS:

```css
h1 {
	font-size: 2.1875rem;
	line-height: 2.5rem;
}
```



### Optional configuration settings

#### Setting fonts with separate font files for each weight

Some typefaces require specific fonts for certain weights in which case we can set the `family-per-weight` value to true:

```scss
$font-sans-fallback-stack: Helvetica, sans-serif;

$fonts: (
    Apercu: (
        family-per-weight: true,
        normal: ('Apercu Regular', #{$font-sans-fallback-stack}),
        semi-bold: ('Apercu Medium', #{$font-sans-fallback-stack}),
        bold: ('Apercu Bold', #{$font-sans-fallback-stack}),
```

## Acknowledgements

- [Codepen demo](http://codepen.io/erskine/pen/xEqFC)
- [Setting typographic scale with Sass maps](http://erskinedesign.com/blog/setting-typographic-scale-with-sass-maps/)