SHELL := /bin/bash
# use bash for <( ) syntax

.PHONY : 

.PRECIOUS : %.md

all : README.html

MATHJAX = https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js

# may want to add "--self-contained" to the following
PANDOC_OPTS = --standalone  --self-contained
MATHJAX_OPTS = --mathjax=$(MATHJAX)?config=TeX-AMS-MML_HTMLorMML 
# optionally add in a latex file with macros
LATEX_MACROS = macros.tex
ifeq ($(wildcard $(LATEX_MACROS)),)
	# macros file isn't there
else
	PANDOC_OPTS += -H .pandoc.$(LATEX_MACROS)
endif

.pandoc.$(LATEX_MACROS) : $(LATEX_MACROS)
	(echo '<div style="display: none">'; echo '\['; cat $(LATEX_MACROS); echo '\]'; echo '</div>') > $@

%.pandoc.html : %.tex
	pandoc -o %@ $(PANDOC_OPTS) $(MATHJAX_OPTS) $<

%.html : %.Rmd
	Rscript -e 'templater::render_template("$<", output="$@", change.rootdir=TRUE, clean=FALSE)'

%.html : %.md .pandoc.$(LATEX_MACROS)
	pandoc -o $@ $(PANDOC_OPTS) $(MATHJAX_OPTS) $<

%.local.html : %.md .pandoc.$(LATEX_MACROS)
	pandoc -o $@ $(PANDOC_OPTS) $(LOCAL_MATHJAX_OPTS) $<

%.md : %.Rmd
	Rscript -e 'knitr::knit_patterns[["set"]]($(KNITR_PATTERNS)); templater::render_template("$<", output="$@", change.rootdir=TRUE)'

%.pdf : %.md
	pandoc -o $@ -t latex $<

## VARIOUS SLIDE METHODS
REVEALJS_OPTS = -t revealjs -V theme=simple -V slideNumber=true -V transition=none -H resources/adjust-revealjs.style --slide-level 2
SLIDES_OPTS = $(REVEALJS_OPTS)

%.slides.html : %.md .pandoc.$(LATEX_MACROS)
	pandoc -o $@ $(SLIDES_OPTS) $(PANDOC_OPTS) $(MATHJAX_OPTS) $<


## 
# Graphics whatnot

# save inkscape svg files as .ink.svg and this'll do the right thing
%.svg : %.ink.svg
	inkscape $< --export-plain-svg=$@

%.pdf : %.ink.svg
	inkscape $< --export-pdf=$@

%.svg : %.pdf
	inkscape $< --export-plain-svg=$@

%.png : %.pdf
	convert -density 300 $< -flatten $@


##
# pdf from latex
#

%.pdf : %.tex %.bbl
	while ( pdflatex $<;  grep -q "Rerun to get" $*.log ) do true ; done

%.aux : %.tex
	-pdflatex $<

%.bbl : %.aux
	bibtex $<

##
# LaTeXML

LATEXML = $(shell which latexml)
LATEXMLC = $(shell which latexmlc)
LATEXMLPOST = $(shell which latexmlpost)

###
# stuff for compilers
LATEXMLFLAGS = 
LATEXMLPOSTFLAGS = --javascript=resources/LaTeXML-maybeMathjax.js --css=resources/plr-style.css --stylesheet=resources/xsl/LaTeXML-all-xhtml.xsl --javascript=resources/adjust-svg.js
# uncomment this to split out chapters into separate documents
# LATEXMLPOSTFLAGS += --split
LATEX_MACROS = macros.tex

%.html : %.md
	pandoc $(PANDOC_OPTS) $(PANDOC_HTML_OPTS) -f markdown -o $@ $<

%.xml : %.bib
	$(LATEXMLC) --destination=$@ --bibtex $<

%.xml : %.tex
	$(LATEXML) $(LATEXMLFLAGS) --destination=$@ $<

%.html : %.xml
	$(eval BIBS = $(shell grep '\\bibliography{' $*.tex \
		| sed -e 's/.*\\bibliography{\([^}]*\)\}.*/\1/' \
		| tr ',' '\n' ))
	@if [ '$(BIBS)' ]; then \
		echo 'making bibliography $(BIBS)'; \
		make $(BIBS); \
	fi
	$(LATEXMLPOST) --format=html5 $(foreach bib,$(BIBS),--bibliography=$(bib)) $(LATEXMLPOSTFLAGS) --destination=$@ $<

