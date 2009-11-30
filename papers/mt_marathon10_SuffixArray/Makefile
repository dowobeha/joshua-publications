
PAPER=paper

all: ${PAPER}.pdf

#.SECONDARY: %.tex %.aux %.blg %.bbl
.SECONDARY: %.blg
.SUFFIXES:

%.pdf: %.tex %.aux %.blg %.bbl 
	xelatex $*
	xelatex $*
	touch $*.blg $*.bbl

%.blg %.bbl: %.tex %.aux
	bibtex $*

%.aux: %.tex
	xelatex $*

clean:
	rm -f *.aux *.bbl *.blg *.log *.pdf


open: ${PAPER}.pdf
	open $<



.PHONY: all open