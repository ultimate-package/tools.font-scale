Font scale tool
================

Mixins for accessing a typographic scale from a Sass map. For more information check the [original post](http://erskinedesign.com/blog/setting-typographic-scale-with-sass-maps/) on the subject.

Here’s an example of how you might use this tool in a real project:

```scss
//scss
h1 {
	@include font-scale(base, helvetica);

    @media screen and (min-device-width : 320px) {
        @include font-scale(large, helvetica);
    }
}

//css output
h1 {
	font-size: 16px;
	line-height: 20px;

    @media screen and (min-device-width : 320px) {
        font-size: 35px;
        line-height: 40px;
    }
}
```

## Installation

This module can be installed as a bower package like so:

```
bower install ult-font-scale
```

In your main `.scss` file you’ll need to add a base font size which will be used to calculate the output rem values. After that you’ll want to add a `supports` map to convert all of the units to rems: 

```
$font-base-size: 16;
$supports: (rem: true);
```

Then you have to import the `font-scale` and `rem-calc` tool which also happens to be a dependency if you want rem values:

```
@import "bower_components/ult-font-scale/font-scale";
@import "bower_components/ult-rem-calc/rem-calc";
```

Once that’s done we’ll need to set our typographic scale as a Sass map. Usually I’d do this in another partial like `font-scale.scss` and import it back into the main Sass file:

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

With all that data in place we can finally use the mixins like so:

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
