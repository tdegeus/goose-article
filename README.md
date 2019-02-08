# goose-article

A customised article class for LaTeX.

>   This library is free to use. Any additions are very much appreciated, in terms of suggested functionality, code, documentation, testimonials, word-of-mouth advertisement, .... As always, the code comes with no guarantee. None of the developers can be held responsible for possible mistakes or misuse.
>   
>   Bug reports or feature requests can be filed on GitHub.
>   
>   (c - MIT) T.W.J. de Geus (Tom) | tom@geus.me | www.geus.me | [github.com/tdegeus/goose-article](http://github.com/tdegeus/goose-article)

## Outline

<!-- MarkdownTOC -->

- [Usage](#usage)
- [Options](#options)
- [Citations](#citations)
- [Examples](#examples)

<!-- /MarkdownTOC -->

## Usage

`goose-article` is a customised class designed for scientific articles. The usage is similar to the default `article` class while the class takes care of formatting. To get started copy the files from [src/](src/) to to main directory of your project (always copy [goose-article.cls](src/goose-article.cls) and copy to your need [unsrtnat.bst](src/unsrtnat.bst) or [apalike.bst](src/apalike.bst)).

By default most of the standard LaTeX packages are loaded. Any of these packages can be reloaded without problems (possibly using other options). In addition, the title, the authors and their affiliations, contact information, and optionally a header can be specified.

This results in the following structure:

```latex
\documentclass[...]{goose-article}

% The title (also used as PDF-title).
\title{...}

% The different authors. The optional number(s) correspond(s) to the affiliations.
% N.B. the authblk-package is used, see that package for more information.
\author[1,2]{...}
\author[2]{...}

% The different affiliations. Use "\nl" to enforce a line break.
\affil[1]{...}
\affil[2]{...}

% The contact information.
\contact{...} % E.g. "\href{mailto:tom@geus.me}{tom@geus.me}"

% The name to put in the PDF information.
\hypersetup{pdfauthor={...}}

% Text to put in the header. The page number is always used.
\header{...}

% =============================

\begin{document}

\maketitle

\begin{abstract}
...
\end{abstract}

...

\end{document}
```

## Options

*   `garamond`, `times`, `verdana`

    Choose a font. The default computer-modern font is used if no font is specified. If you select one of these fonts, switch in compilation from using `pdflatex` to `xelatex`. XeLaTeX is similar to `pdflatex` but it allows for the usage of TrueType-fonts.

*   `narrow`

    Widen the margins of the page, useful during the review process.

*   `doublespacing`

    Set the line spacing to double, useful during the review process.

*   `empty`
    
    Do not use any header (does not even show the page number).

*   `twocolumnbib`

    Use a two-column bibliography.

*   `namecite`

    Use names instead of numbers to cite to references.

## Citations

Citations and references are handled using [natbib](http://ctan.org/pkg/natbib). In this class, the `unsrtnat` layout is used. Thereby, the extended `unsrtnat.bst` is available that includes output for the `arxivid` field. The `goose-article` class creates commands to convert the `doi` and `arxivid` fields to links (to `doi.org` and `arxiv.org` respectively). Similarly a customised `apalike` style is available.

Following standard natbib, one can use `\cite{...}` or `\citep{...}` for normal citations and `\citet{...}` to include the name. [See also this cheat-sheet](http://merkel.texture.rocks/Latex/natbib.php).

Note that the outputted reference list depends largely on the content of the included `bib`-file. A simple command-line tool, [GooseBib](https://github.com/tdegeus/GooseBib), is available to clean up arbitrary `bib`-files.

## Examples

* [Basic example](examples/basic/example.tex)
* [Two-column example](examples/twocolumn/example.tex)


