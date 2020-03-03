ifeq ($(OS),Windows_NT)
    DEL_COMMAND := del
else
    DEL_COMMAND := rm
endif

all: main.pdf

# LaTeX must be run multiple times to get references right
ifeq (0,1)
main.pdf: main.bib main.tex $(wildcard *.tex)
	pdflatex $< -draftmode
	pdflatex $<

main.bib: main.aux
	bibtex main.aux

main.aux: main.bib
	pdflatex main.tex -draftmode
	pdflatex main.tex
endif

main.pdf: documentation.tex $(wildcard *.tex)
	pdflatex $<
	pdflatex $<

documentation.tex: 
	pdflatex documentation.tex
	bibtex documentation
	pdflatex documentation.tex
	pdflatex documentation.tex

clean:
	$(DEL_COMMAND) -f pdfa.xmpi *.synctex* *.nlo *.nls *.ilg *.log *.dvi *.aux *.toc *.lof *.lot *.out *.bbl *.blg
	$(DEL_COMMAND) -f main.pdf
