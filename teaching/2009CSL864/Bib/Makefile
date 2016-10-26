FNAME = paper

default:
	@latex $(FNAME);bibtex $(FNAME)
	@clear;(latex $(FNAME); echo "No more Warnings") | grep Warning

clean:
	@rm $(FNAME).{aux,bbl,blg,dvi,log,toc,lof,lot,ps,pdf,brf} *~

show:
	@yap $(FNAME).dvi &

all:
	@latex $(FNAME);bibtex $(FNAME);
	@make default

html:
	@make all
	@tth -L$(FNAME) < $(FNAME).tex > $(FNAME).html

pdf:
	@make all
	@dvips -t letter -K -Ppdf -G0 -o $(FNAME).ps $(FNAME).dvi
	@/usr/bin/ps2pdf14 -dPDFSETTINGS=/prepress -dEmbedAllFonts=true -dEncodeGrayImages=true -dAutoFilterGrayImages=false -dGrayImageFilter=/FlateEncode -dEncodeMonoImages=true -dAutoFilterMonoImages=false -dMonoImageFilter=/FlateEncode -dEncodeColorImages=true -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode $(FNAME).ps $(FNAME).pdf
	@make default
