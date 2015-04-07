LX = xelatex
MI = makeindex
BX = bibtex

FILEN = schaefer-egbd
REMOTE = rsling@dgm07.hpsg.fu-berlin.de:/home/rsling/public_html/
TEXFLAGS =
#TEXFLAGS = -interaction=nonstopmode
PREFLAGS = -no-pdf

quick:
	-$(LX) $(TEXFLAGS) $(PREFLAGS) $(FILEN)
	-$(LX) $(TEXFLAGS) $(FILEN)

all:
	-$(LX) $(TEXFLAGS) $(PREFLAGS) $(FILEN)
	-$(BX) $(FILEN)
	-$(LX) $(TEXFLAGS) $(PREFLAGS) $(FILEN)
	sed -i s/.*\\emph.*// schaefer-egbd.adx #remove titles which biblatex puts into the name index
	makeindex -o schaefer-egbd.and schaefer-egbd.adx
	makeindex -o schaefer-egbd.lnd schaefer-egbd.ldx
	makeindex -o schaefer-egbd.snd schaefer-egbd.sdx
	-$(LX) $(TEXFLAGS) $(PREFLAGS) $(FILEN)
	-$(LX) $(TEXFLAGS) $(FILEN)

view:
	evince $(FILEN).pdf &

scp:
	scp $(FILEN).pdf $(REMOTE)$(FILEN).pdf
