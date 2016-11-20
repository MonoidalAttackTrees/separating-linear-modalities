PDFLATEX = pdflatex
BIBTEX = bibtex
OTT = ott
OTT_FLAGS := -tex_show_meta false -tex_wrap true
SKIM := skim_revert.sh
SKIMRevinPath := $(shell command -v $(SKIM) 2> /dev/null)

all: pdf
  # This is for my private machine.  It forces my PDF reader to reload.
  # It should not run unless "skim_revert.sh" is in your PATH.
  ifdef SKIMRevinPath	
	@$(SKIM) Assoc.pdf &>/dev/null
	@$(SKIM) Assoc.pdf &>/dev/null
	@$(SKIM) Assoc.pdf &>/dev/null
  endif

pdf : Assoc.pdf

Assoc.tex : Assoc.ott
	$(OTT) $(OTT_FLAGS) -i Assoc.ott -o Assoc.tex

Assoc.pdf : Makefile Assoc.tex
	$(PDFLATEX) Assoc.tex

clean :
	rm -f *.aux *.dvi *.ps *.log *-ott.tex *-output.tex *.bbl *.blg *.rel *.pdf *~ *.vtc *.out *.spl *-inc.tex
