## authorator

A Python program to create a LaTeX file with a large number of authors and  affiliations. This is useful for managing
manuscripts with a large number of authors (in LaTeX).

Authorator inputs a csv file with the authors and their affiliations, and outputs a LaTeX file that can be imported
into the document via \input, or simply cut-and-pasted into your main manuscript file.

Caveats: 
* Need to \usepackage{authblk} in your Latex file preamble.
* Need to create your title page with \maketitle
* Because authorator uses utf-8, you may need to compile your LaTeX file using XeTeX. Conversely, you can convert your latex file to ASCII using iconv or somesuch. Pure ASCII not implemented yet.
* Uses Python3

Todo:
 * Implement ASCII
 
### authors csv file

The input file to authorator is a tab-delimited csv file. It should have
four columns: First Name, Middle Name, Last Name, Affiliations.
The field delimiter does not have to be tab, and can be changed using the `--delim` option. It is not recommended to
change to common characters (such as a comma) since those are probably in the Affiliations anyway, and may break the
parser.

See `example_authors.csv` for example formatting.

* First Name, Middle Name, Last Name: author's names. One author per
  line
* Affiliations: the author's affiliations examples). If an author has more than one affiliation, those are 
  separated by a ";". The separator character can be modified using the `--affildelim` option.
  In the example file, Darwin and Spock have two affiliations. Kirk has one affiliaiton, the same as Spock.
* Title line: the first line of the authors csv file should be a title
  line, with the field names. The order of the fields is not important, as long as all four fields are there.



### How to run
Simplest way to run:

`./authorator -i authors.csv -o authors.tex`

This will create a tex file with the authors affiliations. See `example_authors.tex` for the result of the input of
`example_authors.csv`. Note that you need to [`\usepackage{authblk}`](https://www.ctan.org/pkg/authblk) in your LaTeX
document to make this work.

### How to put the authors list in your LaTeX document

Your LaTeX document should look something line this:
```
\documentclass{article}
.
.
\usepackage{authblk}
.
.
\input{authors} % your authors.tex file
.
.
\title{My long manuscript with many authors}

\begin{document}
\maketitle

Write lots of smart stuff here.

\end{document}

```
