Font scale tool
================

A series of mixins and functions to set font-size, line-height and font-family values from a typographic scale. For more information check the [original post](http://erskinedesign.com/blog/setting-typographic-scale-with-sass-maps/) on the subject.

```scss
//scss
h1 {
	@include font-scale(helvetica, large);
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

### Setting the typographic scale

First the scale must be set in an alternative configuration file in a Sass map, with each specific font being made into its own map as well:

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




### Setting fonts with separate font files for each weight

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