ifeq ($(OS),Windows_NT)
    DEL_COMMAND := del
else
    DEL_COMMAND := rm
endif

all: main.pdf

# LaTeX must be run multiple times to get references right
main.pdf: main.tex $(wildcard *.tex) bibliography.bib
	pdflatex $<
	bibtex main
	makeindex main.nlo -s nomencl.ist -o main.nls
	pdflatex $<
	pdflatex $<



clean:
	$(DEL_COMMAND) -f pdfa.xmpi *.synctex* *.nlo *.nls *.ilg *.log *.dvi *.aux *.toc *.lof *.lot *.out *.bbl *.blg
	$(DEL_COMMAND) -f main.pdf
