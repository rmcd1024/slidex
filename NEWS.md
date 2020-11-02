# Version 0.0.0.9002


`slidex` does a fantastic job of converting pptx to `xaringan`-flavored
markdown. This is a fork of version 0.0.0.9001, which adds the parameter
`output_format` to the `convert_pptx` function. The value can be
either `xaringan` (default) or `latex` (Beamer). 

## What does this extension accomplish?

If `xaringan` is specified, the output should be identical to that in
version 0.0.0.9001. If `latex` is specified, differences are as
follows:

* the YAML header specifies beamer output and incorporates beamer
  options, including xelatex compilation (to handle unicode created in
  the translation from pptx) and slide-level
* slide heads are changed from `#` to `##` and `slide_level=2` is
  added to the YAML header
* references to `.wmf` graphics are changed to `.png`
* all wmf files are converted to png *if* libreoffice is installed and
  available at the command line (tested under Linux)
* the `xaringan` `reveal.js` extensions are removed. If there are two
  graphics on a page, they are placed side by side and shrunk. If
  there are more than two graphics on a page they are shrunk in
  proportion to the number of graphic images. The idea is to enable
  you to see what's there, and then tweak the markdown to get the size
  and placement you want 

## Why create this extension in the first place? 

The goal  was to create a pptx translation that is purely
markdown. This enables pdf output without the intermediate step of
printing pdf from a browser. 
    
