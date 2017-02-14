PDFLATEX = pdflatex
BIBTEX = bibtex
OTT = ott
OTT_FLAGS := -tex_show_meta false -tex_wrap false
SKIM := skim_revert.sh
SKIMRevinPath := $(shell command -v $(SKIM) 2> /dev/null)

all: pdf
  # This is for my private machine.  It forces my PDF reader to reload.
  # It should not run unless "skim_revert.sh" is in your PATH.
  ifdef SKIMRevinPath	
	@$(SKIM) main.pdf &>/dev/null
	@$(SKIM) main.pdf &>/dev/null
	@$(SKIM) main.pdf &>/dev/null
  endif

pdf : main.pdf

AL-output.tex : AL.ott AL.tex
	$(OTT) $(OTT_FLAGS) -i AL.ott -o AL-ott.tex -tex_filter AL.tex AL-output.tex -tex_name_prefix AL

AR-output.tex : AR.ott AR.tex
	$(OTT) $(OTT_FLAGS) -i AR.ott -o AR-ott.tex -tex_filter AR.tex AR-output.tex -tex_name_prefix AR

AN-output.tex : AN.ott AN.tex
	$(OTT) $(OTT_FLAGS) -i AN.ott -o AN-ott.tex -tex_filter AN.tex AN-output.tex -tex_name_prefix AN

NA-output.tex : NA.ott NA.tex
	$(OTT) $(OTT_FLAGS) -i NA.ott -o NA-ott.tex -tex_filter NA.tex NA-output.tex -tex_name_prefix NA

ANA-output.tex : ANA.ott ANA.tex
	$(OTT) $(OTT_FLAGS) -i ANA.ott -o ANA-ott.tex -tex_filter ANA.tex ANA-output.tex -tex_name_prefix ANA

main.pdf : Makefile main.tex ANA-output.tex NA-output.tex AN-output.tex AR-output.tex AL-output.tex
	$(PDFLATEX) main.tex

clean :
	rm -f *.aux *.dvi *.ps *.log *-ott.tex *-output.tex *.bbl *.blg *.rel *.pdf *~ *.vtc *.out *.spl *-inc.tex
