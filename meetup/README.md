# Rider Meetup Board - LaTeX Version

This is a LaTeX version of the Rider Meetup Board form, converted from HTML. It uses a parameterized template system to generate PDFs for different days from a single source file.

## Files

- `meetup.tex` - Main LaTeX file that accepts day as a parameter
- `meetup-template.tex` - The template content (shared by all days)
- `Makefile` - Build script for compiling the documents
- `saturday.html` - Original HTML version

## Requirements

You need a LaTeX distribution installed:
- **macOS**: Install MacTeX or BasicTeX
- **Linux**: Install TeX Live (`sudo apt-get install texlive-full` on Ubuntu/Debian)
- **Windows**: Install MiKTeX or TeX Live

## How to Compile

### Using Make (recommended)

```bash
# Compile all PDFs (saturday.pdf and sunday.pdf)
make

# Compile specific days
make saturday.pdf
make sunday.pdf
make monday.pdf
make friday.pdf

# View specific PDFs (macOS)
make view-saturday
make view-sunday
make view-all

# Clean auxiliary files
make clean

# Remove all generated files including PDFs
make cleanall
```

### Manual Compilation

```bash
# Compile for Saturday
pdflatex -jobname=saturday "\def\meetupday{Saturday}\input{meetup.tex}"
pdflatex -jobname=saturday "\def\meetupday{Saturday}\input{meetup.tex}"

# Compile for Sunday
pdflatex -jobname=sunday "\def\meetupday{Sunday}\input{meetup.tex}"
pdflatex -jobname=sunday "\def\meetupday{Sunday}\input{meetup.tex}"

# Compile for any day (replace DAYNAME)
pdflatex -jobname=DAYNAME "\def\meetupday{DAYNAME}\input{meetup.tex}"
```

## Adding More Days

To add a meetup board for another day, simply add a new rule to the Makefile:

```makefile
# Example: Add Wednesday
wednesday.pdf: meetup.tex meetup-template.tex
	$(LATEX) -jobname=wednesday "\def\meetupday{Wednesday}\input{meetup.tex}"
	$(LATEX) -jobname=wednesday "\def\meetupday{Wednesday}\input{meetup.tex}"
```

Then update the `PDFS` variable if you want it included in the `make all` command:
```makefile
PDFS = saturday.pdf sunday.pdf wednesday.pdf
```

## Customization

You can modify the following in `meetup-template.tex`:
- Adjust table row heights by changing the `[20pt]` values
- Modify column widths in the tabular environment
- Change colors by adjusting the `gray!10` value for the header row
- Modify the header text or layout

## Output

The compiled PDFs will have:
- Letter size page (8.5" x 11")
- 0.75" margins
- Centered header with title and subtitle
- Day-specific label (Saturday, Sunday, or any day you specify)
- Group information section
- 14-row table for rider information
- Footer note about limiting riders 