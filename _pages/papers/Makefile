.PHONY: tmp-dir all

B2HFLAGS = -dl \
	   -s ./bold-title.bst \
           --nodoc -nofooter -noheader --no-abstract -nokeys --no-keywords --nobibsource\
           --named-field sources 'source code' \
           --named-field video 'video' \
           --named-field slides slides \
           --named-field full 'full version' \
           --named-field short 'short version' \
           --named-field prelim 'preliminary version' \
           --named-field conf 'conference version' \
           --named-field official 'official version' \
           --named-field homepage 'home page' \
           --named-field manuscript 'manuscript' \
           --named-field TR 'tech report' \
           --named-field TRbw 'tech report (black and white)' \
           --named-field book 'book' \
           --named-field pdf 'pdf' \
           --reverse-sort --sort-by-date

# Added to fix broken texlive 2010 distro that prevents bibtex2html from using /var/folders for tmp files
# @TMPDIR=.	

all: tmp-dir mjr-recent.html mjr-conference.html mjr-theses.html mjr-journal.html # mjr-misc.html

mjr-recent.html: mjr.bib Makefile tmp-dir
	bib2bib -ob mjr-recent.bib -oc mjr-recent.keys -c '(mjr:"yes") & (recent:"yes")' mjr.bib
	@TMPDIR=. bibtex2html -o mjr-recent $(B2HFLAGS) -citefile mjr-recent.keys mjr-recent.bib
	sed -i.bak "s/\[/<br>\[/g" mjr-recent.html

mjr-journal.html: mjr.bib Makefile tmp-dir
	bib2bib -ob mjr-journal.bib -oc mjr-journal.keys -c '(mjr:"yes") & ($$type="ARTICLE") & !(note:"Invited")' mjr.bib
	@TMPDIR=. bibtex2html -o mjr-journal $(B2HFLAGS) -citefile mjr-journal.keys mjr-journal.bib
	sed -i.bak "s/\[/<br>\[/g" mjr-journal.html

mjr-conference.html: mjr.bib Makefile tmp-dir
	bib2bib -ob mjr-conference.bib -oc mjr-conference.keys -c '(mjr:"yes") & ($$type="INPROCEEDINGS") & !(note:"Invited")' mjr.bib
	@TMPDIR=. bibtex2html -o mjr-conference $(B2HFLAGS) -citefile mjr-conference.keys mjr-conference.bib
	sed -i.bak "s/\[/<br>\[/g" mjr-conference.html

mjr-theses.html: mjr.bib Makefile tmp-dir
	bib2bib -ob mjr-theses.bib -oc mjr-theses.keys -c '(mjr:"yes") & (($$type="MASTERSTHESIS") | ($$type="PHDTHESIS"))' mjr.bib
	@TMPDIR=. bibtex2html -o mjr-theses $(B2HFLAGS) -citefile mjr-theses.keys mjr-theses.bib
	sed -i.bak "s/\[/<br>\[/g" mjr-theses.html

mjr-misc.html: mjr.bib Makefile tmp-dir
	bib2bib -ob mjr-misc.bib -oc mjr-misc.keys -c '(mjr:"yes") & ((note:"Invited") | ($$type="INCOLLECTION") | ($$type="TECHREPORT"))' mjr.bib
	@TMPDIR=. bibtex2html -o mjr-misc $(B2HFLAGS) -citefile mjr-misc.keys mjr-misc.bib
	sed -i.bak "s/\[/<br>\[/g" mjr-misc.html

