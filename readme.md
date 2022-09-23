# Hugo SVG Font (v2)

## Simple Partial Usage

The "source" path is relative to the resources folder.

```HTML
{{ partial "svg-font" "icons/bootstrap/envelope" }}
```

## Optional Arguments for Partial

To use the optional argument you must pass a dict as the partials context.

``` HTML
{{ partial "svg-font" (dict "src" "icons/bootstrap/envelope" "em" 2 "block" true "title" "Icon Title" "desc" "Icon Desc")}}
```

`src` points to the SVG file relative to the assets folder. The .svg suffix is optional.

`em` is for setting the width that the icon will be displayed at. The default is 1em which will display an svg at its native size.

`block` is set to true if you are not using svg inline with text. This enables `display:block`.

`title` adds a title tag which browsers pick up and display on hover. It also adds `aria-labelledby` to the SVG. (for assistive technology). The title is useful for desktop users, but does not add functionality for mobile users. (who aren't using assistive technology/screen readers)

`description` adds a description tag and adds `aria-describedby` to the SVG. (for assistive technology)

## Shortcode usage

{{< svg-font src="icons/bootstrap/envelope" em=2 block=true title="Icon Title" desc="Icon Desc" >}}

## Styling your icons

You need to wrap your partial or shortcode in a div or span and add CSS classes to change the size and color.

An example utilizing bootstrap 5's utility classes is as follows:

```HTML
<span class="fs-2 text-primary">{{ partial "svg-font" "icons/bootstrap/envelope" }}</span>
```

*fs-2 changes the font size for the svg and text-primary changes the line color to primary (blue by default).*

## Installation

### Import module

Ensure that you are importing v2 as v1 is depreciated and not maintained.

```YAML
# config.yaml
module:
  imports:
  - path: github.com/future-wd/hugo-svg-font/v2
```

### Import CSS

You need to import required css from `/assets/scss/svg-font.scss'

```SCSS
// /assets/scss/index.scss
@import "svg-font.scss";
```

Or instead run the following partial in the projects head to compile the scss (source map and non-compressed CSS provided for development use)

```HTML
{{- partial "svg-font/css" . }}
```

## Example Output

### Input

``` HTML
{{ partial "svg-font" (dict "src" "icons/bootstrap/envelope" "em" 2 "block" true "title" "Email Address" "desc" "Email address of business")}}
```

```HTML
<!-- /assets/icons/bootstrap/envelope.svg -->
<!-- sourced from https://icons.getbootstrap.com/icons/envelope/ -->
<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-envelope" viewBox="0 0 16 16">
  <path d="M0 4a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2V4zm2-1a1 1 0 0 0-1 1v.217l7 4.2 7-4.2V4a1 1 0 0 0-1-1H2zm13 2.383-4.758 2.855L15 11.114v-5.73zm-.034 6.878L9.271 8.82 8 9.583 6.728 8.82l-5.694 3.44A1 1 0 0 0 2 13h12a1 1 0 0 0 .966-.739zM1 11.114l4.758-2.876L1 5.383v5.73z"/>
</svg>
```

### Output

```HTML
<svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" role="img" height="16" width="16" viewBox="0 0 16 16" class="svg-font em-1 d-block" aria-labelledby="e072ecbe2bee2c0d727360049ba7e5cb-title" aria-describedby="e072ecbe2bee2c0d727360049ba7e5cb-desc">
<title id="e072ecbe2bee2c0d727360049ba7e5cb-title">Email Address</title>
<desc id="e072ecbe2bee2c0d727360049ba7e5cb-desc">Email address of business</desc>
<path d="M0 4a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2V4zm2-1a1 1 0 0 0-1 1v.217l7 4.2 7-4.2V4a1 1 0 0 0-1-1H2zm13 2.383-4.758 2.855L15 11.114v-5.73zm-.034 6.878L9.271 8.82 8 9.583 6.728 8.82l-5.694 3.44A1 1 0 0 0 2 13h12a1 1 0 0 0 .966-.739zM1 11.114l4.758-2.876L1 5.383v5.73z"></path>
</svg>
```

```CSS
.svg-font {
  font-size: inherit;
  color: inherit;
  fill: currentColor;
  vertical-align: middle; }
.svg-font.em-2 {
  height: 2em;
  width: 2em; }
```
