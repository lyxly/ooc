# Copyright (C) 2009-2010, suxpert, All right reserved.

# Version Control System Information: Subversion, host on Google Code;
# FileID:	$Id$;
# FileDate:	$Date$;
# FileRevision:	$Revision$

# Makefile for GNUmake, \LaTeX{} -> pdf.


RM = rm
TEX = xelatex # -quiet -interaction=nonstopmode
OPEN = evince
TAR = tar -cjf
MV = mv
CP = cp

# OPEN = start
# RM = erase
# MV = rename
# CP = copy

VCS = svn
# Use Make to submit source files maybe NOT good enough.

TARGET = book.pdf
BALL = OOC.tar.bz2

SRC = header.tex\
      locale.tex\
      book.tex\
      preface.tex\
      body.tex\
      chapter01.tex\
      chapter02.tex\
      chapter03.tex\
      chapter04.tex\
      chapter05.tex\
      chapter06.tex\
      chapter07.tex\
      chapter08.tex\
      chapter09.tex\
      chapter10.tex\
      chapter11.tex\
      chapter12.tex\
      chapter13.tex\
      chapter14.tex\
      appendixA.tex\
      appendixB.tex\
      appendixC.tex

# Various of temp files:
LOGS = book.log
TOCS = book.toc
OUTS = book.out
AUXS = $(SRC:.tex=.aux)
BAKS = $(SRC:.tex=.tex~)
# Vim set backup; For Gedit or sth else, modify this to .bak or whatever.

$(TARGET): $(SRC)
	$(TEX) book
	$(TEX) book

# Re-run for hyperlinks.

.PHONY: clean distclean dist checkin exec clear

clean:
	-$(RM) $(TARGET)
	-$(RM) $(LOGS)

# $(OUTS) $(TOCS) $(AUXS)

clear:
	-$(RM) $(BAKS) # *~
	-$(RM) $(LOGS)
	-$(RM) $(OUTS) $(TOCS)
	-$(RM) $(AUXS)

distclean: clean clear
	-$(RM) $(BALL)

checkin: distclean
	$(VCS) --help # TODO:

dist: $(TARGET) clear
	$(MV) $(TARGET) OOC.pdf
	$(TAR) $(BALL) $(SRC) OOC.pdf Makefile
	$(CP) $(BALL) OOC-`date -u -d now +%Y-%m-%d-%H-%M`.tar.bz2
	$(MV) OOC.pdf $(TARGET)

exec: $(TARGET)
	$(OPEN) $(TARGET)

