# Hugo Inline SVG [<img src="https://d33wubrfki0l68.cloudfront.net/c38c7334cc3f23585738e40334284fddcaf03d5e/2e17c/images/hugo-logo-wide.svg" align="right" width="250">](https://gohugo.io/)

[![GitHub License](https://img.shields.io/github/license/future-wd/hugo-inline-svg?style=flat-square)](https://github.com/future-wd/hugo-inline-svg/blob/master/LICENSE)
[![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/future-wd/hugo-inline-svg?style=flat-square)](https://github.com/future-wd/hugo-inline-svg/tags)
[![GoLang version"](https://img.shields.io/github/go-mod/go-version/future-wd/hugo-inline-svg?style=flat-square)](https://go.dev/)
[![Awesome](https://awesome.re/badge-flat.svg)](https://github.com/budparr/awesome-hugo)

## Simple Partial Usage

The "source" path is relative to the resources folder.

```HTML
{{ partial "inline-svg" "icons/bootstrap/envelope" }}
```

## Optional Arguments for Partial

To use the optional argument you must pass a dict as the partials context.

``` HTML
{{ partial "inline-svg" (dict "src" "icons/bootstrap/envelope" "fs" 2 "block" true "title" "Icon Title" "desc" "Icon Desc")}}
```

### Source 

`src` points to the SVG file relative to the assets folder. The .svg suffix is optional.

<!-- `em` is for setting the width that the icon will be displayed at. The default is 1em which will display an svg at its native size. -->

<!-- `block` is set to true if you are not using svg inline with text. This enables `display:block`. -->

### Display style

`display` can be set to  the following:

- `inline` to `display:inline-block` and match the height of text (scale of 0.7em).
- `block` to `display:block` and have a scale of 1em. (default)

### Size

By default the SVG's are set to `font-size: inherit;` which allows the svg to take on the `font-size` of its parent. Aternatively you can override this behaviour with **EITHER** following options:

- `fs` can be set to 1-7. These sizes mirror bootstrap's font sizes with the addition of 7 which is 0.875 (.small or \<small>)

- `rem` can be set to 1-5 which will set the `font-size` to 1-5rem. More granular control is available with `fs`.

### SVG Title

`title` adds a title tag which browsers pick up and display on hover. It also adds `aria-labelledby` to the SVG. (for assistive technology). The title is useful for desktop users, but does not add functionality for mobile users. (who aren't using assistive technology/screen readers)

### SVG Description

`description` adds a description tag and adds `aria-describedby` to the SVG. (for assistive technology)

## Shortcode usage

{{< svg-font src="icons/bootstrap/envelope" block=true title="Icon Title" desc="Icon Desc" >}}

## Styling your icons

You need to wrap your partial or shortcode in a div or span and add CSS classes to change the size and color.

An example utilizing bootstrap 5's utility classes is as follows:

```HTML
<span class="fs-2 text-primary">{{ partial "inline-svg" "icons/bootstrap/envelope" }}</span>
```

*fs-2 changes the font size for the svg and text-primary changes the line color to primary (blue by default).*

## Installation

### Import module


```YAML
# config.yaml
module:
  imports:
  - path: github.com/future-wd/hugo-inline-svg
```

### Import CSS

You need to import required css from `/assets/scss/inline-svg.scss'

```SCSS
// /assets/scss/index.scss  ! if your file is not located here, you must adjust your import path !
@import "inline-svg.scss";
```

Or instead run the following partial in the projects head to compile the scss (source map and non-compressed CSS provided for development use)

```HTML
{{- partial "svg-font/css" . }}
```
