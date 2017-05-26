PDFLATEX = pdflatex
BIBTEX = bibtex
OTT = ott
OTT_FLAGS := -tex_wrap false -tex_show_meta true -picky_multiple_parses false
SKIM := skim_revert.sh
SKIMRevinPath := $(shell command -v $(SKIM) 2> /dev/null)
PDF := main.pdf

all: pdf
  # This is for my private machine.  It forces my PDF reader to reload.
  # It should not run unless "skim_revert.sh" is in your PATH
  ifdef SKIMRevinPath
	@$(SKIM) $(PDF) &>/dev/null
	@$(SKIM) $(PDF) &>/dev/null
	@$(SKIM) $(PDF) &>/dev/null
  endif

pdf : main.pdf

quick : main.tex ref.bib Makefile
	$(PDFLATEX) -jobname=main main.tex
        # This is for my private machine.  It forces my PDF reader to reload.
        # It should not run unless "skim_revert.sh" is in your PATH.
	ifdef SKIMRevinPath
		@$(SKIM) $(PDF) &>/dev/null
		@$(SKIM) $(PDF) &>/dev/null
		@$(SKIM) $(PDF) &>/dev/null
	endif

lambek-itself-ott.tex : lambek-itself.tex
	@$(OTT) $(OTT_FLAGS) -i Elle/Elle.ott -o Elle-inc.tex -tex_name_prefix Elle \
		-tex_filter lambek-itself.tex lambek-itself-ott.tex

lambek-exchange-ott.tex : lambek-exchange.tex
	@$(OTT) $(OTT_FLAGS) -i Elle/Elle.ott -o Elle-inc.tex -tex_name_prefix Elle \
		-tex_filter lambek-exchange.tex lambek-exchange-ott.tex

# Now this takes the full LaTex translation and compiles it using
# pdflatex.
main.pdf : main.tex ref.bib Makefile appendix.tex Lambek-categories.tex categorical-models.tex adjoint-models.tex categorical-models.tex resource-adjoint-logics.tex applications.tex lambek-exchange-ott.tex lambek-itself-ott.tex
	$(PDFLATEX) -jobname=main main.tex
	$(BIBTEX) main
	$(PDFLATEX) -jobname=main main.tex
	$(PDFLATEX) -jobname=main main.tex

clean :
	rm -f *.aux *.dvi *.ps *.log *-ott.tex *-output.tex *.bbl *.blg *.rel *~ *.vtc *.out *.spl *-inc.tex
