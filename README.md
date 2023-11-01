[![ci](https://github.com/tdegeus/goose-article/workflows/CI/badge.svg)](https://github.com/tdegeus/goose-article/actions)
[![pre-commit](https://github.com/tdegeus/goose-article/workflows/pre-commit/badge.svg)](https://github.com/tdegeus/goose-article/actions)

# goose-article

A customised article class for LaTeX.

# Contents

<!-- MarkdownTOC -->

- [Disclaimer](#disclaimer)
- [Usage](#usage)
- [Options](#options)
- [Citations](#citations)
- [Examples](#examples)
- [Tips](#tips)

<!-- /MarkdownTOC -->

# Disclaimer

This library is free to use.
Any additions are very much appreciated, in terms of suggested functionality,
code, documentation, testimonials, word-of-mouth advertisement, etc.
Bug reports or feature requests can be filed on [GitHub](https://github.com/tdegeus/goose-article).
As always, the code comes with no guarantee.
None of the developers can be held responsible for possible mistakes.

Download:
[.zip file](https://github.com/tdegeus/goose-article/zipball/master) |
[.tar.gz file](https://github.com/tdegeus/goose-article/tarball/master).

(c - [MIT](https://github.com/tdegeus/goose-article/blob/master/LICENSE)) T.W.J. de Geus (Tom) |
tom@geus.me | www.geus.me |
[github.com/tdegeus/goose-article](https://github.com/tdegeus/goose-article)

# Usage

*goose-article* is a customised class designed for scientific articles.
The usage is similar to the default *article* class while the class takes care of formatting.
To get started, copy the files from [src/](src/) to to main directory of your project
(always copy [goose-article.cls](src/goose-article.cls) and copy according to your need
[unsrtnat.bst](src/unsrtnat.bst), [unsrtnat_hyperlink.bst](src/unsrtnat_hyperlink.bst),
or [apalike.bst](src/apalike.bst)).

By default, most of the standard LaTeX packages are loaded.
Any of these packages can be reloaded without problems (possibly using other options).
In addition, the title, the authors and their affiliations, contact information,
and optionally a header can be specified.

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

% The author to put in the PDF information.
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

% If you have references in "myrefs.bib"
\bibliographystyle{unsrtnat}
\bibliography{myrefs}

\end{document}
```

# Options

*   Any option for the `article` class, such as `12pt`, `fleqn`, etc.

*   `garamond`, `times`, `verdana`

    Choose a font.
    The default computer-modern font is used if no font is specified.
    If you select one of these fonts, switch in compilation from using `pdflatex` to `xelatex`.
    XeLaTeX is similar to `pdflatex` but it allows for the usage of TrueType-fonts.

*   `narrow`, `wide`, `wwide`

    Change the page margins (from largest to smallest margins: `narrow`, (normal), `wide`, `wwide`).

*   `doublespacing`

    Set the line spacing to double, useful during the review process.

*   `empty`

    Do not use any header (does not even show the page number).

*   `plainparagraph`

    Do not append a period to `\paragraph`.

*   `displayparagraph`

    Show paragraph titles in the text (instead of inline).

*   `twocolumnbib`

    Use a two-column bibliography.

*   `normalsizebib`

    Bibliography in normal font size (instead of `\scriptsize`).

*   `namecite`

    Use name-citations instead of numbers.
    Often combined with `\bibliographystyle{apalike}` (see below).

*   `showlinks`

    Highlight links in the displayed (i.e. not the printed one) PDF.

*   `colorlinks`

    Show links using a blue color.

# Citations

Citations and references are handled using [natbib](http://ctan.org/pkg/natbib).
You can select your `\bibliographystyle{...}` of preference before calling `\bibliography{...}`.
An extended [unsrtnat.bst](src/unsrtnat.bst) is available that includes output
for the `arxivid` field.
Similarly a customised *apalike* style is available ([apalike.bst](src/apalike.bst)).

A little bit more customised is the *unsrtnat_hyperlink* bibliography style,
in which the *doi* (or, if missing, the *arxivid* or *url*) are used
to create a hyperlink behind the title.
The *doi* or *arxivid* are not explicitly shown in citation.

Following standard *natbib*, one can use `\cite{...}` or `\citep{...}`
for normal citations and `\citet{...}` to include the name.
[See also this cheat-sheet](http://merkel.texture.rocks/Latex/natbib.php).

Note that the outputted reference list depends largely on the content of the included `bib`-file.
A simple command-line tool, [GooseBib](https://github.com/tdegeus/GooseBib),
is available to clean up arbitrary `bib`-files.

# Examples

*   [Basic example](examples/basic/example.tex),
    see [PDF](examples/basic/example.pdf).

*   [Basic example with `namecite`](examples/namecite/example.tex),
    see [PDF](examples/basic/example.pdf).

*   [Two-column example](examples/twocolumn/example.tex),
    see [PDF](examples/twocolumn/example.pdf).

# Tips

*   [Dummy subfigure label](examples/general-trick_dummy-subfigure/example.tex),
    see [PDF](examples/general-trick_dummy-subfigure/example.pdf).

*   [Dummy subfigure label, upper-case](examples/general-trick_dummy-subfigure-upper/example.tex),
    see [PDF](examples/general-trick_dummy-subfigure-upper/example.pdf).
