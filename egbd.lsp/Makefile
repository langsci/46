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
#	makeindex schaefer-egbd.idx
	texindy --german schaefer-egbd.idx
	-$(LX) $(TEXFLAGS) $(PREFLAGS) $(FILEN)
	printf "\033c"
	@echo
	@echo " === LAST RUN === "
	@echo
	-$(LX) $(TEXFLAGS) $(FILEN) | grep 'Warning'


view:
	open $(FILEN).pdf &

edit:
#	mvim -c ':set spell spelllang=de' -c ':nnoremap <F12> ]s' -c ':nnoremap <F11> [s' -c ':nnoremap <F10> zg' chapters/*.tex schaefer-egbd.tex local*.sty
	mvim -c ':set spell spelllang=de' -c ':nnoremap <F15> ]s' -c ':nnoremap <F14> [s' chapters/*.tex schaefer-egbd.tex local*.sty
