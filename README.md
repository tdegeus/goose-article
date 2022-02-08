[![ci](https://github.com/tdegeus/GooseSLURM/workflows/ci/badge.svg)](https://github.com/tdegeus/GooseSLURM/actions)
[![pre-commit](https://github.com/tdegeus/GooseSLURM/workflows/pre-commit/badge.svg)](https://github.com/tdegeus/GooseSLURM/actions)

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

This library is free to use. Any additions are very much appreciated, in terms of suggested functionality, code, documentation, testimonials, word-of-mouth advertisement, etc. Bug reports or feature requests can be filed on [GitHub](https://github.com/tdegeus/goose-article). As always, the code comes with no guarantee. None of the developers can be held responsible for possible mistakes.

Download: [.zip file](https://github.com/tdegeus/goose-article/zipball/master) | [.tar.gz file](https://github.com/tdegeus/goose-article/tarball/master).

(c - [MIT](https://github.com/tdegeus/goose-article/blob/master/LICENSE)) T.W.J. de Geus (Tom) | tom@geus.me | www.geus.me | [github.com/tdegeus/goose-article](https://github.com/tdegeus/goose-article)

# Usage

*goose-article* is a customised class designed for scientific articles. The usage is similar to the default *article* class while the class takes care of formatting. To get started, copy the files from [src/](src/) to to main directory of your project (always copy [goose-article.cls](src/goose-article.cls) and copy according to your need [unsrtnat.bst](src/unsrtnat.bst), [unsrtnathyper.bst](src/unsrtnathyper.bst), or [apalike.bst](src/apalike.bst)).

By default, most of the standard LaTeX packages are loaded. Any of these packages can be reloaded without problems (possibly using other options). In addition, the title, the authors and their affiliations, contact information, and optionally a header can be specified.

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

\end{document}
```

# Options

*   `garamond`, `times`, `verdana`

    Choose a font. The default computer-modern font is used if no font is specified. If you select one of these fonts, switch in compilation from using `pdflatex` to `xelatex`. XeLaTeX is similar to `pdflatex` but it allows for the usage of TrueType-fonts.

*   `narrow`, `wide`, `wwide`

    Change the page margins (from largest to smallest margins: `narrow`, (normal), `wide`, `wwide`).

*   `doublespacing`

    Set the line spacing to double, useful during the review process.

*   `fleqn`

    Use left-aligned (in stead of centered) equations.

*   `empty`

    Do not use any header (does not even show the page number).

*   `twocolumnbib`

    Use a two-column bibliography.

*   `unsrtnat` (default)

    Use "unsrtnat" as bib style.
    A custom version is shipped with *goose-article*.
    It differs from "unsrtnat" in that "arxivid" is supported (see below).

*   `unsrtnathyper`

    Use "unsrtnathyper" as bib style.
    Similar to `unsrtnat`, with in addition a hyperlink created behind the title (see below).

*   `apalike`

    Use "apalike" as bib style.
    I.e. use names instead of numbers to cite to references.
    A custom version is shipped with *goose-article*.
    It differs from "unsrtnat" in that "arxivid" and "doi" is supported (see below).

*   `showlinks`

    Highlight links in the displayed (i.e. not the printed one) PDF.

*   `colorlinks`

    Show links using a blue color.

# Citations

Citations and references are handled using [natbib](http://ctan.org/pkg/natbib). In this class, the *unsrtnat* layout is used. Thereby, the extended [unsrtnat.bst](src/unsrtnat.bst) is available that includes output for the `arxivid` field. The *goose-article* class creates commands to convert the `doi` and `arxivid` fields to links (to `doi.org` and `arxiv.org` respectively). Similarly a customised *apalike* style is available ([apalike.bst](src/apalike.bst)).

A little bit more customised is the *unsrtnathyper* bibliography style, in which the *doi* (or, if missing, the *arxivid* or *url*) are used to create a hyperlink behind the title. The *doi* or *arxivid* are not explicitly shown in citation.

Following standard *natbib*, one can use `\cite{...}` or `\citep{...}` for normal citations and `\citet{...}` to include the name. [See also this cheat-sheet](http://merkel.texture.rocks/Latex/natbib.php).

Note that the outputted reference list depends largely on the content of the included `bib`-file. A simple command-line tool, [GooseBib](https://github.com/tdegeus/GooseBib), is available to clean up arbitrary `bib`-files.

# Examples

*   [Basic example](examples/basic/example.tex),
    see [PDF](examples/basic/example.pdf).

*   [Two-column example](examples/twocolumn/example.tex),
    see [PDF](examples/twocolumn/example.pdf).

# Tips

*   [Dummy subfigure label](examples/general-trick_dummy-subfigure/example.tex),
    see [PDF](examples/general-trick_dummy-subfigure/example.pdf).

*   [Dummy subfigure label, upper-case](examples/general-trick_dummy-subfigure-upper/example.tex),
    see [PDF](examples/general-trick_dummy-subfigure-upper/example.pdf).
