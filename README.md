## authorator

A Python program to create a Latex file with a large number of authors and  affiliations. This is useful for managing manuscripts with a large number of authors.

Authorator inputs a csv file with the authors and their affiliations, and outputs a latex file that can be importad inot he main file via \input, or simply cut-and-pasted into your main manuscript file.

Caveats: 
* Need to \usepackage{authblk} in your Latex file preamble.
* Need to create your title page with \maketitle
* Because authorator uses utf-8, you may need to compile your latex file using XeTeX. Conversely, you can convert your latex file to ASCII using iconv or somesuch. Pure ASCII not implemented yet.
* Uses Python3

Todo:
 * Implement ASCII
 
### authors csv file

The input file to authorator is a tab-delimited csv file. It should have
four columns: First Name, Middle Name, Last Name, Affiliations.
* First Name, Middle Name, Last Name: author's names. One author per
  line
* Affiliations: the author's affiliations (see example_authors.csv for
  examples). If an author has more than one affiliations, those are 
  separated by a ";".
* Title line: the first line of the authrs csv file should be a title
  line, with the field names. The order of the fields is not important,
as long as all four fields are there.


### How to run
Simplest way to run:

`./authorator -i authors.csv -o authors.tex`

This will create a tex file

### How to put the authors list in your LaTeX document

Your Document should look something line this:
```
\begin{docuemnt}
.
.
\usepackage{authblk}
.
.
\input{authors}
.
.
\maketitle
```
