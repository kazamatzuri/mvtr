# Makefile for LaTeX document compilation

# LaTeX compiler
LATEX = pdflatex

# All PDF targets
PDFS = saturday.pdf sunday.pdf

# Default target - build all PDFs
all: $(PDFS)

# Generic rule for building any day's PDF
saturday.pdf: meetup.tex meetup-template.tex
	$(LATEX) -jobname=saturday "\def\meetupday{Saturday}\input{meetup.tex}"
	$(LATEX) -jobname=saturday "\def\meetupday{Saturday}\input{meetup.tex}"

sunday.pdf: meetup.tex meetup-template.tex
	$(LATEX) -jobname=sunday "\def\meetupday{Sunday}\input{meetup.tex}"
	$(LATEX) -jobname=sunday "\def\meetupday{Sunday}\input{meetup.tex}"


# Clean auxiliary files
clean:
	rm -f *.aux *.log *.out *.toc

# Clean all generated files
cleanall: clean
	rm -f *.pdf

# View the PDFs (macOS)
view-saturday: saturday.pdf
	open saturday.pdf

view-sunday: sunday.pdf
	open sunday.pdf

view-all: $(PDFS)
	open $(PDFS)

.PHONY: all clean cleanall view-saturday view-sunday view-all 