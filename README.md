# Berry - CSS Utilities for any CSS-framework

CSS Library for Utility classes. For any CSS-framework.

Use the most suitable option for your favorite css-framework.

- `berry.css` - no normalize, no colors classes
- `berry-color.css` - no normalize, included colors
- `berry-normalize.css` - included normalize, no colors classes
- `berry-normalize-colors.css` - included normalize, included colors

All files include "box-sizing"-reset: `box-sizing: border-box`.

## Use Sass to configure

Customization with variables:
- Typical use: `variables/_variables.scss`
- Minimal classes: `variables/_variables-minimum.scss`

In the file `berry.scss`, you can specify the necessary modules.

## Using Berry 

Connect the CSS-file as you like.

```html
<link href="/path_to_styles/berry.css" rel="stylesheet">
<link href="/path_to_styles/ANY.css" rel="stylesheet">
```

## Methods of naming css-classes 

The delimiter is the symbol "-" (minus). Before the numbers and units of measurement "-" is not specified. Right: ".w10", ".w250px". Wrong: ".w-10", ".w250-px".

### Prefixes

- "b-" — block
- "t-" — text
- "w-" — width
- "h-" — height
- "bg-" — background (color, size)
- "lh-" — line-height
- "va-" — vertical-align
- "bor-" — border
- "mar-" — margin
- "pos-" — position
- "pad-" — padding
- "hide-" — invisibility
- "link-" — links
- "flex-" — flex
- "layout-" or "container-" — layout/container
- "hover-" — for :hover

### Modifiers

- "px" — px
- "em" — em
- "vh" — vh
- "rem" — rem
- "-max" — max-size (sample: max-height)
- "-min" — min-size (sample: min-height)
- "-t" — top
- "-r" — right
- "-b" — bottom
- "-l" — left
- "-tb" — top and bottom
- "-rl" — right and left
- "-imp" — for !important


### Adaptive Design Modifiers

Configured in the `_variables.scss` file.

- "-small"
- "-phone"
- "-tablet"
- "-medium"
- "-desktop"
- "-large"
- and others

## Samples classes

- .w34 -> width: 34%
- .pad10-b -> padding-bottom: 10px
- .pad5-b-phone -> padding-bottom: 10px for phone
- .mar25-rl -> margin-right: 25px; margin-left: 25px
- .t-red -> color: $red
- .w50-tablet -> width: 50% for tablet
- .b-hide -> display: none
- .hover-bg-red -> .bg-red:hover { .bg-red; }

For other examples, see http://unicss.maxsite.com.ua/samples

## CSS classes Berry

### Block

- .b-clearfix
- .b-right 
- .b-left 
- .b-center 
- .b-hide 
- .b-hide-imp 
- .b-inline, .b-inline-block 
- .b-block 
- .b-flex 
- .b-grid 
- .b-clear 

```html
<div class="b-inline">text</div>
```

### Vertical-align

- .va-baseline 
- .va-top 
- .va-middle 
- .va-bottom 
- .va-text-top 
- .va-text-bottom 
- .va-sub 
- .va-super 

```html
<img class="va-bottom" ...>
```

### Border

- .bordered

- .bor-none 
- .bor-none-t 
- .bor-none-r 
- .bor-none-b 
- .bor-none-l 

- .bor-solid (dotted, dashed, double) 
- .bor-solid-t 
- .bor-solid-r 
- .bor-solid-b 
- .bor-solid-l 
- .bor-solid-tb 
- .bor-solid-rl 

- .bor-color1 (and other colors)
- .hover-bor-color1

- .bor1 (border-width: 1px) (and other width)

```html
<div class="bor2 bor-dotted bor-red">text</div>
<div class="bordered">text</div>
<div class="bordered bor-none-r">text</div>
```

### Flex

- .flex (display: flex; justify-content: space-between; align-items: stretch;)

- .flex-row 
- .flex-row-reverse 
- .flex-column 
- .flex-column-reverse 
- .flex-wrap 
- .flex-wrap-reverse 
- .flex-nowrap 

- .flex-jc-start (justify-content)
- .flex-jc-end 
- .flex-jc-between 
- .flex-jc-around 
- .flex-jc-center, .flex-hcenter 

- .flex-ai-start (align-items)
- .flex-ai-end 
- .flex-ai-baseline 
- .flex-ai-stretch
- .flex-ai-center, .flex-vcenter 

- .flex-ac-start (align-content)
- .flex-ac-end 
- .flex-ac-center 
- .flex-ac-between 
- .flex-ac-around 
- .flex-ac-stretch 

- .flex-as-auto (align-self)
- .flex-as-start 
- .flex-as-end 
- .flex-as-center 
- .flex-as-baseline 
- .flex-as-stretch 

- .flex-order1 (and other values)
- .flex-grow1 (and other values)
- .flex-shrink1 (and other values)
- .flex-tablet (and other @media)

- .flex-wrap-tablet 
- .flex-reverse-tablet 
- .flex-vcenter-tablet 
- .flex-hcenter-tablet 
- .flex-order1-tablet (and other values)

```html
<div class="flex flex-vcenter flex-wrap-tablet">
	<div class="flex-grow2">1</div>
	<div class="flex-grow4 flex-order3">2</div>
	<div class="flex-grow1">3</div>
</div>
```

### Height

- .h100 (height: 100%)
- .h-auto 
- .h10px (and other values)
- .h10px-min
- .h10px-max 
- .h100vh (height: 100vh) (and other values)
- .h100vh-min
- .h100vh-max

```html
<div class="h30px">text</div>
```

### Layout / Container 

- .layout-center
- .layout-center-wrap
- .layout-wrap
- .layout-center-tablet (and other @media)
- .layout-center-wrap-tablet

```html
<div class="layout-center-wrap">
	<div class="layout-wrap">
		text
	</div>
</div>
```

### Padding
- .pad0 (and other values) 
- .pad0-t 
- .pad0-r 
- .pad0-b 
- .pad0-l 
- .pad0-tb 
- .pad0-rl

- .pad0-tablet (and other @media, and other values)
- .pad0-t-tablet 
- .pad0-r-tablet 
- .pad0-b-tablet 
- .pad0-l-tablet 
- .pad0-tb-tablet 

```html
<div class="pad20-rl pad0-b pad10-t">text</div>
```

### Margin
- .mar0 (and other values) 
- .mar0-t 
- .mar0-r 
- .mar0-b 
- .mar0-l 
- .mar0-tb 
- .mar0-rl 

- .mar0-tablet (and other @media, and other values)
- .mar0-t-tablet 
- .mar0-r-tablet 
- .mar0-b-tablet 
- .mar0-l-tablet 
- .mar0-tb-tablet 

```html
<div class="mar20-rl mar10-b mar0-t">text</div>
```

### Position

- .pos-fixed 
- .pos-absolute 
- .pos-relative 

- .pos10-t (top: 10px;) (and other values)
- .pos10-r 
- .pos10-b 
- .pos10-l 

- .z-index99 (and other values)

```html
<div class="pos-absolute pos10-r pos20-b">text</div>
```

### Rounded (border-radius)

- .b-circle (border-radius: 50%)
- .rounded 
- .rounded10 (and other values) 

```html
<div class="bordered rounded10">text</div>
```

### Text

- .t-reset (font-weight: normal; font-style: normal; text-decoration: none;)

- .bold 
- .bold-normal 
- .bold-bolder
- .bold-light 
- .italic 
- .underline 
- .strike (text-decoration: line-through;)
- .small-caps 
- .capitalize 
- .upper 
- .lower 
- .cursor-pointer 

- .t-right
- .t-left 
- .t-center 
- .t-justify 
- .t-decoration-none
  .t-nowrap 
- .t-wrap 
- .t-pre-wrap 
- .t-break, .t-break-word 

- .t-georgia (font-family: Georgia, Times New Roman, serif;)
- .t-times (font-family: Times New Roman, serif;)
- .t-arial (font-family: Arial, Helvetica, Verdana, sans-serif;)
- .t-verdana (font-family: Verdana, Arial, Helvetica, sans-serif;)
- .t-mono (font-family: Consolas, PT Mono, Monaco, Menlo, Courier New, monospace;)

- .t-clip (white-space: nowrap; overflow: hidden; text-overflow: ellipsis;)

- .t100 (font-size: 1rem;) (and other values) 
- .t100em (font-size: 1em;)
- .t10px (font-size: 10px;)

- .t-right-tablet (and other @media)
- .t-left-tablet 
- .t-center-tablet 
- .t-justify-tablet 
- .t-nowrap-tablet 
- .t-wrap-tablet
- .t100-tablet  (and other values)

```html
<div class="t120 bold t-center capitalize">text</div>
```

## Line-height

- .lh100 (line-height: 1;) (and other values) 
- .lh100em (line-height: 1em;)

```html
<div class="lh120">text</div>
```

## Visibility

- .visibility-hidden (visibility: hidden;)
- .visibility-visible (visibility: visible;)

- .hide-tablet (and other @media)

```html
<div class="hide-phone">text</div>
```

# Width

- .w-max-layout (width: 100%; max-width: 1200px;)
- .w100-max (max-width: 100%;)
- .w-hide (display: none;)
- .w-auto (width: auto;)

- .w5px (and other values) 
- .w5px-min 
- .w5px-max 

- .w0 (width: 0%;) (and other values) 
- .w0-min 
- .w0-max 

- .w-hide-tablet  (and other @media)
- .w-auto-tablet 

- .w50-tablet (and other @media, and other values)
- .w50-min-tablet 
- .w50-max-tablet

```html
<div class="flex flex-wrap-tablet">
	<div class="w30 w48-tablet w100-phone">1</div>
	<div class="w35 w48-tablet w100-phone">2</div>
	<div class="w30 w100-tablet">3</div>
</div>
```

## Background-size

- .bg-size-auto (background-size: auto;)
- .bg-size-cover (background-size: cover;)
- .bg-size-contain (background-size: contain;)

```html
<div style="background: url(...);" class="bg-size-cover"></div>
```

## Links

- a.hover-no-color - :hover (color: inherit;)
- a.hover-no-underline - :hover (text-decoration: none;)
- .hover-no-color - a:hover (color: inherit;)
- .hover-no-underline - a:hover (text-decoration: none;)
- .link-no-color, .links-no-color (color: inherit;)
- .link-no-color-imp, .links-no-color-imp (color: inherit !important;)

```html
<div class="t-red links-no-color"><a href="#">link</a></div>
<a class="hover-no-underline" href="#">link</a>
```

## Color text and background. Opacity

- .t-transparent (color: transparent;)
- .bg-transparent (background-color: transparent;)

- .opacity10, .hover-opacity10 (opacity: 0.1;) (and other values)
- .bg-op10, .hover-bg-op10 (background-color: rgba(0, 0, 0, 0.1);)

- .t-color1 (and other values)
- .bg-color1
- .hover-t-color1
- .hover-bg-color1

- .links-hover-t-color1 (and other values)
- .links-hover-bg-color1

```html
<div class="t-red600 bg-yellow300">text</div>
<div class="links-hover-t-red"><a href="#">link</a></div>
<a class="t-blue hover-t-red600 hover-bg-yellow100" href="#">link</a>
```

## Copyright and license

(c) 2019, Berry - CSS Utilities, http://maxsite.org/berry

[MIT License](https://github.com/maxsite/berry/blob/master/LICENSE)
