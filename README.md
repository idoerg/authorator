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
 
# How to run
Simplest way to run:
