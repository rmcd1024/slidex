
<!-- README.md is generated from README.Rmd. Please edit that file -->

[![Travis build
status](https://travis-ci.org/datalorax/slidex.svg?branch=master)](https://travis-ci.org/datalorax/slidex)
[![AppVeyor build
status](https://ci.appveyor.com/api/projects/status/github/datalorax/slidex?branch=master&svg=true)](https://ci.appveyor.com/project/datalorax/slidex)
[![Coverage
status](https://codecov.io/gh/datalorax/slidex/branch/master/graph/badge.svg)](https://codecov.io/github/datalorax/slidex?branch=master)
[![CRAN
status](https://www.r-pkg.org/badges/version/slidex)](https://cran.r-project.org/package=slidex)

# Preliminary note: This is a fork, please read

This is a fork of `datalorax/slidex`, an impressive package that
converts pptx files to Rmd (`xaringan`-flavored). This fork, in
addition, converts to "latex", using the option
`output_format="latex"`. If you ignore the output_format option, it
should mimic the behavior of the original package. It also adds the
ability to convert `wmf` and `emf` files to `png` *if* you have
`libreoffice` installed (tested only on Linux). 

# slidex

This package is a work-in-progress, but is aimed at making the process
of converting Microsoft PowerPoint slides to beautiful HTML
[xaringan](https://github.com/yihui/xaringan) slides as seamless as
possible, maintaining tables, figures, links, and bulleted lists.

## Installation

The package is not yet on CRAN. Install the development version with

``` r
devtools::install_github("datalorax/slidex")
```

## Basic usage

At present, the package exports a single function, `convert_pptx`, which
takes two required arguments: the `path` to the PPTX file (passed as a
string), and the `author` (also passed as a string). For example:

``` r
library(slidex)
pptx <- system.file("examples", "slidedemo.pptx", package = "slidex")

convert_pptx(path = pptx, author = "Daniel Anderson")
```

You can optionally pass additional arguments, such as `theme` (see a
list of themes
[here](https://github.com/yihui/xaringan/tree/master/inst/rmarkdown/templates/xaringan/resources))
or a new
`title`.

![](https://github.com/datalorax/slidex/raw/master/docs/slidex-preview.gif)

## Suggested packages

Although not a dependency, the package functionally requires the
[xaringan](https://github.com/yihui/xaringan) package, and works best if
the [knitr](https://github.com/yihui/knitr),
[kableExtra](https://github.com/haozhu233/kableExtra), and
[tibble](https://github.com/tidyverse/tibble) packages are installed.
Without the latter three, tables will not be produced, although the code
to create a dataframe from the tables will still be embedded. Install
suggested packages from CRAN with

``` r
install.packages(c("xaringan", "knitr", "kableExtra", "tibble"))
```

## Things the package **should** be able to do

  - Maintain bulleting levels
  - Maintain bolding and italicizing (no support for underlining yet)
  - Maintain pictures
  - Maintain links (slightly imperfect currently)
  - Extract notes from the slides. By default the notes are embedded in
    the slides and a separate .txt file is written out.

## Things the package does not yet do, but hopefully will

  - Pull data and potentially reproduce plots (some support for this
    already, look in “assets/data” if you have a chart and want the data
    from it)
  - Convert `emf` file types to `png`s. This is a Microsoft proprietary
    format and will require users have LibreOffice installed.
  - Maintain two-panel layouts
  - Support both .ppt and .pptx file types. Currently only the latter is
    supported. Will require LibreOffice.

## Other ideas?

I’d love to hear from you if you’ve used the package and had success or
you’ve struggled. Either way, feedback, particularly at this early
stage, would be greatly appreciated.
