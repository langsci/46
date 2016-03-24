LX = xelatex
MI = makeindex
BX = bibtex

FILEN = schaefer-egbd
TEXFLAGS =
#TEXFLAGS = -interaction=nonstopmode
PREFLAGS = -no-pdf

quick:
	-$(LX) $(TEXFLAGS) $(PREFLAGS) $(FILEN)
	printf "\033c"
	@echo
	@echo " === LAST RUN === "
	@echo
	-$(LX) $(TEXFLAGS) $(FILEN) | grep 'Warning'

clean:
	\rm *.adx *.and *.aux *.bbl *.blg *.idx *.ilg *.ldx *.lnd *.log *.out *.pdf *.rdx *.run.xml *.sdx *.snd *.toc *.wdx *.xdv
	\rm chapters/*.aux

all:
	-$(LX) $(TEXFLAGS) $(PREFLAGS) $(FILEN)
	-$(BX) $(FILEN)
	-$(LX) $(TEXFLAGS) $(PREFLAGS) $(FILEN)
	gsed -i s/.*\\emph.*// schaefer-egbd.adx #remove titles which biblatex puts into the name index
	makeindex -o schaefer-egbd.and schaefer-egbd.adx
	makeindex -o schaefer-egbd.lnd schaefer-egbd.ldx
	makeindex -o schaefer-egbd.snd schaefer-egbd.sdx
	-$(LX) $(TEXFLAGS) $(PREFLAGS) $(FILEN)
	printf "\033c"
	@echo
	@echo " === LAST RUN === "
	@echo
	-$(LX) $(TEXFLAGS) $(FILEN) 

view:
	open $(FILEN).pdf &

edit:
	mvim -c ':set spell spelllang=de' chapters/*.tex schaefer-egbd.tex
