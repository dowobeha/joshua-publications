
RERUN = "(There were undefined references|Rerun to get (cross-references|the bars) right)"
RERUNBIB = "No file.*\.bbl|Citation.*undefined"

all: paper.pdf
	open $<

paper.tex: figure.pgf.tex

%.pgf.tex: %.dot
	echo "{\\\\scalebox{0.7} {" > $@
	echo "{\\\\rotatebox{90} {" >> $@
	dot2tex $< --figonly -f pgf -e utf8 --prog=dot --graphstyle="font=\footnotesize" | grep -v "^$$" >> $@
	echo "}}" >> $@
	echo "}}" >> $@

%.pdf: %.tex
	pdflatex $<
	egrep $(RERUNBIB) $*.log && (bibtex $*; pdflatex $*) 
	(egrep $(RERUN) $*.log && pdflatex $*) && (egrep $(RERUN) $*.log && pdflatex $*)) || egrep -i "(Reference|Citation).*undefined" $*.log

