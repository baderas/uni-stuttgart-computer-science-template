About
=====

Unoffical LaTeX template for Master, Bachelor, Diploma, and Student Theses at the University of Stuttgart, Computer Science.

More information at https://github.com/latextemplates/uni-stuttgart-computer-science-template.

It originates from the studiforge server at https://vorlagen.studiforge.informatik.uni-stuttgart.de/trac/

Quick start
-----------
If you don't want to use git, just download https://github.com/latextemplates/uni-stuttgart-computer-science-template/archive/template.zip

Recommended LaTeX environments
------------------------------
* offline: [TeXstudio] together with [JabRef].
* online: [overleaf]. Also with [git support](https://www.overleaf.com/blog/195-new-collaborate-online-and-offline-with-overleaf-and-git-beta#.VYFC2UZejkU).

See [LaTeX Editors/IDEs question on TeX.SX](http://tex.stackexchange.com/questions/339/latex-editors-ides) for a complete list of LaTeX editors.

### Recommended setup of MiKTeX
* Install MiKTeX for: "Only for: `username`"
* Install MiKTeX to: `C:\MiKTeX`. This enabled browsing for documentation at `C:\MiKTeX29\doc\latex
* Install missing packages on the fly: `Yes`

Characteristics of the template
-------------------------------
* UTF-8
* pdflatex
* Depends on [biblatex]

This template works on Windows using the current [MiKTeX](http://www.miktex.org) distribution. On Linux (TexLive full >= 2012) should work without any issues. 


Using with your own git repository
==================================

Initialization
--------------
This howto assumes that you have not a git repository for your thesis.
If you have, just add https://github.com/latextemplates/uni-stuttgart-computer-science-template.git as upstream and merge the branch "template" into your "master" branch.

1. Open command line
1. git clone https://github.com/latextemplates/uni-stuttgart-computer-science-template.git
1. cd uni-stuttgart-computer-science-template
1. git remote rename origin github
1. git checkout -b master

Now, you are on the master branch, where you can write your thesis and push it to your (remote) origin repository, in case you have one.

Merging updates from the template
---------------------------------
If you want to merge updates from github, do the following:

1. git fetch github
1. git merge github/template


LaTeX compilation
=================
The template is compiled using normal LaTeX commands.
Your LaTeX environment (such as [TeXStudio]) should take care about the compilation transparently.
If you want to include .svg graphics, [inkscape] has to be in your path.

If you want to compile using the command line, you can use following tools.

Automatic compilation using latexmk
-----------------------------------

    latexmk -pdf ausarbeitung

Continuous previewing using latexmk
-----------------------------------

    latexmk -pvc -pdf ausarbeitung

This will open Acrobat Reader once. Close it and start a PDF reader supporting instant reload of PDFs.
We recommend [Sumatra PDF].

Automatic compilation using make
--------------------------------
For those, who have [cygwin](http://www.cygwin.com/) installed or run a linux machine, this template offers a simple LaTeX makefile. It is not so sophisticated as other projects, but does its job

    make

Make targets:
 * `pdf` (default): Generates ausarbeitung.pdf
 * `aspell`: Checks all files using aspell.
 * `clean`: Removes all temporary files.
 * `mrproper`: Cleans up and removes also editor backup files.
 * `stand`: Creates a new PDF with the current status of the thesis.
 * `view`: Opens the configured viewer
 * `6`: Generates a 3x2 postscriptfile using psnup.

Alternatives:
* https://github.com/shiblon/latex-makefile
* https://github.com/ransford/pdflatex-makefile
* https://github.com/brotchie/latex-rubber-makefile
* See http://stackoverflow.com/questions/1240037/recommended-build-system-for-latex
* Current favourite: [LaTeX-Mk](http://latex-mk.sourceforge.net/).

Tweaks
======

Switching to English
--------------------

The template has been built primarily for German documents. English documents, however, are also very welcome.

Two steps to switch to English typesetting:

1. `ausarbeitung.tex`: Right on top: remove the `%` before `pointlessnumbers` (line 17)
1. `ausarbeitung.tex`: Exchange commands `\ifdeutsch` and `\ifenglisch`. (Lines 23,23 <-> 27,28).
1. `preambel/packages_and_options.tex` at `usepackage` of `uni-stuttgart-cs-cover`: disabled `language=german` and enable `language=english`. (Lines 448 and 449)
1. Cleanup everything (e.g., `latexmk -c ausarbeitung`). Otherwise pdflatex will complain because of `ngerman`.

Change Appearance of Chapter Headings
-------------------------------------

Edit `preambel/chapterheads.tex`.

Final version
-------------

  - If you included some version control statements, please remove them. Currently, the template does not support any, but it used to support SVN.
  - By using `\largeparge` and `\shortpage`, single lines at the bottom or at the top of the page can be manually fixed.
  - Search the PDF for "TODO" or similar things. Remove `\usepackage{todonotes}` in `preambel/packages_and_options`.
  - Ensure that you run `pdflatex` at least three times and that there no "undefined references".
  - The margins are intended for a duplex printing. **Do not change them** (or do exactly know what you are doing).

Further Reading
---------------

See http://wiki.flupp.de/LaTeX


# Contained Files and Directories

* ausarbeitung.tex
  * Main file
  * New chapters are added by using `\input`
  * Adjust title etc. here
* Makefile: The Makefile.
* README.md: This file.
* uni-stuttgart-cs-cover.sty: Verbatim copy of uni-stuttgart-cs-cover.sty available at https://github.com/latextemplates/uni-stuttgart-computer-science-cover
* `bibliography.bib`. Bibliography. [biblatex] format. Manage it with [JabRef].
* content/: Place for the actual content
  * content/einleitung.tex: First chapter: The introduction
  * content/kapitel2.tex: Second chapter
  * content/zusammenfassung`_`und`_`ausblick.tex: Conclusion and outlook.
  * content/anhang.tex
* graphics/: Directory containing the figures.
  By using PDFLaTeX it is possible to use PDFs, JPGs, PNGs, ... We recommend to use PDFs to enable smooth scaling.
* macros/: Directory for macros.
  * macros/commands.tex: Example macros
* preambel/: Latex header of the document ("preambel" in latex)
  * preambel/chapterheads.tex: Definition for the chapter headings.
  * preambel/fonts.tex: Font selection
  * preambel/margins.tex: Margin settings / Einstellung der Seitenränder
  * preambel/packages`_`and`_`options.tex: Includes required packages and their options.
  * preambel/pagestyle.tex: Defines the head and the foot of a page.

 [biblatex]: https://www.ctan.org/pkg/biblatex
 [inkscape]: http://inkscape.org/
 [JabRef]: http://jabref.sf.net
 [overleaf]: https://www.overleaf.com/
 [Sumatra PDF]: http://blog.kowalczyk.info/software/sumatrapdf/free-pdf-reader-de.html
 [TeXStudio]: http://texstudio.sourceforge.net/