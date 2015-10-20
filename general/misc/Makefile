BASENAME=${shell basename `grep -l '\\documentclass' *.tex` .tex}
VIEWER=xdg-open

.phony: all default clean compile view

all: clean compile view

default: compile

clean:
	for i in .acn .acr .alg .aux .bbl .blg .glg .glo .gls .ist .log .out .pdf .run.xml -blx.bib .snm .toc .nav;\
	do\
		echo rm ${BASENAME}$$i; \
		rm -f ${BASENAME}$$i; \
	done

compile:
	pdflatex ${BASENAME}
	makeglossaries ${BASENAME}
	pdflatex ${BASENAME}
	makeglossaries ${BASENAME}
	pdflatex ${BASENAME}
	bibtex ${BASENAME}
	pdflatex ${BASENAME}
	pdflatex ${BASENAME}

view:
	${VIEWER} ${BASENAME}.pdf
