[![ci](https://github.com/tdegeus/goose-article/workflows/CI/badge.svg)](https://github.com/tdegeus/goose-article/actions)
[![pre-commit](https://github.com/tdegeus/goose-article/workflows/pre-commit/badge.svg)](https://github.com/tdegeus/goose-article/actions)

# goose-article

A customised article class for LaTeX.

# Contents

*   [Usage](#usage)
*   [Options](#options)

    * [article class options](#articleclassoptions)
    * [font](#font)
    * [layout](#layout)
    * [bibliography](#bibliography)
    * [headers](#headers)

*   [Natbib: doi and arXiv](#natbib)
*   [Examples](#examples)
*   [Tips](#tips)

# Disclaimer

This library is free to use.
Any additions are very much appreciated, in terms of suggested functionality,
code, documentation, testimonials, word-of-mouth advertisement, etc.
Bug reports or feature requests can be filed on [GitHub](https://github.com/tdegeus/goose-article).
As always, the code comes with no guarantee.
None of the developers can be held responsible for possible mistakes.

# <a name='usage'></a>Usage

*goose-article* is a customised class designed for scientific articles.
The class is based on the default *article* class, but with some additional formatting and options.
Usage:

*   Copy [goose-article.cls](src/goose-article.cls) (from [src/](src/)) to to main directory of your project.
*   Optionally, copy [unsrtnat.bst](src/unsrtnat.bst) that includes `doi` links and a arXiv-id if present.

By default, most of the standard LaTeX packages are loaded.
Any of these packages can be reloaded without problems (possibly using other options).
In addition, the title, the authors and their affiliations, and optionally a header can be specified.

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

% Suggestion: set the proper author in the PDF information.
\hypersetup{pdfauthor={...}}

% Optional: add a page-header.
\header{...}

% =============================

\begin{document}

\maketitle

\begin{abstract}
...
\end{abstract}

...

% If you have references in "library.bib"
\bibliographystyle{unsrtnat}
\bibliography{library}

\end{document}
```

# <a name='options'></a>Options

## <a name='articleclassoptions'></a>article class options

*   Any option for the `article` class, such as `12pt`, `fleqn`, etc.

## <a name='font'></a>font

*   `font=[default], garamond, times, verdana`

    Choose a font.

    -   `default`: the default LaTeX font (computer-modern).
    -   `garamond`: the Garamond font, required `xelatex`.
    -   `times`: the Times New Roman font, required `xelatex`.
    -   `verdana`: the Verdana font, required `xelatex`.

## <a name='layout'></a>layout

*   `left=25mm, ...`

    Left margin. Passed to the `geometry` package.

*   `right=25mm, ...`

    Right margin. Passed to the `geometry` package.

*   `top=30mm, ...`

    Top margin. Passed to the `geometry` package.

*   `bottom=30mm, ...`

    Bottom margin. Passed to the `geometry` package.

*   `pagenumbers=[true], false`

    Show page numbers.

*   `doublespacing`

    Set the line spacing to double, useful during the review process.

*   `linenumbers`

    Add line numbers, useful during the review process.

## <a name='bibliography'></a>bibliography

*   `bibpackage=[natbib], biblatex, none`

    Choose the bibliography package.
    In both cases citations are with compressed numbers.

*   `bibsize=[scriptsize], ...`

    The font-size of the bibliography.

*   `bibcols=[1], ...`

    Number of (additional) columns in the bibliography.
    **Warning**: this option is only implemented for `natbib`.

## <a name='headers'></a>headers

*   `paragraphshape=[runin], ...`

    The shape of the paragraph header.

*   `paragraphafter=[.], ...`

    The character after the paragraph header.

# <a name='natbib'></a>Natbib: doi and arXiv

If you use [natbib](http://ctan.org/pkg/natbib) to handle your bibliography,
you can select your `\bibliographystyle{...}` of preference before calling `\bibliography{...}`.
An extended [unsrtnat.bst](src/unsrtnat.bst) is available that includes hyperlinks to the doi and arXiv-id.

# <a name='examples'></a>Examples

*   [Basic example](examples/basic/example.tex),
    see [PDF](examples/basic/example.pdf).

*   [Basic example with biblatex](examples/basic_biblatex/example.tex),
    see [PDF](examples/basic_biblatex/example.pdf).

*   [Two-column example](examples/twocolumn/example.tex),
    see [PDF](examples/twocolumn/example.pdf).

# <a name='tips'></a>Tips

*   [Dummy subfigure label](examples/general-trick_dummy-subfigure/example.tex),
    see [PDF](examples/general-trick_dummy-subfigure/example.pdf).

*   [Dummy subfigure label, upper-case](examples/general-trick_dummy-subfigure-upper/example.tex),
    see [PDF](examples/general-trick_dummy-subfigure-upper/example.pdf).
